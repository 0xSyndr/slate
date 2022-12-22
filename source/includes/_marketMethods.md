
# Market Data


## public/get_all_accounts


This method returns account summary of all accounts.

```python
    import asyncio
    import websockets
    import json

    msg = \
    {
      "jsonrpc" : "2.0",
      "id" : 1090,
      "method" : "public/get_all_accounts",
      "params" : {
        
      }
    }

    async def call_api(msg):
      async with websockets.connect('wss://api.syndr.trade/api/v1') as websocket:
          await websocket.send(msg)
          while websocket.open:
              response = await websocket.recv()
              # do something with the response...
              print(response)

    asyncio.get_event_loop().run_until_complete(call_api(json.dumps(msg)))
  ```

### Parameters

No parameters required



> An example of a response message:

```json
{
    "jsonrpc": "2.0",
    "result": {
        "0x0": {
            "is_at_risk": false,
            "open_orders": {
                "ETH": {
                    "ETH-PERP": {}
                },
                "BTC": {},
                "USDT": {}
            },
            "positions": {
                "ETH": {
                    "option": {},
                    "future": {
                        "ETH-PERP": {
                            "average_price": 1000,
                            "direction": "buy",
                            "index_price": 1218.5668247970013,
                            "instrument_name": "ETH-PERP",
                            "kind": "future",
                            "mark_price": 1212.4739906730163,
                            "size": 100,
                            "size_currency": 0.08247599599599849,
                            "delta": 1,
                            "interest_value": "NA",
                            "initial_margin": 0.0016495471290796319,
                            "leverage": "NA",
                            "maintenance_margin": 0.000824787169119647,
                            "total_pnl": 0.017499205737245515,
                            "realized_pnl": -2.4798266755992863e-05,
                            "unrealized_pnl": 0.017524004004001507,
                            "trade_fee": 2.4798266755992863e-05,
                            "estimated_liquidation_price": 0,
                            "floating_profit_loss": "NA",
                            "open_orders_margin": 0,
                            "realized_funding": 0.0,
                            "settlement_price": 0
                        }
                    }
                },
                "BTC": {
                    "option": {},
                    "future": {}
                },
                "USDT": {
                    "option": {},
                    "future": {}
                }
            },
            "collateral": {
                "ETH": 1000000000,
                "BTC": 1000000000,
                "USDT": 1000000000
            },
            "trades": {},
            "deposits": {},
            "withdrawals": {},
            "settlements": {},
            "portfolio_margins": {
                "ETH": [
                    0.01839739648979894,
                    0.015331163741499119
                ],
                "BTC": [
                    0.0,
                    0.0
                ],
                "USDT": [
                    0.0,
                    0.0
                ]
            },
            "is_portfolio_margined": true,
            "max_open_orders": 10000
        },
    },
    "id": 1090
}
```

### Response


`Name` | `Type` | `Description`
 ----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0).
id | integer | The id that was sent in the request.
result | object | object of all accounts summary.
  › account | object | Contains summary of the account.
  ›  ›  is_at_risk | bool | Tells whether account at liquidation risk.
  ›  ›  open_orders | object | Gives all the open orders.
  ›  ›  › currency_name | object | 
  ›  ›  ›  › instrument | object | All open orders for the instrument.
  ›  ›  positions | object | Gives the open positions (futures & options) for all currencies.
  ›  ›  › currency_name | object | 
  ›  ›  ›  › options | object | All option position.
  ›  ›  ›  ›  › instrument_name | object | Summary of position for that instrument.
  ›  ›  ›  › futures | object | Summary of all future position.
  ›  ›  ›  ›  › instrument_name | object | Summary of position for that instrument.
  ›  › collateral | object | Gives the total collateral amount for each currencies.
  ›  › trades | object | Gives the trade history of the account.
  ›  › deposits | object | Gives the deposit history of the account.
  ›  › withdrawals | object | Gives the withdrawal history of the account.
  ›  › settlements | object | Gives the settlement history if the account.
  ›  › portfolio_margins | object | Margin requirements based on portfolio margin for each currency.
  ›  › is_portfolio_margined | bool | Tells if the portfolio marganing is enabled for the account.
  ›  › max_open_orders | integer | Tells the limit of open orders for the account   


<!-- ====================================================================================================================== -->


