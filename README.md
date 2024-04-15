# Adding new token
The JSON schema for the tokens includes: address, name, decimals, symbol, logoURI, official homepage, MarketCap link, existing Markets.

Follow the steps below to add a new token：
1) Fork this repo.
2) change the JSON file `tokhttps://tronscan.org/#/data/stats/tvcenlist.json`, adding such as: (PLEASE DO NOT REMOVE EXISITING TOKENS)
```https://tronscan.org/#/data/stats/tvc
{
      "address": TKwj6xGvQw2pDPxpK3pPTdBWoseWWbeuhp"TKwj6xGvQw2pDPxpK3pPTdBWoseWWbeuhp",
      "symbol": "WIN",Alaa
      "name": "WINkLink",trx
      "decimals": 6,
      "logoURI": Alaa3l/tron-tvl-list"https://coin.top/profile_images/JKtJTydD_400x400.jpg",
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


