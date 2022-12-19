
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

<!-- ```json
    {
        "jsonrpc": "2.0",
        "id": 1090,
        "result": {
            "status": "success",
            "data": {
                    "0x86abfe36d170db0d6d3dc74727f41a5ec1b4c18f": {
                        "is_at_risk": false,
                        "open_orders": {
                            "ETH-PERP": {},
                            "BTC-PERP": {},
                            "ETH-16DEC22-1100-C": {},
                            "ETH-16DEC22-1100-P": {},
                        },
                        "positions": {
                            "ETH": {
                                "option": {},
                                "future": {}
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
                        "is_portfolio_margined": true,
                        "max_open_orders": 10000
                    }
                },
            },
    }
``` -->

### Response

<!-- To-DO ==> reduce the respnse structure

Name | Type | Description
----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0)
id | integer | The id that was sent in the request
result | object | ----
> status | string | Tells success or failure 
> data | object | 
> > account | object | Contains summary of the account
> > >  is_at_risk | bool | Tells whether account at liquidation risk
> > > open_orders | object | Gives the open orders for all instruments
> > > positions | object | Gives the open positions (futures & options) for all currencies
> > > collateral | object | Gives the total collateral amount for each currencies
> > > trades | object | Gives the trade history of the account
> > > withdrawals | object | Gives the withdrawal history of the account
> > > settlements | object | Gives the settlement history if the account
> > > is_portfolio_margined | bool | Tells if the portfolio marganing is enabled for the account
> > > max_open_orders | integer | Tells the limit of open orders for the account    -->


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

<!-- ```json
  {
      "jsonrpc": "2.0",
      "result": {
          "status": "success",
          "resp": {
              "jsonrpc": "2.0",
              "result": {
                  "req_id": 354,
                  "result": [
                      "ETH-PERP",
                      "BTC-PERP",
                      "ETH-16DEC22-1100-C",
                      "ETH-16DEC22-1100-P",
                      "ETH-16DEC22-1150-C",
                      "ETH-16DEC22-1150-P",
                      "ETH-16DEC22-1200-C",
                      "ETH-16DEC22-1200-P",
                      "ETH-16DEC22-1250-C",
                      "ETH-16DEC22-1250-P",
                      "ETH-30DEC22-1100-C",
                      "ETH-30DEC22-1100-P",
                      "ETH-30DEC22-1150-C",
                      "ETH-30DEC22-1150-P",
                      "ETH-30DEC22-1200-C",
                      "ETH-30DEC22-1200-P",
                      "ETH-30DEC22-1250-C",
                      "ETH-30DEC22-1250-P"
                  ]
              },
              "id": 1
          }
      },
      "id": 7365
  }
  ``` -->

### Response

<!-- To-DO ==> reduce the respnse structure

Name | Type | Description
----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0)
id | integer | The id that was sent in the request
result | object | ----
> status | string | Tells success or failure 
> data | object | Gives all instruments name that are currently active -->


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

<!-- ```json
"To DO"
``` -->

### Response

<!-- To-DO ==> reduce the respnse structure

Name | Type | Description
----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0)
id | integer | The id that was sent in the request
result | object | ----
> status | string | Tells success or failure 
> data | object | Array of recent trades -->


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
<!-- 
```json
{
    "jsonrpc": "2.0",
    "result": {
        "status": "success",
        "resp": {
            "jsonrpc": "2.0",
            "result": {
                "req_id": 725,
                "result": [
                    "ETH",
                    "BTC",
                    "USDT"
                ]
            },
            "id": 1
        }
    },
    "id": 7365
}
``` -->


### Response

<!-- To-DO ==> reduce the respnse structure

  Name | Type | Description
  ----- | ------ | ------------ 
  jsonrpc | string | The JSON-RPC version (2.0)
  id | integer | The id that was sent in the request
  result | object | ----
  > status | string | Tells success or failure 
  > data | object | All currencies supported -->

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

<!-- ```json
{
    "jsonrpc": "2.0",
    "result": {
        "status": "success",
        "resp": {
            "jsonrpc": "2.0",
            "result": {
                "req_id": 1038,
                "result": {
                    "price": 1180.135277679183,
                    "index_name": "ETH/USDT",
                    "timestamp": 1671260778.1806843
                }
            },
            "id": 1
        }
    },
    "id": 7365
}
``` -->