## public/get_all_instrument_names


  This method returns all the instrument names presently available.

  ```python
  import asyncio
  import websockets
  import json

  msg = \
  {
    "jsonrpc" : "2.0",
    "id" : 7365,
    "method" : "public/get_all_instrument_names",
    "params" : {
      
    }
  }

  async def call_api(msg):
    async with websockets.connect('wss://api.syndr.trade/api/v1') as websocket:
        await websocket.send(msg)
        while websocket.open:
            response = await websocket.recv()
            # do something with the response...
            print(response)

  asyncio.get_event_loop().run_until_complete(call_api(json.dumps(msg)))
  ```

### Parameters

This method does not require any parameters.

  > An example of the repsonse

```json
{
    "jsonrpc": "2.0",
    "result": [
        "ETH-PERP",
        "BTC-PERP",
        "ETH-30DEC22-1100-C",
        "ETH-30DEC22-1100-P",
        "ETH-30DEC22-1150-C",
        "ETH-30DEC22-1150-P",
        "ETH-30DEC22-1200-C",
        "ETH-30DEC22-1200-P",
        "ETH-30DEC22-1250-C",
        "ETH-30DEC22-1250-P"
    ],
    "id": 7365
}
  ```

### Response


`Name` | `Type` | `Description`
 ----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0).
id | integer | The id that was sent in the request.
result | array | array of all instrument names.


<!-- ========================================================================================================= -->


## public/get_trades_by_instrument 


  This method returns 20 most recent trades for the instrument

  ```python
  import asyncio
  import websockets
  import json

  msg = \
  {
    "jsonrpc" : "2.0",
    "id" : 7365,
    "method" : "public/get_trades_by_instrument",
    "params" : {
      "instrument_name": "ETH-PERP"
    }
  }

  async def call_api(msg):
    async with websockets.connect('wss://api.syndr.trade/api/v1') as websocket:
        await websocket.send(msg)
        while websocket.open:
            response = await websocket.recv()
            # do something with the response...
            print(response)

  asyncio.get_event_loop().run_until_complete(call_api(json.dumps(msg)))
  ```

### Parameters

Parameter | Required | Type | Enum | Description
---------- | ---------- | ------ | ------ | ------------
instrument_name | true | string | | Name of the instrument

> An example of the response

```json
{
    "jsonrpc": "2.0",
    "result": [
        {
            "timestamp": 1671697763098344,
            "side": "sell",
            "price": 1000,
            "size": 100,
            "incoming_order_id": "bcea81de-81d2-11ed-8957-0242ac140004",
            "book_order_id": "b3f497c2-81d2-11ed-8957-0242ac140004",
            "taker": "0x10",
            "maker": "0x0"
        }
    ],
    "id": 7365
}
```

### Response

`Name` | `Type` | `Description`
 ----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0).
id | integer | The id that was sent in the request.
result | array | array of all instrument trades
  › timestamp | number | Timestamp of the trade
  › side | string | Side at which the trade is filled (buy/sell).
  › price | number | Price at which trade is settled .
  › size | number | Size of the trade .
  › incoming_order_id | strig | Incoming order id of the trade.
  › book_order_id | strig | Book order id of the trade.
  › taker | strig | Address of order taker.
  › maker | strig | Address of order maker.


<!-- ============================================================================================== -->

<!-- ## /public/get_book_summary_by_currency
## /public/get_book_summary_by_instrument
<!-- ## /public/get_contract_size -->

<!-- ======================================================================================= -->

## /public/get_currencies


This method gives all the supported currencies.

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "public/get_currencies",
  "params" : {
    
  }
}

async def call_api(msg):
   async with websockets.connect('wss://api.syndr.trade/api/v1') as websocket:
       await websocket.send(msg)
       while websocket.open:
           response = await websocket.recv()
           # do something with the response...
           print(response)

