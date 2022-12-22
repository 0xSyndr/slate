
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

```jspn
{
    "jsonrpc": "2.0",
    "result": false,
    "id": 7365
}
```


### Response

`Name` | `Type` | `Description`
 ----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0).
id | integer | The id that was sent in the request.
result | bool | True if account at risk of liquidation

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

```json
 {
    "jsonrpc": "2.0",
    "result": {
        "total_pl": 0.0,
        "session_upl": 0,
        "session_rpl": 0,
        "projected_maintenance_margin": 0,
        "projected_initial_margin": 0,
        "projected_delta_total": 0,
        "portfolio_margining_enabled": true,
        "options_vega": 0,
        "options_value": 0,
        "options_theta": 0,
        "options_session_upl": 0,
        "options_session_rpl": 0,
        "options_pl": 0,
        "options_gamma": 0,
        "options_delta": 0,
        "margin_balance": 0,
        "maintenance_margin": 0.0,
        "initial_margin": 0.0,
        "futures_session_upl": 0,
        "futures_session_rpl": 0,
        "futures_pl": 0.0,
        "fee_balance": 0,
        "equity": 1000000000.0,
        "delta_total_map": {
            "eth_usd": 0
        },
        "delta_total": 0,
        "currency": "ETH",
        "balance": 1000000000.0,
        "available_withdrawal_funds": 1000000000.0,
        "available_funds": 1000000000.0
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
  › total_pl | number | Profit and loss 
  › session_upl | number | Session unrealized profit and loss 
  › session_rpl | number | Session realized profit and loss
  › projected_maintenance_margin | number | Projected maintenance margin of the account
  › projected_initial_margin | number | Projected initial margin of the account
  › projected_delta_total | number | The sum of position deltas 
  › portfolio_margining_enabled | bool | True if portfolio margin is enabled 
  › options_vega | number | Options summary vega
  › options_value | number | Options value
  › options_session_upl | number | Options session unrealized profit and Loss
  › options_session_rpl | number | Options session realized profit and Loss
  › options_pl | number | Options profit and Loss
  › options_gamma | number | Options summary gamma
  › options_delta | number | Options summary delta
  › margin_balance | number | The margin balance of the account
  › maintenance_margin | number | The maintenance margin
  › futures_session_upl | number | Futures session unrealized profit and Loss
  › futures_session_rpl | number | Futures session realized profit and Loss
  › futures_pl | number | Futures profit and Loss
  › fee_balance | number | The account's fee balance
  › equity | number | The account's current equity
  › delta_total_map | object | Total delta of different positions
  › delta_total | number | The sum of position deltas
  › balance | number | The account's balance
  › available_withdrawal_funds | number | Total available withdrawal funds 
  › available_funds | number | Total available funds of the account


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

```jspn
{
    "jsonrpc": "2.0",
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
  › Currency name | object
  › ›  option | object | list of option positions for that currency
  › ›  future | object | list of future positions for that currency 



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
