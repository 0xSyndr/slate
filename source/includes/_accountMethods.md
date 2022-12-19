
# Account Management

<!-- ======================================================================================== -->

## /private/get_if_account_at_risk


This method gives a bool result whether the position is at liquidation risk.
This requires authentication.

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "private/get_if_account_at_risk",
  "params" : {
    "from": "0x0"
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

 
> An example of the response 

<!-- ```jspn
{
  "jsonrpc": "2.0",
  "result": {
    "status": "success", 
    "resp": {
      "jsonrpc": "2.0", 
      "result": {
        "req_id": 6953, 
        "result": false}
        , "id": 1
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


<!-- ======================================================================================= -->


<!-- ## /public/get_announcements
## /public/get_portfolio_margins
## /private/change_api_key_name
## /private/change_scope_in_api_key
## /private/change_subaccount_name
## /private/create_api_key
## /private/create_subaccount
## /private/disable_api_key
## /private/enable_affiliate_program
## /private/enable_api_key
<!-- ## /private/get_access_log -->

<!-- ============================================================================================ -->

## /private/get_account_summary


This method give the account summary for the given currency

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "private/get_account_summary",
  "params" : {
    "from": "0x0",
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

`Parameter` | `Required` | `Type` | `Enum` | `Description`
 ---------- | ---------- | ------ | ------ | ------------
   from | true | string | address of sender
 currency| true | string | Currency name

 > An example of the response

<!-- ```json
 "TO FIX"
``` -->


### Response

<!-- `Name` | `Type` | `Description`
 ----- | ------ | ------------ 
`id` | `integer` | `The id that was sent in the request`
`jsonrpc` | `string` | `The JSON-RPC version (2.0)`
`result` | `----` | `----` -->


<!-- ## /private/get_affiliate_program_info
## /private/get_email_language
## /private/get_new_announcements
## /private/get_portfolio_margins -->
<!-- ## /private/get_position -->




<!-- ========================================================================================= -->

## /private/get_positions


This method gives all open positions of the user.

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "private/get_positions",
  "params" : {
    "from" : "0x0"
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


> An example of the response

<!-- ```json
{
    "jsonrpc": "2.0",
    "result": {
        "status": "success",
        "resp": {
            "jsonrpc": "2.0",
            "result": {
                "req_id": 3114,
                "result": {
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


<!-- ========================================================================================== -->


<!-- ## /private/get_subaccounts
## /private/get_subaccounts_details
## /private/get_transaction_log
## /private/get_user_locks
## /private/list_api_keys
## /private/remove_api_key
## /private/remove_subaccount
## /private/reset_api_key
## /private/set_announcement_as_read
## /private/set_api_key_as_default
## /private/set_email_for_subaccount
## /private/set_email_language
## /private/set_password_for_subaccount
## /private/toggle_notifications_from_subaccount
## /private/toggle_portfolio_margining
## /private/toggle_subaccount_login --> 
