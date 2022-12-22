
# Subscription

## /public/subscribe

Can be used to subscribe to one or more channels.

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 3041,
  "method" : "public/subscribe",
  "params" : {
    "channels": ["ticker.ETH-PERP"]
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
channels | true | array | | channels to subscribe


> An example of the response

```json
{
  "jsonrpc": "2.0",
  "id": 3041,
  "result": [
    
  ]
}
``````json
{
  "jsonrpc": "2.0",
  "id": 3041,
  "result": [
    
  ]
}
```


### Response

`Name` | `Type` | `Description`
 ----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0).
id | integer | The id that was sent in the request.
result | array | array of string.



## /private/subscribe

Can be used to subscribe to one or more channels. Subscribing to private channels requires authentication.

```python
import asyncio
import websockets
import json

msg = \
{
  "jsonrpc" : "2.0",
  "id" : 3679,
  "method" : "private/subscribe",
  "params" : {
    "channels": ["user.orders.ETH-PERP"]
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
channels | true | array | | channels to subscribe


> An example of the response

```json
{
  "jsonrpc": "2.0",
  "id": 3041,
  "result": [
    
  ]
}
```


### Response

`Name` | `Type` | `Description`
 ----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0).
id | integer | The id that was sent in the request.
result | array | array of string.