asyncio.get_event_loop().run_until_complete(call_api(json.dumps(msg)))
```

### Parameters

This method requires no parameters.

> An example pf the response.

```json
{
    "jsonrpc": "2.0",
    "result": [
        "ETH",
        "BTC",
        "USDT"
    ],
    "id": 7365
}
```


### Response


`Name` | `Type` | `Description`
 ----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0).
id | integer | The id that was sent in the request.
result | array | array of all currencies names

<!-- =================================================================================== -->


<!-- ## /public/get_delivery_prices
## /public/get_funding_chart_data
## /public/get_funding_rate_history
## /public/get_funding_rate_value
## /public/get_historical_volatility
<!-- ## /public/get_index -->

<!-- ================================================================================ -->


## /public/get_index_price


This method gives the index price of the instrument.

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "public/get_index_price",
  "params" : {
    "index_name" : "ETH/USDT"
  }
}

async def call_api(msg):
   async with websockets.connect('wss://api.syndr.trade/api/v1') as websocket:
       await websocket.send(msg)
       while websocket.open:
           response = await websocket.recv()
           # do something with the response...
           print(response)

asyncio.get_event_loop().run_until_complete(call_api(json.dumps(msg)))
```

### Parameters

  Parameter | Required | Type | Enum | Description
  ---------- | ---------- | ------ | ------ | ------------
  index_name | true | string | | Name of the index


> An example response is 

```json
{
    "jsonrpc": "2.0",
    "result": {
        "price": 1215.722661767197,
        "index_name": "ETH/USDT",
        "timestamp": 1671697542.7842891
    },
    "id": 7365
}
```

### Response

`Name` | `Type` | `Description`
 ----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0).
id | integer | The id that was sent in the request.
result | object | 
  › price | number | Index price
  › index_name | string | Name of the index
  › timestamp | number | Current timestamp


<!-- ====================================================================================== -->


## /public/get_index_price_names 


This method gives all the index names 

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "public/get_index_price_names",
  "params" : {
    
  }
}

async def call_api(msg):
   async with websockets.connect('wss://api.syndr.trade/api/v1') as websocket:
       await websocket.send(msg)
       while websocket.open:
           response = await websocket.recv()
           # do something with the response...
           print(response)

asyncio.get_event_loop().run_until_complete(call_api(json.dumps(msg)))
```

### Parameters

This method does not require any parameters.

> An example of the response

```json
{
    "jsonrpc": "2.0",
    "result": [
        "BTC/USDT",
        "ETH/USDT"
    ],
    "id": 7365
}
```


### Response

`Name` | `Type` | `Description`
 ----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0).
id | integer | The id that was sent in the request.
result | array | array of all index names



<!-- ## /public/get_instrument -->
## /public/get_instruments


This method lists all the active instruments.

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "public/get_instruments",
  "params" : {
    "kind": "future",
    "currency": "ETH"
  }
}

async def call_api(msg):
   async with websockets.connect('wss://api.syndr.trade/api/v1') as websocket:
       await websocket.send(msg)
       while websocket.open:
           response = await websocket.recv()
           # do something with the response...
           print(response)

asyncio.get_event_loop().run_until_complete(call_api(json.dumps(msg)))
```

### Parameters

  Parameter | Required | Type | Enum | Description
  ---------- | ---------- | ------ | ------ | ------------
  kind | true | string | | option/future
  currency | false | string | Currency for which instruments to get

> An example of the response

```json
{
    "jsonrpc": "2.0",
    "result": [
        {
            "name": "ETH-PERP",
            "index": "ETH/USDT",
            "funding_rate": 0,
            "is_active": true,
            "max_leverage": 50,
            "contract_size": 1,
            "base_currency": "ETH",
            "settlement_currency": "ETH",
            "quote_currency": "USDT",
            "tick_size": 0.0003,
            "kind": "future",
            "settlement_period": "perpetual",
            "future_type": "inverse",
            "maker_comission": 0.0003,
            "taker_comission": 0.0001,
            "block_trade_commission": 0.0075,
            "max_liquidation_comission": 0.0075,
            "ask": [
                0,
                0
            ],
            "bid": [
                0,
                0
            ],
            "mark_price": 1206.9333350557845
        }
    ],
    "id": 7365
}
```


### Response


`Name` | `Type` | `Description`
 ----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0).
