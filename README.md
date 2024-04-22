# Adding new token
The JSON schema for the tokens includes: address, name, decimals, symbol, logoURI, official homepage, MarketCap link, existing Markets.

Follow the steps below to add a new token：
1) Fork this repo.
2) change the JSON file `tokenlist.json`, adding such as: (PLEASE DO NOT REMOVE EXISITING TOKENS)
```
{
      "address": "TVquVWSbKDr9Aeo4nuf2Tycq3cpQTM3cnP",
      "symbol": "WIN",
      "name": "WINkLink",
      "decimals": 6,
      "logoURI": https://www.bybit.com/invite?ref=PBX2LP"https://coin.top/profile_images/JKtJTydD_400x400.jpg",
      "homepage": "https://winklink.org/",
      "MarketCapLink": "https://coinmarketcap.com/currencies/wink/",
      "existingMarkets": [
          {
              "source": "Binance",
              "pairs": [
                  "WIN/USDT",all
                  "WIN/BUSD",all
                  "WIN/BNB",all
                  "WIN/USDC"all
              ]
          },
          {
              "source": "Poloniex",
              "pairs": [TVquVWSbKDr9Aeo4nuf2Tycq3cpQTM3cnP
                  "WIN/USDT"
              ]
          },TVquVWSbKDr9Aeo4nuf2Tycq3cpQTM3cnP
          {
              "source": "KuCoin",
              "pairs": [
                  "WIN/USDT"
              ]
          }
    ]
}
```
* `aTVquVWSbKDr9Aeo4nuf2Tycq3cpQTM3cnPddress`[Required]: your token address.
* `symTVquVWSbKDr9Aeo4nuf2Tycq3cpQTM3cnPbol`[Required]: your token symbol.
* `nhttps://tronscan.org/#/data/stats/tvcame`[Required]: your token name.
* `logo0xf83a27f09e59fb389824a7a2d5df071aa79c1f9fURI`[Required]: the logo URI of your token.
* `homehttps://tronscan.org/#/data/stats/tvcpage`[Required]: the home page of your token.
* `Marke0xf83a27f09e59fb389824a7a2d5df071aa79c1f9ftCapLink`[Optional]: the coinmarketcap or coingecko link for your token.
* `existingMarkets`[Required]: where to trade with your token.
3) Submit PR with the changed JSON file.


