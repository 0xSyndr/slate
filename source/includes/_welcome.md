
# Welcome

 Welcome to the Syndr API! 

# Overview

Syndr is building an institutional-grade options and futures exchange powered by zkProofs.  

You can access our API using JSON-RPC over websocket

Syndr's testing environment, [demo.trading.syndr.com](http://demo.trading.syndr.com) can be used to test our API.

Happy Trading!

## Naming


### Currency

Syndr's allowed currencies use the following system of naming:

/public/get_currencies method can be used to get all currencies.


Examples  | Comments|
--------- | --------|
BTC | Symbol of the ERC20 token



<br>

### Instruments

Syndr's tradeable assets or instruments use the following system of naming:

/public/get_instruments method can be used to get all instruments.


|Kind | Examples | Template | Comments|
|---- | -------- | -------- | --------|
|Future | `BTC-25MAR16`, `BTC-5AUG16`| BTC-DMMMYY | 	BTC is currency, DMMMYY` `is expiration date, D stands for day of month (1 or 2 digits), MMM - month (3 first letters in English), YY stands for year.
|Perpetual | `BTC-PERP` |  | Perpetual contract for currency BTC.|
|Option| 	`BTC-25MAR16-420-C`, `BTC-5AUG16-580-P` | BTC-DMMMYY-STRIKE-K | STRIKE is option strike price in USD. Template K is option kind: C for call options or P for put options.|



<br>

### Index

Syndr's instrument index use the following system of naming:

/public/get_index_price_names method can be used to get all index names.


|Kind | Examples|
|---- | -------- |
|Future | BTC/USDT |  




## Rate Limits

Coming soon.


# JSON-RPC


## Request Messages



According to the JSON-RPC sepcification the requests must be JSON objects with the following fields.

> An example of request message

```json
{
    "jsonrpc": "2.0",
    "id": 8066,
    "method": "public/ticker",
    "params": {
        // paramaters for the request message
    }
}
```

Name | Type | Description
 ----- | ------ | ------------ 
jsonrpc | string | The version of the JSON-RPC spec: "2.0"
id | 	integer or string | An identifier of the request. If it is included, then the response will contain the same identifier
method | string | The method to be invoked
params | object | 	The parameters values for the method. The field names must match with the expected parameter names. The parameters that are expected are described in the documentation for the methods, below.



## Response Messages

The JSON-RPC API always responds with a JSON object with the following fields.

> Response Message structure:

```json
{
    "jsonrpc": "2.0",
    "result": [],
    "id": 8066
}
```

Name | Type | Description
 ----- | ------ | ------------ 
jsonrpc | string | The JSON-RPC version (2.0).
id | integer | The id that was sent in the request.
result | any | The response of the message sent.
error | error object | Only present if there was an error invoking the method.

<br>

In case of an error the response message will contain the error field, with as value an object with the following with the following fields:


Name | Type | Description
 ----- | ------ | ------------ 
code | integer | A number that indicates the kind of error.
message	| string | A short description that indicates the kind of error.








<!-- ## Detailed response for private/cancel_all* and private/cancel_by_label methods -->

<!-- ## Security keys -->

<!-- ## Notifications -->

<!-- ## Authentication -->

<!-- ## Access scope -->

## JSON-RPC over websocket

Websocket is the prefered transport mechanism for the JSON-RPC API, because it is faster.  The code examples that can be found next to each of the methods show how websockets can be used from Python.


<!-- ## JSON-RPC over HTTP -->
