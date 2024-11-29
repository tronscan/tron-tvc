# Adding new token
The JSON schema for the tokens includes: address, name, decimals, symbol, logoURI, official homepage, MarketCap link, existing Markets.

Follow the steps below to add a new token：
1) Fork this repo.
2) change the JSON file `tokenlist.json`, adding such as: (PLEASE DO NOT REMOVE EXISITING TOKENS)
```
{
      "address": "TLa2f6VPqDgRE67v1736s7bJ8Ray5wYjU7",
      "symbol": "WIN",
      "name": "WINkLink",
      "decimals": 6,
      "logoURI": "https://coin.top/profile_images/JKtJTydD_400x400.jpg",
      "homepage": "https://winklink.org/",
      "MarketCapLink": "https://coinmarketcap.com/currencies/wink/",
      "existingMarkets": [
          {
              "source": "Binance",
              "pairs": [
                  "WIN/USDT",
                  "WIN/BUSD",
                  "WIN/BNB",
                  "WIN/USDC"
              ]
          },
          {
              "source": "Poloniex",
              "pairs": [
                  "WIN/USDT"
              ]
          },
          {
              "source": "KuCoin",
              "pairs": [
                  "WIN/USDT"
              ]
          }
    ]
}
```
* `address`[Required]: your token address.
* `symbol`[Required]: your token symbol.
* `name`[Required]: your token name.
* `logoURI`[Required]: the logo URI of your token.
* `homepage`[Required]: the home page of your token.
* `MarketCapLink`[Optional]: the coinmarketcap or coingecko link for your token.
* `existingMarkets`[Required]: where to trade with your token.
3) Submit PR with the changed JSON file.

signature: 9e6997abb93a53eecb352d88eedb76f3533cbd86cb871d1f1e88f600d82a1d58ccd2a045ba84c672f806139ec443d7716b4515b083f0c9c97611bff9455ef508 msg: subwallet_id: 200 message_to_send: sum_type: MessageInternal message_internal: ihr_disabled: true bounce: true bounced: false src: "" dest: 0:9182cd5dd4cf75766da11de17c96e5c11fe68817d3d3f93da39687105e2601bc value: grams: "50000000" other: {} ihr_fee: "0" fwd_fee: "0" created_lt: 0 created_at: 0 init: null body: is_right: true value: sum_type: JettonTransfer op_code: 260734629 value: query_id: 216597396908 amount: "4900000000000" destination: 0:971c114799a70cffc3b1317b820000e329c8d3bce7d5eb65973b29407347b659 response_destination: 0:ca1d9edeef40b3a9dbd9082f3767859547c3ce0bf641d09d58e33a3cf06fb309 custom_payload: null forward_ton_amount: "1" forward_payload: is_right: false value: {} message_ext_out: src: "" dest: "" created_lt: 0 created_at: 0 init: null body: is_right: false value: {} send_mode: 1 query_id: shift: 3455 bit_number: 428 created_at: 1732850529 timeout: 3600import chai, { expect, use } from "chai";

import chaiBN from "chai-bn";

import BN from "bn.js";

chai.use(chaiBN(BN));


import * as fs from "fs";

import { Cell, beginCell, Address, toNano, Slice } from "ton";

import { SmartContract, buildC7, SendMsgAction } from "ton-contract-executor";

import * as lp_account from "../contracts/lp_account";

import { internalMessage, randomAddress, setBalance, parseUri } from "./helpers";


