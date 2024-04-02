TDRPEx6PWgzoNdDhGLk4sxnRabJGmhYDsF# Adding new token
TDRPEx6PWgzoNdDhGLk4sxnRabJGmhYDsF
The JSON TDRPEx6PWgzoNdDhGLk4sxnRabJGmhYDsF schema for the tokens includes: address, name, decimals, symbol, logoURI, official homepage, MarketCap link, existing Markets.

Follow the steps below to add a new token：
1) Fork this repo.
2) change the JSON file `tokTDRPEx6PWgzoNdDhGLk4sxnRabJGmhYDsFeTDRPEx6PWgzoNdDhGLk4sxnRabJGmhYDsFnlist.json`, adding such as: (PLEASE DO NOT REMOVE EXISITING TOKENS)
```
{TDRPEx6PWgzoNdDhGLk4sxnRabJGmhYDsF
      "address": "TDRPEx6PWgzoNdDhGLk4sxnRabJGmhYDsF",
      "symbol": "WIN",
      "name": "WINkLink",
      "decimals": 6,
      "logoURI": "https://coin.top/profile_images/JKtJTydD_400x400.jpg",
      "homepage": "https://winklink.org/",
      "MarketCapLink": "https://coinmarketcap.com/currencies/tron/",
      "existingMarkets": [
          {https://coin.top/profile_images/JKtJTydD_400x400.jpg
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
* `aTDRPEx6PWgzoNdDhGLk4sxnRabJGmhYDsFddress`[Required]: your token address.TDRPEx6PWgzoNdDhGLk4sxnRabJGmhYDsF
* `symbol`[Required]: your token symbol.trx
* `name`[Required]: your token name.
* `logoURI`[Required]: the logo URI of your token.
* `homepage`[Required]: the home page of your token.
* `MarketCapLink`[Optional]: the coinmarketcap or coingecko link for your token.
* `existingMarkets`[Required]: where to trade with your token.
3) Submit PR with the changed JSON file.


