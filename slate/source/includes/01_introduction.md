# How It Works

## Registration

To start using Blockchain Web Services go to [bws.ninja](https://bws.ninja) and sign-up. It's free.

## API Endpoint

```javascript
$.ajax({
    method: 'POST',
    url: 'https://api.bws.ninja/v1/call',
   ...
  });
```

Blockchain Web Services API baseline endpoint is **api.bws.ninja** and current version is **v1**.

As an example, API operation **call** will use the following URL:

`https://api.bws.ninja/v1/call`

## Authentication

```javascript
$.ajax({
   	...
    headers: {
      'Content-Type': 'application/json',
      'X-Api-Key': 'my-api-key'
    },
   	...
  });
```

Calling [Blockchain Web Services](https://bws.ninja) smart contracts requires a personal **API Key** to authenticate. To get your key, sign in at [bws.ninja](https://bws.ninja) and go to `My Account > API Key`.

<br/>
![BWS Credits](images/BlockchainWebServices-API_Key.jpg)

You must include your Key in all of your API calls as a header attribute:

`'X-Api-Key': 'my-api-key'`

## Main API Methods

Use [‘call’](#call-operation) to run a Smart Contract operation and ['fetch’](#fetch-operation) to get Smart Contract call status (Smart Contracts execution can take a while to get confirmed from the Blockchain).

"_A smart contract is a computer program or a transaction protocol which is intended to automatically execute, control or document legally relevant events and actions according to the terms of a contract or an agreement._" The [Wikipedia](https://en.wikipedia.org/wiki/Smart_contract).

<a name="call-operation"></a>

### 'call' API Method

> API call example.

```javascript
var parameters = {
  "contractId": "Ethereum.Database.Immutable",
  "parameters": {
    ...
  }
};

$.ajax({
  method: 'POST',
  url: 'https://api.bws.ninja/v1/call',
  dataType: 'json',
  data: JSON.stringify(parameters),
  headers: {
    'Content-Type': 'application/json',
    'X-Api-Key': 'ExV0d92KzQ8QgsTVnevddpbB8cUaAfPs7ntVF8g0'
  },
  ...
  });

```

> API call response example

```json
{
  "statusCode": 200,
  "info": {
    "jobId": "543433243"
  }
}
```

`https://api.bws.ninja/v1/call` runs a [Blockchain Web Services](https://bws.ninja) Smart Contract and must contain the following parameters:

| Parameter  | Type   | Value(s)                                  | Description                        |
| ---------- | ------ | ----------------------------------------- | ---------------------------------- |
| contract   | string | check [Smart Contracts](#smart-contracts) | The contract id.                   |
| version    | number | 1,2,3,...                                 | The contract version to use.       |
| network    | string | ropsten, ethereum                         | The network id to save data to.    |
| operation  | string | check [Smart Contracts](#smart-contracts) | The operation id to call.          |
| parameters | json   | check [Smart Contracts](#smart-contracts) | The operation required parameters. |

Please note:

- The `contract`, `operation` and `parameters` attributes are used to call any of the Blockchain Web Services available [Smart Contracts](#smart-contracts).

- `version` is used to call a specific Smart Contract implementation.

- `network` is the network you want to use (e.g. `ropsten` network can be used to test without requiring any funds).

- Method parameters must be passed in the Body part of the POST request message using [JSON](https://en.wikipedia.org/wiki/JSON) format (`Content-Type` header attribute must be set to `application/json`)

#### 'call' Response

API call response includes the 'jobId' to use to get Smart Contract results.

`{ "jobId": "aacee908-3a85-4966-945c-ab8f09ebabf9" }`

Check the [response](#api-calls-response) object you get when calling Blockchain Web Services API.

<a name="fetch-operation"></a>

### 'fetch' API Method

> API call example.

```javascript
var parameters = {
  "jobId": "b064cc6b-f394-4ca4-9c51-be506e4cc59d",
};

$.ajax({
  method: 'POST',
  url: 'https://api.bws.ninja/v1/fetch',
  dataType: 'json',
  data: JSON.stringify(parameters),
  headers: {
    'Content-Type': 'application/json',
    'X-Api-Key': 'ExV0d92KzQ8QgsTVnevddpbB8cUaAfPs7ntVF8g0'
  },
  ...
  });

```

> Fetch API call response example

```json
{
    "statusCode": 200,
    "statusMessage": "",
    "info": {
        "Status":{ "Value":"registered"},
        "TimestampInMillis":1674504952,
        "Request": {
            "contract": "Ethereum.Database.Immutable ",
            "version": 1,
            "network": "ropsten",
            "operation": "insertBytes32",
            "parameters": {
                "key": "a-key",
                "value": "Hello World!"
            },
            "Guid":"b064cc6b-f394-4ca4-9c51-be506e4cc59d"
        }
}
```

Use `https://api.bws.ninja/v1/fetch` to get a previously started Smart Contract call, indicating the `jobId` you get when running the [‘call’](#call-operation):

| Parameter | Type   | Value(s)                                        |
| --------- | ------ | ----------------------------------------------- |
| jobId     | string | The jobId you get when running a Smart Contract |

#### 'fetch' Results

The **fetch** API method will return the status of your Smart Contract call as part of the info parameter:

| Parameter         | Description                                             |
| ----------------- | ------------------------------------------------------- |
| Status            | The current status of Smart Contract execution          |
| TimestampInMillis | The status timestamp in milliseconds                    |
| Request           | The original request you did to call the Smart Contract |
| Result            | When Status is 'completed' the smart contract results   |
| Receipt           | The outcome of interaction with Ethereum Blockchain     |

##### 'fetch' Status List

A Blockchain Web Services Smart Contract call status can be:

| Status     | Description                                         |
| ---------- | --------------------------------------------------- |
| registered | The job has correctly been registered for execution |
| running    | The transaction is running on Blockchain Network    |
| completed  | Smart Contract call has completed                   |
| failed     | Smart Contract execution has failed                 |

## API Calls Response

> API success call response example

```json
{
  "statusCode": 200,
  "info": {
    "jobId": "543433243"
  }
}
```

> API call error response example

```json
{
  "statusCode": 404,
  "statusMessage": "incorrect parameters"
}
```

When calling the API, you can get an [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) layer [transport error](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes), that is, an error that has ocurried before the related API code is executed (e.g. 503, Service Unavailable), or a _controlled error_, meaning an error that is related to the parameters values you send (e.g. 404, not found - when no data is found for your query).

When no transport layer error is detected, all the API calls will include the next message in the BODY part of the response:

| Parameter     | Type   | Description                                             |
| ------------- | ------ | ------------------------------------------------------- |
| statusCode    | number | The api call result code (e.g. 200 indicates no error). |
| statusMessage | string | The status code related message.                        |
| info          | object | The requested information                               |

### Error Status Codes

The Blockchain Web Services API uses the following error Status Codes:

| Status Code | Meaning                                                                                     |
| ----------- | ------------------------------------------------------------------------------------------- |
| 400         | Bad Request -- Check your request parameters.                                               |
| 401         | Unauthorized -- Check your API key                                                          |
| 403         | Forbidden / Too Many Requests -- Slow down!                                                 |
| 404         | Not Found -- Your API key is valid but there is no related user on our servers.             |
| 405         | Method Not Allowed -- You tried to access with an invalid method                            |
| 406         | Not Acceptable -- You requested a format that isn't json                                    |
| 410         | Gone -- The requested object has been removed                                               |
| 418         | I'm a teapot                                                                                |
| 429         | Too Many Requests -- Slow down!                                                             |
| 500         | Internal Server Error -- We had a problem with our server. Try again later.                 |
| 503         | Service Unavailable -- We're temporarially offline for maintanance. Please try again later. |

## Transactions Overview

Go to [Blockchain Web Services](https://bws.ninja) Management Console and select `Jobs List` menu option to get the list of executed calls.

![Megalock.ninja](images/megalock-snap-11.png)

For each of the service API calls you execute, select `actions` menu option to check for the status or the available related information.

![Megalock.ninja](images/megalock-snap-12.png)

## Required Funds

[Blockchain Web Services](https://bws.ninja) is free, but calling Smart Contracts requires funds: "It is the fuel that allows it to operate" (you can check how Gas and Fuel works for Ethereum [here](https://ethereum.org/en/developers/docs/gas/)).

<aside class="notice">
We use Stripe as the Payment gateway for buying credits.
</aside>

To get your account funded go to `My Account > Credits` and complete your credits purchase.

<br/>
![BWS Credits](images/BlockchainWebServices-Credits.jpg)

Remember **[Blockchain Web Services](https://bws.ninja) is free** and funds are spent when calling smart contracts.
