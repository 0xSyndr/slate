
# Wallet

<!-- ======================================================================================================================= -->

## private/deposit

TO FIX

This method is used to deposit collateral into your margin account.

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "private/deposit",
  "params" : {
    "fix"
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

<!-- ### Parameters

Parameter | Required | Type | Enum | Description
 ---------- | ---------- | ------ | ------ | ------------|
from | true | string | | address of the user
currency | true | string | currency to be deposited
amount | true | integer | amount to be deposited  -->

> An example of the response

```json
{
  "To Fix"
}
```


<!-- ### Response

Name | Type | Description
 ----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0)
id | integer | The id that was sent in the request
result | object | 
> amount | integer | new collateral added
> balance | integer | new balance of the currency
> currency | string | currency collateral is deposited to
> timestamp | integer | deposited timestamp
> status | string | tells the status of the transaction -->


<!-- ========================================================================================================================== -->

<!-- ## /private/cancel_transfer_by_id
## /private/cancel_withdrawal
## /private/create_deposit_address
## /private/get_current_deposit_address
## /private/get_deposits
## /private/get_transfers
## /private/get_withdrawals
## /private/submit_transfer_to_subaccount
## /private/submit_transfer_to_user -->

<!-- ======================================================================================================================== -->

## /private/withdraw

TO FIX


This method allows to withdraw from account to wallet

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "private/withdraw",
  "params" : {
    "fix"
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

<!-- ### Parameters

`Parameter` | `Required` | `Type` | `Enum` | `Description`
 ---------- | ---------- | ------ | ------ | ------------ -->

> An example of the response

```json
  "To Fix"
```

<!-- ### Response

`Name` | `Type` | `Description`
 ----- | ------ | ------------ 
`id` | `integer` | `The id that was sent in the request`
`jsonrpc` | `string` | `The JSON-RPC version (2.0)`
`result` | `----` | `----` -->


<!-- =========================================================================================== -->
