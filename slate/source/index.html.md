---
title: Blockchain Web Services Help

language_tabs:
 - javascript


toc_footers:
  - <a href='https://bweb.services'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/NachoColl/bws-help/issues' target="_blank">Need help? click here</a>

includes:
  - errors

search: false
---

# Introduction

Welcome to [Blockchain Web Services](https://bweb.services) API documentation! An API you can use to call Blockchain Smart Contracts.

## Required Funds (Credits)

To call Smart Contracts ...
## API Call Results

> "Hello world!" small contract call example.

```javascript
var parameters = {
  "...": {
    "...": "..."
  }
};

```

When you call [Blockchain Web Services](https://bweb.services) API to ...

<aside class="warning">
....
</aside>

We recommend that you start testing the API by using [Postman](https://www.getpostman.com/). Check Javascript code examples included on this page.

## Account Dashboard

As part of [Blockchain Web Services](https://bweb.services)  you also get ...

<aside class="notice">
....
</aside>


# API Endpoints

[Blockchain Web Services](https://bweb.services) API uses the next endpoint:

`https://api.bweb.services/`

<aside class="notice">
...
</aside>

# Authentication

```javascript
$.ajax({
    method: 'POST',
  	...
    headers: {
      'Content-Type': 'application/json',
      'X-Api-Key': 'my-api-key'
    },
   	...
  });
```

[Blockchain Web Services](https://bweb.services) API requires a personal **API Key** to authenticate your calls (to get such key, just sign in at [bweb.services](https://bweb.services).

Once you get your API Key, you must include it in all of your API calls as a header attribute:

`'X-Api-Key': 'my-api-key'`

<aside class="notice">
You must replace <code>my-api-key</code> with your personal API key.
</aside>

# Passing parameters

Method call parameters must be passed in the Body part of the request message using [JSON](https://en.wikipedia.org/wiki/JSON) format.

The `Content-Type` header attribute must be set to `application/json`.

```javascript

// How to set API Call parameters

{
	
	...
	
	"date" : "1482932562"
	
	...
	
	"total" : 19.99
	
	...
	
}
```

# API Calls Response

> API call `seller/get` response example


```
{
 "statusCode":200,
 "statusMessage":"",
 "info":  "{
    \"jobId\":\"543433243\"
  }"
}
```

> API call error response example


```
{
 "statusCode":404,
 "statusMessage":"incorrect parameters",
 "info":  ""
}
```


When calling the API, you can get an [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) layer transport error, that is, an error that has ocurried before the related API code is executed (e.g. 503, Service Unavailable), or a *controlled error*, meaning an error that is related to the parameters values you send (e.g. 404, not found - when no data is found for your query). By using this strategy, you will be able to catch and differentiate all kind of API call errors easily.

<br/>
When no transport layer error is detected, all the API calls will include the next message in the BODY part of the response:


Parameter | Type | Description 
--------- | -------  | ----------- 
statusCode | number | The api call result code, using [HTTP status codes values](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) (e.g. 200 indicates no error).
statusMessage | string | The status code related message.
info | string* | The related requested information.
<br/><br/>
Please take note that the info result parameter may be just a simple text or a more complex json schema (check the examples on the right).


# Smart Contracts API

## <span style="color:green">call</span>

> Call a Smart Contract.

```javascript
var parameters = {
    "...": "..."
}

$.ajax({
    method: 'POST',
    url: 'https://api.bweb.services/call',
    data: JSON.stringify(sellerJson),
    headers: {
      'Content-Type': 'application/json',
      'X-Api-Key': 'ExV0d92KzQ8QgsTVnevddpbB8cUaAfPs7ntVF8g0'
    },
    dataType: 'json',
    success: function (response) {
      console.log(response); 
    },
    error: function (xhr, textStatus, errorThrown) {
      console.log(xhr);
    }
  });
```

> If successfull, the call will return the related Job Id to fetch for results.

Use this method to call a Smart Contract.

<aside class="notice">
...
</aside>

### HTTP Request

`POST https://api.bweb.services/call`

### Request Parameters

Parameter | Type | Description | Notes
--------- | -------  | ----------- | -------
networkId | string | The Blockchain network you want to use | check the list of available networks.