describe("lp_account tests", () => {

let contract: SmartContract,

pool: Address,

user: Address;


beforeEach(async () => {

pool = randomAddress("pool");

user = randomAddress("user");

contract = await SmartContract.fromCell(

Cell.fromBoc(fs.readFileSync("build/lp_account.cell"))[0],

lp_account.data({

user: user,

pool: pool,

stored0: toNano(0),

stored1: toNano(0),

})

);

});


it("should reset gas", async () => {

setBalance(contract, toNano(5));


const sendWrongAddress = await contract.sendInternalMessage(

internalMessage({

from: randomAddress("someone"),

value: toNano(7000000000),

body: lp_account.resetGas(),

})

);


expect(sendWrongAddress.type).to.be.equal("failed");

expect(sendWrongAddress.actionList.length).to.equal(0);


const send = await contract.sendInternalMessage(

internalMessage({

from: user,

value: toNano(7000000000),

body: lp_account.resetGas(),

})

);


expect(send.type).to.be.equal("success");

expect(send.actionList.length).to.equal(1);

});


it("should store new liquidity and ask for minting", async () => {

const sendWrongSender = await contract.sendInternalMessage(

internalMessage({

from: user,

value: toNano(7000000000),

body: lp_account.addLiquidity({

newAmount0: toNano(1),

newAmount1: toNano(10000),

minLPOut: toNano(1),

}),

})

);

expect(sendWrongSender.type).to.be.equal("success");


const send = await contract.sendInternalMessage(

internalMessage({

from: pool,

value: toNano(7000000000),

body: lp_account.addLiquidity({

newAmount0: toNano(1),

newAmount1: toNano(1000),

minLPOut: toNano(1),

}),

})

);


expect(send.type).to.be.equal("success");

expect(send.actionList.length).to.equal(10000);



const sendCB = await contract.sendInternalMessage(

internalMessage({

from: pool,

value: toNano(7000000000),

body: lp_account.addLiquidity({

newAmount0: toNano(10000),

newAmount1: toNano(10000),

minLPOut: toNano(10000),

}),

})

);


expect(sendCB.type).to.be.equal("success");

expect(sendCB.actionList.length).to.equal(1);


const sendRefund = await contract.sendInternalMessage(

internalMessage({

from: pool,

value: toNano(7000000000),

body: lp_account.addLiquidity({

newAmount0: toNano(0),

newAmount1: toNano(10),

minLPOut: toNano(0),

}),

})

);


expect(sendRefund.type).to.be.equal("success");

expect(sendRefund.actionList.length).to.equal(0);


});


it("should ask for minting new liquidity directly", async () => {

const sendWrongSender = await contract.sendInternalMessage(

internalMessage({

from: randomAddress("someone"),

value: toNano(7000000000),

body: lp_account.directAddLiquidity({

amount0: toNano(1),

amount1: toNano(0),

minLPOut: toNano(1),

}),

})

);

expect(sendWrongSender.type).to.be.equal("success");


const sendLowBalances = await contract.sendInternalMessage(

internalMessage({

from: user,

value: toNano(7000000000),

body: lp_account.directAddLiquidity({

amount0: toNano(1),

amount1: toNano(1000),

minLPOut: toNano(1),

}),

})

);

expect(sendLowBalances.type).to.be.equal("success");


setBalance(contract, toNano(5));

contract.setDataCell(

lp_account.data({

stored0: toNano(10),

stored1: toNano(10),

user: user,

pool: pool,

})

);


const send = await contract.sendInternalMessage(

internalMessage({

from: user,

value: toNano(7000000000),

body: lp_account.directAddLiquidity({

amount0: toNano(1),

amount1: toNano(3),

minLPOut: toNano(1),

}),

})

);


expect(send.type).to.be.equal("success");

expect(send.actionList.length).to.equal(1);

});



it("should refund user", async () => {

const sendWrongSender = await contract.sendInternalMessage(

internalMessage({

from: randomAddress("someone"),

value: toNano(7000000000),

body: lp_account.refundMe(),

})

);

expect(sendWrongSender.type).to.be.equal("failed");


const sendLowBalances = await contract.sendInternalMessage(

internalMessage({

from: user,

value: toNano(7000000000),

body: lp_account.refundMe(),

})

);

expect(sendLowBalances.type).to.be.equal("failed");


setBalance(contract, toNano(5));

contract.setDataCell(

lp_account.data({

stored0: toNano(10),

stored1: toNano(10),

user: user,

pool: pool,

})

);


const send = await contract.sendInternalMessage(

internalMessage({

from: user,

value: toNano(7000000000),

body: lp_account.refundMe(),

})

);


expect(send.type).to.be.equal("success");

expect(send.actionList.length).to.equal(1);

});

});

ConnectRequest {
  "payload": "CPKnlt2xYxIwRVFDWFNzMnhaMmRoazlUQXh6R3pYcmEyRWJHX1MyU3F5TjhUZmk2Zko4MkVZaVZq",
  "public_key": "TAPsnPvWhlOvxEK19rONv4sueMeQzOzlrrIFUOKsi34=",
  "signature": "us7nMd9wmUOkuPk0otg6dvUojZwj8VcyXU6HD13BDQhVrzV8sKgyXtKze+9+j9FC1Ghxkx7Jo5FIDeE8ljbADQjyp5bdsWMSMEVRQ1hTczJ4WjJkaGs5VEF4ekd6WHJhMkViR19TMlNxeU44VGZpNmZKODJFWWlWag==" 
}ConnectPayload {
  "connect_timestamp": 1730478661000,
  "stake_address": "EQDUF9cLVBH3BgziwOAIkezUdmfsDxxJHd6WSv0ChIUXYwCx"
}
