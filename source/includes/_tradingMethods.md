

# Trading

<!-- ======================================================================================== -->

## /private/buy


This method places a buy order.

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "private/buy",
  "params" : {
    "type": "limit",
    "from": "0x0",
    "instrument_name": "ETH-PERP",
    "amount" : 100,
    "price" : 1000,
    "time_in_force": "GTC"
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
 from | true | string |  |address of sender
 instrument_name| true | string |  |Instrument name
amount | true | number |  | It represents the requested order size. For perpetual and futures the amount is in USD units, for options it is amount of corresponding cryptocurrency contracts, e.g., BTC or ETH
time_in_force | true | string | |Specifies how long the order remains in effect. Currently only GTC supported (good till canceled)
type | true | string | `limit` , `market` | The order type
label | false | string |  |user defined label for the order
price | false | number | | The order price in base currency (Only for limit)

> An example of the response

```json
{
    "jsonrpc": "2.0",
    "result": {
        "order": {
            "type": "limit",
            "from": "0x0",
            "instrument_name": "ETH-PERP",
            "amount": 100,
            "price": 1000,
            "time_in_force": "GTC"
        },
        "trades": []
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
  › order | object | Details of the order sent
  › trades | array | Array of all the trades that happen because of the order.


<!-- ============================================================================================= -->


## /private/sell


This method places a sell order.

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "private/sell",
  "params" : {
    "type": "limit",
    "from": "0x0",
    "instrument_name": "ETH-PERP",
    "amount" : 100,
    "price" : 1000,
    "time_in_force": "GTC"
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
 from | true | string |  |address of sender
 instrument_name| true | string |  |Instrument name
amount | true | number |  | It represents the requested order size. For perpetual and futures the amount is in USD units, for options it is amount of corresponding cryptocurrency contracts, e.g., BTC or ETH
time_in_force | true | string | |Specifies how long the order remains in effect. Currently only GTC supported (good till canceled)
type | true | string | `limit` , `market` | The order type
label | false | string |  |user defined label for the order
price | false | number | | The order price in base currency (Only for limit)

> An example of the response

<!-- ```json
{
    "jsonrpc": "2.0",
    "result": {
        "status": "success",
        "resp": {
            "jsonrpc": "2.0",
            "result": {
                "req_id": 4209,
                "result": {
                    "order": {
                        "type": "limit",
                        "from": "0x0",
                        "instrument_name": "ETH-PERP",
                        "amount": 10,
                        "price": 1000
                    },
                    "trades": [],
                    "status": "success"
                }
            },
            "id": 1
        }
    },
    "id": 7365
}
``` -->


### Response

`Name` | `Type` | `Description`
 ----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0).
id | integer | The id that was sent in the request.
result | object | 
  › order | object | Details of the order sent
  › trades | array | Array of all the trades that happen because of the order.


<!-- ============================================================================================= -->


<!--
## /private/edit
<!-- ## /private/edit_by_label -->

<!-- ============================================================================================== -->

## /private/cancel


This method allows to cancel a given order

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "private/cancel",
  "params" : {
    "from" : "0x0",
    "instrument_name": "ETH-PERP",
    "order_id": "3c52bdf8-814a-11ed-9866-0242ac130003" 
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
  from | true | string | | address of sender
 instrument_name| true | string | | Instrument name
 order_id | true | string | | the order id of the order to cancel

> An example of the response

```json
{
    "jsonrpc": "2.0",
    "result": {
        "order": {
            "from": "0x0",
            "instrument_name": "ETH-PERP",
            "order_id": "3c52bdf8-814a-11ed-9866-0242ac130003"
        }
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
  › order | object | Details of the order to be cancelled
  ›  › from | string | Address of the account
  ›  › instrument_name | string | Name of the instrument
  ›  › order_id | string | Order id of the order to be cancelled



<!-- ============================================================================================ -->


<!-- ## /private/cancel_all -->
<!-- ## /private/cancel_all_by_currency -->


<!-- ============================================================================================ -->


## /private/cancel_all_by_instrument


This method cancels all the open orders of a particular instrument

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "private/cancel_all_by_instrument",
  "params" : {
    "from": "0x0",
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
   from | true | string | | address of sender
 instrument_name| true | string | | Instrument name

> An example of the response

```json
{
    "jsonrpc": "2.0",
    "result": {
        "order": {
            "from": "0x0",
            "instrument_name": "ETH-PERP"
        },
        "messaage": "Cancelled all orders"
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
  › order | object | Details of the order to be cancelled
  ›  › from | string | Address of the account
  ›  › instrument_name | string | Name of the instrument
  › message | string | "Cancelled all orders if successful"


<!-- ============================================================================================ -->


<!-- ## /private/cancel_by_label
## /private/close_position
## /private/get_margins
## /private/get_mmp_config
## /private/get_open_orders_by_currencytransfer_by_id
## /private/cancel_withdrawal
## /private/create_deposit_address
## /private/get_current_deposit_address
## /private/get_deposits
## /private/get_transfers
## /private/get_withdrawals
## /private/submit_transfer_to_subaccount
<!-- ## /private/submit_trans -->


<!-- ============================================================================================= -->


## /private/get_open_orders_by_instrument


This method gives all the open orders

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "private/get_open_orders_by_instrument",
  "params" : {
    "from": "0x0",
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
   from | true | string | | address of sender
 instrument_name| true | string | | Instrument name


> An example of the response

```json
{
    "jsonrpc": "2.0",
    "result": {
        "d961995e-814d-11ed-9866-0242ac130003": {
            "order_id": "d961995e-814d-11ed-9866-0242ac130003",
            "time": 1671640687787109,
            "side": "buy",
            "size": 100,
            "time_in_force": "GTC",
            "price": 1000,
            "fromaddr": "0x0",
            "remainingToFill": 100,
            "class": "LimitOrder",
            "label": "",
            "is_liquidation": false,
            "initial_margin": 0.00200004
        }
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
  › order | object | Details of the 
  ›  › order_id | string | Order id of the order
  ›  › time | integer | Timestamp at which order was placed in (microdex)
  ›  › side | string | Order side (buy/sell)
  ›  › size | number | Size of the order.
  ›  › time_in_force | string | Specifies how long the order remains in effect.
  ›  › price | number | Price at which order was placed
  ›  › fromaddr | string | address of the account
  ›  › remainingToFill | number | Size of the order still to be filled.
  ›  › class | string | Order class
  ›  › label | string | Order label
  ›  › is_liquidation | bool | True if order placed by liquidation engine.
  ›  › initial_margin | number | Initial Margin of the order.  


<!-- =============================================================================================== -->

<!-- ## /private/get_order_history_by_currency
## /private/get_order_history_by_instrument
## /private/get_order_margin_by_ids
## /private/get_order_state
## /private/get_trigger_order_history
## /private/get_user_trades_by_currency
## /private/get_user_trades_by_currency_and_time
## /private/get_user_trades_by_instrument
## /private/get_user_trades_by_instrument_and_time
## /private/get_user_trades_by_order
## /private/reset_mmp
## /private/send_rfq
## /private/set_mmp_config
## /private/get_settlement_history_by_instrument
## /private/get_settlement_history_by_currency --> 
