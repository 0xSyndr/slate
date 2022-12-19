

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
    "price" : 1000
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
 from | true | string | address of sender
 instrument_name| true | string | Instrument name
amount | true | number | It represents the requested order size. For perpetual and futures the amount is in USD units, for options it is amount of corresponding cryptocurrency contracts, e.g., BTC or ETH
type | false | string | `limit` , `market` | The order type, default: `"limit"`
label | false | string | user defined label for the order
price | false | number | The order price in base currency (Only for limit) 

> An example of the response

<!-- ```json
{
    "jsonrpc": "2.0",
    "result": {
        "status": "success",
        "resp": {
            "jsonrpc": "2.0",
            "result": {
                "req_id": 4007,
                "result": {
                    "order": {
                        "type": "limit",
                        "from": "0x0",
                        "instrument_name": "ETH-PERP",
                        "amount": 100,
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

<!-- `Name` | `Type` | `Description`
 ----- | ------ | ------------ 
`id` | `integer` | `The id that was sent in the request`
`jsonrpc` | `string` | `The JSON-RPC version (2.0)`
`result` | `----` | `----` -->


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
    "price" : 1000
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
 from | true | string | address of sender
 instrument_name| true | string | Instrument name
amount | true | number | It represents the requested order size. For perpetual and futures the amount is in USD units, for options it is amount of corresponding cryptocurrency contracts, e.g., BTC or ETH
type | false | string | `limit` , `market` | The order type, default: `"limit"`
label | false | string | user defined label for the order
price | false | number | The order price in base currency (Only for limit) 

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

<!-- `Name` | `Type` | `Description`
 ----- | ------ | ------------ 
`id` | `integer` | `The id that was sent in the request`
`jsonrpc` | `string` | `The JSON-RPC version (2.0)`
`result` | `----` | `----` -->


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
    "instrument_name": "ETH",
    "order_id": 87346 
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
  from | true | string | address of sender
 instrument_name| true | string | Instrument name
 order_id | true | integer | the order id of the order to cancel

> An example of the response

<!-- ```json
"To Fix"
``` -->

### Response

<!-- `Name` | `Type` | `Description`
 ----- | ------ | ------------ 
`id` | `integer` | `The id that was sent in the request`
`jsonrpc` | `string` | `The JSON-RPC version (2.0)`
`result` | `----` | `----` -->


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
    "instrument_name": "ETH"
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
   from | true | string | address of sender
 instrument_name| true | string | Instrument name

> An example of the response

<!-- ```json
"To Fix"
``` -->

### Response

<!-- `Name` | `Type` | `Description`
 ----- | ------ | ------------ 
`id` | `integer` | `The id that was sent in the request`
`jsonrpc` | `string` | `The JSON-RPC version (2.0)`
`result` | `----` | `----` -->


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
    "instrument_name": "ETH"
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
   from | true | string | address of sender
 instrument_name| true | string | Instrument name


> An example of the response

<!-- ```json
"To Fix"
``` -->

### Response

<!-- `Name` | `Type` | `Description`
 ----- | ------ | ------------ 
`id` | `integer` | `The id that was sent in the request`
`jsonrpc` | `string` | `The JSON-RPC version (2.0)`
`result` | `----` | `----` -->


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
