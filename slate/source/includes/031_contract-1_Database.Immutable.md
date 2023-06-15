## Database.Immutable

This solution simplifies interactions with blockchain networks, providing a seamless way to store data on a blockchain.

It abstracts the complexities of blockchain transactions and network fees, allowing users to focus solely on their data.

<p class="product-header">Solution</p>

"_An immutable object is an object whose state cannot be modified after it is created_"

Data saved using this solution cannot be changed.

<p class="product-author">Author</p>

<p class="s2">Blockchain Web Services</p>

<p class="product-title">Description</p>

You can use Database.Immutable solution to save immutable data to blockchain and certify written data will never change.

<p class="product-title">Networks</p>

<p class="product-network">Ethereum</p>

Click on Contract Address to check verified contract at `etherscan.io`.

| Network Id | Contract Address                                                                                                                   | Version |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------- | ------- |
| ethereum   | [0x58ca3f44cf5c84c1c29591a483be3288d0a01b7c](https://etherscan.io/address/0x58ca3f44cf5c84c1c29591a483be3288d0a01b7c)              | 2       |
| sepolia    | [0xEF28790d1C8ac0833e8c05BB4344e479Da8a4Dd3](https://sepolia.etherscan.io/address/0xEF28790d1C8ac0833e8c05BB4344e479Da8a4Dd3) | 2       |


<p class="product-network">Polygon</p>

Click on Contract Address to check verified contract at `polygonscan.com`.

| Network Id | Contract Address                                                                                                                   | Version |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------- | ------- |
| polygon   | [0x58ca3f44cF5c84C1C29591A483be3288D0A01b7C](https://polygonscan.com/address/0x58ca3f44cF5c84C1C29591A483be3288D0A01b7C)              | 2       |
| mumbai    | [0x58ca3f44cF5c84C1C29591A483be3288D0A01b7C](https://mumbai.polygonscan.com/address/0x58ca3f44cF5c84C1C29591A483be3288D0A01b7C) | 2       |


<p class="product-title">Operations</p>

<p class="product-operation ">insertBytes32</p>

> insertBytes32 operation call example.

```javascript
var parameters = {
  solution: "Database.Immutable",
  version: 2,
  network: "sepolia",
  operation: "insertBytes32",
  parameters: {
    key: "a-key",
    value: "Hello World!",
  },
};

$.ajax({
  method: "POST",
  url: "https://api.bws.ninja/v1/call",
  data: JSON.stringify(parameters),
  headers: {
    "Content-Type": "application/json",
    "X-Api-Key": "ExV0d92KzQ8QgsTVnevddpbB8cUaAfPs7ntVF8g0",
  },
  dataType: "json",
  success: function (response) {
    console.log(response);
  },
  error: function (xhr, textStatus, errorThrown) {
    console.log(xhr);
  },
});
```

> If successfull, the call will return the related Job Id to fetch for results.

```json
{
  "statusCode": 200,
  "info": {
    "jobId": "543433243"
  }
}
```

Saves up to 32 characters string value in Ethereum database (check [Passing Parameters](#passing-parameters) for other required parameters).

| Parameter  | Value                                                   |
| ---------- | ------------------------------------------------------- |
| solution   | Database.Immutable                                      |
| operation  | insertBytes32                                           |
| parameters | [check Parameters](#insertBytes32-operation-parameters) |

<a name="insertBytes32-operation-parameters"></a>

##### Parameters

The following operation parameters can be used to save a string you can later query by using the `key`value.

| Parameter | Type   | Value(s)             | Description                    |
| --------- | ------ | -------------------- | ------------------------------ |
| key       | string | 32 characters string | The key for data to save.      |
| value     | string | 32 characters string | The value to save on database. |

###### Response

The operation call will return the `jobId` of the job running on Blochchain Web Services to execute your command (remember blockchain operations are asynchronous and can take a while to finish).

`{ "statusCode": 200, "info": { "jobId": "543433243" } }`

<p class="product-operation ">selectBytes32</p>

> selectBytes32 operation parameters call example.

```javascript
var parameters = {
  solution: "Database.Immutable",
  version: 2,
  network: "sepolia",
  operation: "selectBytes32",
  parameters: {
    key: "a-key",
  },
};

...

```

Gets a value you previously stored on Ethereum using `insertBytes32` (check [Passing Parameters](#passing-parameters) for other required parameters).

| Parameter  | Value                                                   |
| ---------- | ------------------------------------------------------- |
| solution   | Database.Immutable                                      |
| operation  | selectBytes32                                           |
| parameters | [check Parameters](#selectBytes32-operation-parameters) |

##### Parameters

Set the `key` value to get the data you previously saved.

| Parameter | Type   | Value(s)             | Description               |
| --------- | ------ | -------------------- | ------------------------- |
| key       | string | 32 characters string | The key for data to save. |

###### Response

The operation call will return the `jobId` of the job running on Blochchain Web Services to execute your command (remember blockchain operations are asynchronous and can take a while to finish).

`{ "statusCode": 200, "info": { "jobId": "543433243" } }`

<a name="insertString-operation"></a>

<p class="product-operation ">insertString</p>

> insertString operation parameters call example.

```javascript
var parameters = {
  solution: "Database.Immutable",
  version: 2,
  network: "sepolia",
  operation: "insertString",
  parameters: {
    key: "a-key",
    value: "Hello World!",
  },
};

...

```

Saves a string value in Ethereum database.

| Parameter  | Value                                                  |
| ---------- | ------------------------------------------------------ |
| solution   | Database.Immutable                                     |
| operation  | insertBytes32                                          |
| parameters | [check Parameters](#insertString-operation-parameters) |

Check [Passing Parameters](#passing-parameters) for other required parameters.

##### Parameters

The following operation parameters can be used to save a string you can later query by using the `key`value.

| Parameter | Type   | Description                    |
| --------- | ------ | ------------------------------ |
| key       | string | The key for data to save.      |
| value     | string | The value to save on database. |

###### Response

The operation call will return the `jobId` of the job running on Blochchain Web Services to execute your command (remember blockchain operations are asynchronous and can take a while to finish).

`{ "statusCode": 200, "info": { "jobId": "5434323243" } }`

<a name="selectString-operation"></a>

<p class="product-operation ">selectString</p>

> selectString operation parameters call example.

```javascript
var parameters = {
  solution: "Database.Immutable",
  version: 2,
  network: "sepolia",
  operation: "selectString",
  parameters: {
    key: "a-key",
  },
};

...

```

Gets a value you previously stored on Ethereum using `insertString`.

| Parameter  | Value                                                  |
| ---------- | ------------------------------------------------------ |
| solution   | Database.Immutable                                     |
| operation  | selectString                                           |
| parameters | [check Parameters](#selectString-operation-parameters) |

Check [Passing Parameters](#passing-parameters) for other required parameters.

##### Parameters

Set the `key` value to get the data you previously saved.

| Parameter | Type   | Description               |
| --------- | ------ | ------------------------- |
| key       | string | The key for data to save. |

###### Response

The operation call will return the `jobId` of the job running on Blochchain Web Services to execute your command (remember blockchain operations are asynchronous and can take a while to finish).

`{ "statusCode": 200, "info": { "jobId": "5423433243" } }`

<br/><br/>
<span class="login-text">Login to your BWS account and test this solution using Postman.<span>
<br/><br/>
<span class="button button-small">
<a href="https://prod.bws.ninja/front-sign-in.html">Log In</a>
</span>