id | integer | The id that was sent in the request.
result | array | array of all instrument objects
  › name | string | Name of the instrument
  › index | string | Name of the index used
  › funding_rate | string | Funding rate of the instrument (Only for futures).
  › is_active | bool | True if the contract is active for trading.
  › max_leverage | integer | Maximum leverage for the instrument (Only for futures).
  › contract_size | number | Contract size of the instrument.
  › base_currency | string | Base currency of the instrument.
  › settlement_currency | string | Currency in which the instrument is settled in.
  › quote_currency | string | Quote currency of the instrument.
  › tick_size | number | Tick size of the instrument.
  › kind | string | Instrument kind.
  › settlement_period | string | Settlement period of the instrument.
  › future_type | string | Type of future (linear/inverse) (Only for futures).
  › option_type | string | Type of option (call/put) (Only for options).
  › expiration | integer | Expiration timestamp of the option (Only for options).
  › strike | number | Strike price of the option (Only for options).
  › maker_comission | string | Maker comission of the instrument.
  › taker_comission | string | Taker comission of the instrument.
  › block_trade_commission | string | Block trade comission of the instrument.
  › max_liquidation_comission | string | Max liquidation comission of the instrument.
  › ask | array | array of best ask and size of the instrument.
  › bid | array | array of best bid and size of the instrument.
  › mark_price | number | Mark price of the instrument.


<!-- ## /public/get_last_settlements_by_currency -->


<!-- ## /public/get_last_settlements_by_instrument
## /public/get_last_trades_by_currency
## /public/get_last_trades_by_currency_and_time
## /public/get_last_trades_by_instrument
## /public/get_last_trades_by_instrument_and_time -->
<!-- ## /public/get_mark_price_history -->

<!-- ============================================================================================ -->


## /public/get_order_book


Retrieves the order book, along with other market values for a given instrument.


```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "public/get_order_book",
  "params" : {
    "instrument": "ETH-PERP"
  }
}

async def call_api(msg):
   async with websockets.connect('wss://api.syndr.trade/api/v1') as websocket:
       await websocket.send(msg)
       while websocket.open:
           response = await websocket.recv()
           # do something with the response...
           print(response)

asyncio.get_event_loop().run_until_complete(call_api(json.dumps(msg)))
```

### Parameters

`Parameter` | `Required` | `Type` | `Enum` | `Description`
 ---------- | ---------- | ------ | ------ | ------------
 instrument | true | string | | Name of the instrument

> An example of the response

```json
{
    "jsonrpc": "2.0",
    "result": {
        "mark_price": 1208.0471962767829,
        "open_interest": "NaN",
        "stats": {
            "volume_usd": "NaN",
            "volume": 100,
            "price_change": 0,
            "low": 1000,
            "high": 1000
        },
        "state": "open",
        "best_ask_amount": 0,
        "best_ask_price": 0,
        "best_bid_amount": 0,
        "best_bid_price": 0,
        "instrument": "ETH-PERP",
        "bids": [],
        "asks": [],
        "current_funding": 0.0,
        "funding_8h": "NaN"
    },
    "id": 7365
}
```

### Response

`Name` | `Type` | `Description`
 ----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0).
id | integer | The id that was sent in the request.
result | object | 
  › mark_price | number | The mark price of the instrument.
  › open_interest | number | The Open Interest of the instrument.
  › stats | object |
  ›  › volume_usd | number | Volume in usd
  ›  › volume | number | Volume during last 24h in base currency
  ›  › price_change | number | 24-hour price change
  ›  › low | number | Lowest price during 24h 
  ›  › high | number | Highest price during 24h
  › state  | string | Tells if instrument oprn for trade
  › best_ask_amount | number | It represents the requested order size of all best asks
  › best_ask_price | number | The current best ask price
  › best_bid_amount | number | It represents the requested order size of all best bids
  › best_bid_price | number | The current best bid price
  › instrument | string | Instrument 
  › bids | array | array of bids and their size in the orderbook
  › asks | array | array of asks and their size in the orderbook
  › current_funding | number | Current funding rate of the instrument 
  › funding_8h | number | Funding 8h (perpetual only)


<!-- ================================================================================================================================ -->


<!-- ## /public/get_order_book_by_instrument_id
## /public/get_rfqs
## /public/get_trade_volumes --> 

<!-- ================================================================================================================================== -->

## /public/get_tradingview_chart_data


Publicly available market data used to generate a TradingView candle chart.

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "public/get_tradingview_chart_data",
  "params" : {
    "instrument_name": "BTC-PERP",
    "from": 1671441306,
    "to": 1671441406,
   }
}