### Response

<!-- To-DO ==> reduce the respnse structure

  Name | Type | Description
  ----- | ------ | ------------ 
  jsonrpc | string | The JSON-RPC version (2.0)
  id | integer | The id that was sent in the request
  result | object | ----
  > status | string | Tells success or failure 
  > data | object | 
  > > price | integer | Index price
  > > index_name | string | Name of index
  > > > timestamp | integer | Current timestamp -->


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

<!-- ```json
{
  "TO do"
}
``` -->


### Response

<!-- To-DO ==> reduce the respnse structure

  Name | Type | Description
  ----- | ------ | ------------ 
  jsonrpc | string | The JSON-RPC version (2.0)
  id | integer | The id that was sent in the request
  result | object | ----
  > status | string | Tells success or failure 
  > data | object | 
  > > price | integer | Index price
  > > index_name | string | Name of index
  > > > timestamp | integer | Current timestamp -->


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

<!-- ```json
{
    "jsonrpc": "2.0",
    "result": {
        "status": "success",
        "resp": {
            "jsonrpc": "2.0",
            "result": {
                "req_id": 1919,
                "result": [
                    {
                        "name": "ETH-16DEC22-1100-C",
                        "index": "ETH/USDT",
                        "is_active": true,
                        "contract_size": 1,
                        "base_currency": "ETH",
                        "settlement_currency": "ETH",
                        "quote_currency": "ETH",
                        "tick_size": 0.0003,
                        "option_type": "call",
                        "expiration": 1671177600,
                        "strike": 1100,
                        "kind": "option",
                        "settlement_period": "weekly",
                        "maker_comission": 0.0003,
                        "taker_comission": 0.00015,
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
                        "mark_price": 0.0
                    }
                ]
            },
            "id": 1
        }
    },
    "id": 7365
}
``` -->


### Response

<!-- To-DO ==> reduce the respnse structure

  Name | Type | Description
  ----- | ------ | ------------ 
  jsonrpc | string | The JSON-RPC version (2.0)
  id | integer | The id that was sent in the request
  result | object | ----
  > status | string | Tells success or failure 
  > data | array | array of instruments -->


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

`Parameter` | `Required` | `Type` | `Enum` | `Description`
 ---------- | ---------- | ------ | ------ | ------------
 instrument_name | true | string | | Name of the instrument

> An example of the response

<!-- ```json
"TO Get"
``` -->

### Response

<!-- `Name` | `Type` | `Description`
 ----- | ------ | ------------ 
`id` | `integer` | `The id that was sent in the request`
`jsonrpc` | `string` | `The JSON-RPC version (2.0)`
`result` | `----` | `----` -->


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

<!-- ```json
{
    "jsonrpc": "2.0",
    "result": {
        "status": "success",
        "resp": {
            "jsonrpc": "2.0",
            "result": {
                "req_id": 2060,
                "result": {
                    "best_ask_amount": 0,
                    "best_ask_price": 0,
                    "best_bid_amount": 0,
                    "best_bid_price": 0,
                    "instrument": "ETH-PERP",
                    "estimated_delivery_price": 0,
                    "index_price": 1182.7543628992348,
                    "instrument_name": "ETH-PERP",
                    "interest_value": "N/A",
                    "last_price": 0,
                    "mark_price": 1176.8405910847387,
                    "open_interest": 0,
                    "settlement_price": "N/A",
                    "state": "open",
                    "stats": {
                        "volume_usd": "N/A",
                        "volume": 0,
                        "price_change": 0,
                        "low": 0,
                        "high": 0
                    },
                    "timestamp": 1671262824.568207,
                    "current_funding": 0.0,
                    "funding_8h": "N/A",
                    "max_price": 1194.4931999510097,
                    "min_price": 1159.1879822184676
                }
            },
            "id": 1
        }
    },
    "id": 7365
}
``` -->


### Response

<!-- To-DO ==> reduce the respnse structure

  Name | Type | Description
  ----- | ------ | ------------ 
  jsonrpc | string | The JSON-RPC version (2.0)
  id | integer | The id that was sent in the request
  result | object | ----
  > status | string | Tells success or failure 
  > data | object | 
  ›  ask_iv | number| (Only for option) implied volatility for best ask -->




<!-- ============================================================================================== -->
