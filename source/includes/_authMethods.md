

# Authentication 

## /private/auth


This method is used to Authenticate the account

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 7365,
  "method" : "private/auth",
  "params" : {
    "from": "0x71C7656EC7ab88b098defB751B7401B5f6d8976F"
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
 ---------- | ---------- | ------ | ------ | ------------|
from | true | string | | address of the user

> An example of the response

<!-- ```json
{
    "jsonrpc": "2.0",
    "result": {
        "status": "Done"
    },
    "id": 7365
}
``` -->


### Response

<!-- Name | Type | Description
 ----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0)
id | integer | The id that was sent in the request
result | string | tells the status of authentication  -->

<!-- ## /public/exchange_token -->
<!-- ## /public/fork_token -->
<!-- ## /private/logout  -->