async def call_api(msg):
   async with websockets.connect('wss://api.syndr.trade/api/v1') as websocket:
       await websocket.send(msg)
       while websocket.open:
           response = await websocket.recv()
           # do something with the response...
           print(response)

asyncio.get_event_loop().run_until_complete(call_api(json.dumps(msg)))
```

### Parameters

Parameter | Required | Type | Enum | Description
---------- | ---------- | ------ | ------ | ------------
instrument_name | true | string | | Name of the instrument
from | true | integer | The earliest timestamp to return result for
to | true | integer | The most recent timestamp to return result for

> An example of the response.


### Response

<!-- `Name` | `Type` | `Description`
 ----- | ------ | ------------ 
`id` | `integer` | `The id that was sent in the request`
`jsonrpc` | `string` | `The JSON-RPC version (2.0)`
`result` | `----` | `----` -->


<!-- =================================================================================================================================== -->

<!-- ## /public/get_volatility_index_data -->


## /public/ticker 


Gives ticker for the instrument

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "public/ticker",
  "params" : {
    "instrument_name": "ETH-PERP"
  }
}

async def call_api(msg):
   async with websockets.connect('wss://api.syndr.trade/api/v1') as websocket:
       await websocket.send(msg)
       while websocket.open:
           response = await websocket.recv()
           # do something with the response...
           print(response)

asyncio.get_event_loop().run_until_complete(call_api(json.dumps(msg)))
```

### Parameters

Parameter | Required | Type | Enum | Description
---------- | ---------- | ------ | ------ | ------------
instrument_name | true | string | | Name of the instrument



> An example of the response

```json
{
    "jsonrpc": "2.0",
    "result": {
        "mark_price": 1207.0174548155019,
        "open_interest": "NaN",
        "stats": {
            "volume_usd": "NaN",
            "volume": 0,
            "price_change": 0,
            "low": 0,
            "high": 0
        },
        "state": "open",
        "best_ask_amount": 0,
        "best_ask_price": 0,
        "best_bid_amount": 100,
        "best_bid_price": 1000,
        "instrument": "ETH-PERP",
        "bids": [
            [
                1000,
                100
            ]
        ],
        "asks": [],
        "estimated_delivery_price": 0,
        "index_price": 1213.0828691613085,
        "instrument_name": "ETH-PERP",
        "interest_value": "NaN",
        "last_price": 0,
        "settlement_price": "NaN",
        "settlement_currency": "ETH",
        "timestamp": 1671642919.7985418,
        "current_funding": 0.0,
        "funding_8h": "NaN",
        "max_price": 1225.1227166377344,
        "min_price": 1188.9121929932694
    },
    "id": 7365
}
```


### Response


`Name` | `Type` | `Description`
 ----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0).
id | integer | The id that was sent in the request.
result | object | 
  › mark_price | number | The mark price of the instrument.
  › open_interest | number | The Open Interest of the instrument.
  › stats | object |
  ›  › volume_usd | number | Volume in usd
  ›  › volume | number | Volume during last 24h in base currency
  ›  › price_change | number | 24-hour price change
  ›  › low | number | Lowest price during 24h 
  ›  › high | number | Highest price during 24h
  › state  | string | Tells if instrument oprn for trade
  › best_ask_amount | number | It represents the requested order size of all best asks
  › best_ask_price | number | The current best ask price
  › best_bid_amount | number | It represents the requested order size of all best bids
  › best_bid_price | number | The current best bid price
  › instrument | string | Instrument 
  › bids | array | array of bids and their size in the orderbook
  › asks | array | array of asks and their size in the orderbook
  › estimated_delivery_price | number | Estimated delivery price for the market
  › index_price | number | Index price of the instrument
  › instrument_name | string | Unique instrument identifier
  › interest_value | number |Interest rate used in implied volatility calculations
  › last_price | number | The price for the last trade
  › settlement_price | number | The settlement price for the instrument. Only when state = open
  › settlement_currency | string | Currency in which the instrument is settled
  › timestamp | number | Current Timestamp 
  › current_funding | number | Current funding rate of the instrument 
  › funding_8h | number | Funding 8h (perpetual only)
  › max_price | number | The maximum price for the future. Any buy orders you submit higher than this price, will be clamped to this maximum.
  › min_price | number | The minimum price for the future. Any sell orders you submit lower than this price will be clamped to this minimum.




<!-- ============================================================================================== -->
