## Ethereum.Database.Immutable

This contract is used for [immutable](https://en.wikipedia.org/wiki/Immutable_object) Ethereum database operations.

"_An immutable object is an object whose state cannot be modified after it is created_"

### Contract Address

You can check Blockchain Web Services contract at the following addresses (to verify click on the contract address link).

| Network Id | Contract Address                                                                                                              |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------- |
| ethereum   |
| ropsten    | [0x81D575b53239BcB4332bb1608a21F1A17035deeA](https://ropsten.etherscan.io/address/0x81D575b53239BcB4332bb1608a21F1A17035deeA) |

### Operations

Use the following operations to save (and get) data to Ethereum [blockchain](https://en.wikipedia.org/wiki/Blockchain) [distributed ledger](https://en.wikipedia.org/wiki/Distributed_ledger) database.

<aside class="notice">
Data you save using those operations will stay on Ethereum database "for ever" :).
</aside>

#### :: insertBytes32

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
  url: "https://api.bweb.services/v1/call",
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

Saves up to 32 characters string value in Ethereum database.

##### insertBytes32 Request Parameters

Use the following parameters to call `insertBytes32` operation:

| Parameter  | Value                                                                     |
| ---------- | ------------------------------------------------------------------------- |
| contract   | Ethereum.Database.Immutable                                               |
| operation  | insertBytes32                                                             |
| parameters | [insertBytes32 Operation Parameters](#insertBytes32-operation-parameters) |

Check [Passing Parameters](#passing-parameters) for other required parameters.

###### insertBytes32 Operation Parameters

The following operation parameters can be used to save a string you can later query by using the `key`value.

| Parameter | Type   | Value(s)             | Description                    |
| --------- | ------ | -------------------- | ------------------------------ |
| key       | string | 32 characters string | The key for data to save.      |
| value     | string | 32 characters string | The value to save on database. |

##### insertBytes32 Response

The operation call will return the `jobId` of the job running on Blochchain Web Services to execute your command (remember blockchain operations are asynchronous and can take a while to finish).

#### :: selectBytes32

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

$.ajax({
  method: "POST",
  url: "https://api.bweb.services/v1/call",
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

Gets a value you previously stored on Ethereum database by calling `insertBytes32`.

##### selectBytes32 Request Parameters

Use the following parameters to call `selectBytes32` operation:

| Parameter  | Value                                                                     |
| ---------- | ------------------------------------------------------------------------- |
| contract   | Ethereum.Database.Immutable                                               |
| operation  | selectBytes32                                                             |
| parameters | [selectBytes32 Operation Parameters](#selectBytes32-operation-parameters) |

Check [Passing Parameters](#passing-parameters) for other required parameters.

###### selectBytes32 Operation Parameters

Set the `key` value to get the data you previously saved.

| Parameter | Type   | Value(s)             | Description               |
| --------- | ------ | -------------------- | ------------------------- |
| key       | string | 32 characters string | The key for data to save. |

##### selectBytes32 Response

The operation call will return the `jobId` of the job running on Blochchain Web Services to execute your command (remember blockchain operations are asynchronous and can take a while to finish).

#### :: insertString

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

$.ajax({
  method: "POST",
  url: "https://api.bweb.services/v1/call",
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

Saves a string value in Ethereum database.

##### insertString Request Parameters

Use the following parameters to call `insertString` operation:

| Parameter  | Value                                                                   |
| ---------- | ----------------------------------------------------------------------- |
| contract   | Ethereum.Database.Immutable                                             |
| operation  | insertBytes32                                                           |
| parameters | [insertString Operation Parameters](#insertString-operation-parameters) |

Check [Passing Parameters](#passing-parameters) for other required parameters.

###### insertString Operation Parameters

The following operation parameters can be used to save a string you can later query by using the `key`value.

| Parameter | Type   | Description                    |
| --------- | ------ | ------------------------------ |
| key       | string | The key for data to save.      |
| value     | string | The value to save on database. |

##### insertString Response

The operation call will return the `jobId` of the job running on Blochchain Web Services to execute your command (remember blockchain operations are asynchronous and can take a while to finish).

#### :: selectString

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

$.ajax({
  method: "POST",
  url: "https://api.bweb.services/v1/call",
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

Gets a value you previously stored on Ethereum database by calling `insertString`.

##### selectString Request Parameters

Use the following parameters to call `selectString` operation:

| Parameter  | Value                                                                   |
| ---------- | ----------------------------------------------------------------------- |
| contract   | Ethereum.Database.Immutable                                             |
| operation  | selectString                                                            |
| parameters | [selectString Operation Parameters](#selectString-operation-parameters) |

Check [Passing Parameters](#passing-parameters) for other required parameters.

###### selectString Operation Parameters

Set the `key` value to get the data you previously saved.

| Parameter | Type   | Description               |
| --------- | ------ | ------------------------- |
| key       | string | The key for data to save. |

##### selectString Response

The operation call will return the `jobId` of the job running on Blochchain Web Services to execute your command (remember blockchain operations are asynchronous and can take a while to finish).
