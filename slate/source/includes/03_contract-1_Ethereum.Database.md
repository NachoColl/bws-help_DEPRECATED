<style>
  .product-header {
    background-color:#5abaf0;
    color: white;
    text-shadow: none !important;
     margin-top:25px !important;
  }

  .product-author {
    background-color:#159957;
    opacity: .8;
    color: white;
    text-shadow: none !important;
     margin-top:25px !important;
  }

  .product-title {
    background-color:#292929;
    color :white;
    text-shadow: none !important;
    margin-top:25px !important;
  }

   .product-operation {
    background-color:#EC712B;
    color :white;
    text-shadow: none !important;
    width: 200px;
    margin-top:25px !important;
  }
</style>
## BWS Database

A Blockchain is essentially a distributed database that runs on a peer-to-peer network. You can use [Blockchain Web Services](https://bws.ninja) to insert or select data to/from Blockchain(s) using the following services:

- [Ethereum.Database.Immutable](#ethereum-database-immutable)
- [Ethereum.Database.Mutable](#ethereum-database-mutable)

Check the documentation provided by the Author to call those services.

<a name="ethereum-database-immutable"></a>

<p class="product-header">Service</p>

<h3 style="margin-top:0">Ethereum.Database.Immutable</h3>

"_An immutable object is an object whose state cannot be modified after it is created_"

<p class="product-author">Author</p>

<p class="s2">Blockchain Web Services</p>

<p class="product-title">Description</p>

You can use Ethereum.Database.Immutable operation to save immutable data to blockchain and certify written data will never change.

<p class="product-title">Contract</p>

Click on Contract Address to check verified contract at `etherscan.io`.

| Network Id | Contract Address                                                                                                                   | Version |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------- | ------- |
| ethereum   | [0x58ca3f44cf5c84c1c29591a483be3288d0a01b7c](https://etherscan.io/address/0x58ca3f44cf5c84c1c29591a483be3288d0a01b7c)              | 2       |
| ropsten    | [0x81D575b53239BcB4332bb1608a21F1A17035deeA](https://ropsten.etherscan.io/address/0x81D575b53239BcB4332bb1608a21F1A17035deeA#code) | 2       |

<p class="product-title">Operations</p>

<p class="product-operation ">insertBytes32</p>

> insertBytes32 operation call example.

```javascript
var parameters = {
  contract: "Ethereum.Database.Immutable",
  version: 2,
  network: "ropsten",
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
| contract   | Ethereum.Database.Immutable                             |
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
  contract: "Ethereum.Database.Immutable",
  version: 2,
  network: "ropsten",
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
| contract   | Ethereum.Database.Immutable                             |
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
  contract: "Ethereum.Database.Immutable",
  version: 2,
  network: "ropsten",
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
| contract   | Ethereum.Database.Immutable                            |
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
  contract: "Ethereum.Database.Immutable",
  version: 2,
  network: "ropsten",
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
| contract   | Ethereum.Database.Immutable                            |
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

<a name="ethereum-database-mutable"></a>

<p class="product-header">Service</p>

<h3 style="margin-top:0">Ethereum.Database.Mutable</h3>

"_This is in contrast to a mutable object (changeable object), which can be modified after it is created._"

> Mutable insertString operation parameters call example.

```javascript
var parameters = {
  contract: "Ethereum.Database.Mutable",
  version: 1,
  network: "ropsten",
  operation: "insertString",
  parameters: {
    key: "a-key",
    value: "Hello World!",
  },
};
```

<p class="product-author">Author</p>

<p class="s2">Blockchain Web Services</p>

<p class="product-title">Description</p>

Mutable insert operations can overwrite previously saved data and the same insert/select operations are available for `Ethereum.Database.Mutable` contract (you just need to replace `contract` and `version` parameter to use Mutable or Immutable contract).

<p class="product-title">Contract</p>

Click on Contract Address to check verified contract at `etherscan.io`.

| Network Id | Contract Address                                                                                                                   | Version |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------- | ------- |
| ethereum   | [0x1aFEe6DD9A1D4af90c39CD8B09296FC505beA00d](https://etherscan.io/address/0x1aFEe6DD9A1D4af90c39CD8B09296FC505beA00d)              | 1       |
| ropsten    | [0x9089Db83F0590EC2eD01A5Eb4F8584Dd6F4bDaC7](https://ropsten.etherscan.io/address/0x9089Db83F0590EC2eD01A5Eb4F8584Dd6F4bDaC7#code) | 1       |

<p class="product-title">Operations</p>

You can use the same operations as for `Ethereum.Database.Immuutable` service, changing the parameter contract to `Ethereum.Database.Mutable`.
