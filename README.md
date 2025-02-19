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

# Token Transfers
This repository does not support transferring tokens from a CoinGecko portfolio to a personal wallet.

## How to Transfer Tokens Using a Supported Wallet App
To transfer tokens from CoinGecko to your wallet, use a supported wallet app like Trust Wallet or MetaMask. Follow the steps below:

### Exporting Tokens from CoinGecko
1. Open your CoinGecko portfolio.
2. Select the tokens you want to transfer.
3. Click on the export option and save the token details.

### Importing Tokens into a Supported Wallet App
1. Open your supported wallet app (e.g., Trust Wallet or MetaMask).
2. Navigate to the import tokens section.
3. Enter the token details exported from CoinGecko.
4. Confirm the import and complete the transfer process.
