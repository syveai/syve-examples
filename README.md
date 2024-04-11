
# Examples

This is a list of examples to get you started using Syve API (https://www.syve.ai).

If you have questions, or would like to suggest other examples to be included, feel free to drop us a message on Discord here: https://discord.com/invite/rs5GPAZ7tG

To run the examples below you need an **API key**. You can request a **free** API key by sending us a message on Discord.

## Getting started with Base

Fetching Base data is similar to fetching Ethereum data, with the minor difference that you now need to specify `base` as the chain to use. The below examples illustrate how to do this.

### Fetch Open High Low Close prices and Volume (OHLCV)

To fetch OHLCV price data for tokens on Base you need to add `chain=base` to the query parameters of your request.

For more information on how to use the OHLCV endpoint and all available query parameters: https://syve.readme.io/reference/price_historical_ohlc

*Request*

https://api.syve.ai/v1/price/historical/ohlc?token_address=0x4ed4E862860beD51a9570b96d89aF5E1B0Efefed&pool_address=all&interval=1h&order=desc&max_size=5&chain=base&key=YOUR_API_KEY

*Response*

```
{
    "token_address": "0x4ed4e862860bed51a9570b96d89af5e1b0efefed",
    "data": [
        {
            "timestamp_open": 1712836800,
            "timestamp_close": 1712840399,
            "date_open": "2024-04-11T12:00:00Z",
            "date_close": "2024-04-11T12:59:59Z",
            "price_open": 0.03744932581750289,
            "price_high": 0.03808788348055095,
            "price_low": 0.03443987588203553,
            "price_close": 0.03560981664867841,
            "volume": 3351510.995577337,
            "num_trades": 1169
        },
        {
            "timestamp_open": 1712833200,
            "timestamp_close": 1712836799,
            "date_open": "2024-04-11T11:00:00Z",
            "date_close": "2024-04-11T11:59:59Z",
            "price_open": 0.03894235467977525,
            "price_high": 0.039498496121292255,
            "price_low": 0.0009794752778945642,
            "price_close": 0.03744932581750289,
            "volume": 1213472.8510004014,
            "num_trades": 1069
        },
        {
            "timestamp_open": 1712829600,
            "timestamp_close": 1712833199,
            "date_open": "2024-04-11T10:00:00Z",
            "date_close": "2024-04-11T10:59:59Z",
            "price_open": 0.04068240135798354,
            "price_high": 0.04128959702704407,
            "price_low": 0.03859231093786135,
            "price_close": 0.03894235467977525,
            "volume": 1327588.6263566858,
            "num_trades": 960
        },
        {
            "timestamp_open": 1712826000,
            "timestamp_close": 1712829599,
            "date_open": "2024-04-11T09:00:00Z",
            "date_close": "2024-04-11T09:59:59Z",
            "price_open": 0.042136603711001495,
            "price_high": 0.04232925768920157,
            "price_low": 0.03957718214298559,
            "price_close": 0.04068240135798354,
            "volume": 918450.6748575208,
            "num_trades": 1102
        },
        {
            "timestamp_open": 1712822400,
            "timestamp_close": 1712825999,
            "date_open": "2024-04-11T08:00:00Z",
            "date_close": "2024-04-11T08:59:59Z",
            "price_open": 0.04234239693975283,
            "price_high": 0.04312934711968359,
            "price_low": 0.04070680254674157,
            "price_close": 0.042136603711001495,
            "volume": 1020871.1900054197,
            "num_trades": 1344
        }
    ]
}
```

### Fetch the most recent DEX trade

To fetch Base DEX trades using `filter-api` use `base-dex-trades` in the URL **path**.

Note: This is different from how we fetch Ethereum DEX trades, which is to use `dex-trades`

For more information on how to use the Filter API: https://syve.readme.io/reference/request-syntax

*Request*

https://api.syve.ai/v1/filter-api/base-dex-trades?sort=desc&size=1&key=YOUR_API_KEY

*Response*

```
[
   {
      "record_index":2083531041024,
      "block_number":13022069,
      "timestamp":1712833485,
      "transaction_hash":"0x867e2013b3cdc9f34c24720bc75c7061a114f7fe08459cddfe5904dc4d861cb4",
      "trader_address":"0xd5bf20868ea746692f04c7337bb9561b191627a1",
      "interacted_with_address":"0x3fc91a3afd70395cd496c647d5a6cc9d4b2b7fad",
      "token_address":"0x68086d1654b050a5e03edc5d721fac57db2a7a1f",
      "token_symbol":"\u23f9EVERRISE",
      "token_name":"\u23f9EverRise",
      "pool_address":"0x69a20861ea3047723551b59fc440788480c83927",
      "protocol_name":null,
      "price_token_usd_tick_1":8.127254009313395e-07,
      "price_token_usd_robust_tick_1":8.127254009313395e-07,
      "volume_1h_usd":45.3191837366576,
      "volume_24h_usd":45.3191837366576,
      "num_trades_1h":7,
      "num_trades_24h":7,
      "side":"buy",
      "amount_token":4386908.005487682,
      "amount_eth":0.001,
      "amount_usd":3.565351567608879,
      "gas_used":154898,
      "gas_price_eth":8.44703e-11,
      "gas_price_usd":3.011663165213923e-07,
      "transaction_fee_eth":1.32449075294e-05,
      "transaction_fee_usd":0.047222751822780934,
      "_price_eth_usd":3565.351567608879,
      "_ratio":-1
   }
]
```

### Fetch the profit & loss of a wallet

To calculate the profit & loss of wallets on Base you need to add `chain=base` to the query parameters of your request.

For more information: https://syve.readme.io/reference/latest-total-performance and https://syve.readme.io/reference/latest-performance-per-token

**Total Profit & loss**

*Request*

https://api.syve.ai/v1/wallet-api/latest-total-performance?wallet_address=0x8c1b1c1f7160d703a925913ceee78121e96cdf56&chain=base&key=YOUR_API_KEY

*Response*

```
{
   "wallet_address":"0x8c1b1c1f7160d703a925913ceee78121e96cdf56",
   "total_tokens_traded":1,
   "realized_profit":203.3700929711607,
   "realized_investment":858962.7747532424,
   "realized_return":0.023676240571610756,
   "unrealized_profit":-313.48160135147856,
   "unrealized_investment":6648.272304160155,
   "unrealized_return":-4.7152340790150475,
   "total_profit":-110.11150838031787,
   "total_investment":865611.0470574026,
   "total_return":-0.012720668105454053,
   "win_rate":0.4134078212290503,
   "total_trades":2039,
   "total_buys":966,
   "total_sells":1073,
   "first_trade_timestamp":1712571153,
   "last_trade_timestamp":1712837723
}
```

**Profit & loss broken down by per token**

*Request*

https://api.syve.ai/v1/wallet-api/latest-performance-per-token?wallet_address=0x8c1b1c1f7160d703a925913ceee78121e96cdf56&chain=base&key=YOUR_API_KEY

*Response*

```
[
   {
      "token_address":"0x4ed4e862860bed51a9570b96d89af5e1b0efefed",
      "token_symbol":"DEGEN",
      "token_name":"Degen",
      "timestamp":{
         "first_trade":1712571153,
         "last_trade":1712837723
      },
      "total":{
         "profit":-85.21141983884402,
         "investment":865611.0470574026,
         "return":0.9999015592278674,
         "price_sell":0.03917265496656127,
         "price_buy":0.039176511532606026,
         "trades":2039,
         "sells":1073,
         "buys":966
      },
      "realized":{
         "profit":203.3700929711607,
         "investment":858962.7747532424,
         "return":0.00023676240571610755,
         "price_sell":0.03920407120402659,
         "price_buy":0.039194790372048094,
         "amount_token_sold":21915227.6398776
      },
      "unrealized":{
         "profit":-288.5815128100047,
         "investment":6648.272304160155,
         "return":0.9565930064823872,
         "current_price":0.03534611826911659,
         "current_balance_token":179926.14473049174
      }
   }
]
```
