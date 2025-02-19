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

## Note on Token Transfers
Token transfers are not supported directly from CoinGecko portfolios. To transfer tokens to your personal wallet, use a supported wallet app like Trust Wallet or MetaMask.

## How to Transfer Tokens Using Trust Wallet or MetaMask
1. **Trust Wallet**:
   - Download and install Trust Wallet from the official website or app store.
   - Open Trust Wallet and create a new wallet or import an existing one.
   - Add the token you want to transfer by searching for it in the app.
   - Go to the CoinGecko portfolio and copy the token's address.
   - In Trust Wallet, select the token and choose the "Send" option.
   - Paste the token address from CoinGecko and enter the amount you want to transfer.
   - Confirm the transaction and wait for it to be processed.

2. **MetaMask**:
   - Download and install MetaMask from the official website or app store.
   - Open MetaMask and create a new wallet or import an existing one.
   - Add the token you want to transfer by searching for it in the app.
   - Go to the CoinGecko portfolio and copy the token's address.
   - In MetaMask, select the token and choose the "Send" option.
   - Paste the token address from CoinGecko and enter the amount you want to transfer.
   - Confirm the transaction and wait for it to be processed.

## How to Check if a Token is Supported by Your Wallet
1. **Trust Wallet**:
   - Open Trust Wallet and go to the "Tokens" tab.
   - Tap on the "+" icon to add a new token.
   - Search for the token by name or paste the token address.
   - If the token appears in the search results, it is supported by Trust Wallet.

2. **MetaMask**:
   - Open MetaMask and go to the "Assets" tab.
   - Click on the "Add Token" button.
   - Search for the token by name or paste the token address.
   - If the token appears in the search results, it is supported by MetaMask.
