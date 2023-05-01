## MegaLock.ninja

<pre style="background-color: initial; padding: 0 0 20px 0; position: absolute; right:0;">
  <img src="images/megalock-snap-1.png" style="width:95%">
</pre>

[MegaLock.ninja](https://megalock.ninja/) demo website only needs 3 calls to **Blockchain Web Services** API to securely save data into Sepolia Network:

- [insertString](#insertString-operation) to save data to the blockchain,
- [selectString](#selectString-operation) to get the data from the blockchain, and
- [fetch](#fetch-operation) to fetch API calls status.

Please note `insertString` and `selectString` are asynchronous operations and return a `jobId` value...

<div class="center-column"></div>

```json
{
  "statusCode": 200,
  "statusMessage": "",
  "info": {
      "jobId": "a1ac1b69-36cd-44ed-aacb-440b31a57dd7"
  }
}
```
<br/>
... you can use to track the operation status by calling the `fetch` method:

<div class="center-column"></div>

```js
async function callFetchJobBWSAPI(endpoint, jobId, apiKey) {
  var body = {
    jobId: jobId,
  };

  const response = await fetch("https://api.bws.ninja/v1/call/fetch", {
    method: "post",
    body: JSON.stringify(body),
    headers: { "Content-Type": "application/json", "X-Api-Key": apiKey },
  });
  const result = await response.json();

  if (result.statusCode != 200) throw new Error(result.statusMessage);

  return result;
}
```

### Saving Data to Ethereum

<pre style="background-color: initial; padding: 0 0 20px 0; position: absolute; right:0;">
  <img src="images/megalock-snap-3.png" style="width:95%">
</pre>

Saving data to the blockchain using [Blockchain Web Services](https://bws.ninja) is as easy as calling the `insertString` method indicating a pair key/value:


<aside class="notice">
In this example we use <a href="#ethereum-database-mutable">Ethereum.Database.Mutable</a> to enable data to be changed.
</aside>

<div class="center-column"></div>

```js
async function callInsertStringBWSAPI(endpoint, key, value, apiKey) {
  var body = {
    contract: "Ethereum.Database.Mutable",
    version: 1,
    network: "sepolia",
    operation: "insertString",
    parameters: {
      key: key,
      value: value,
    },
  };

  const response = await fetch(endpoint + "/call", {
    method: "post",
    body: JSON.stringify(body),
    headers: {
      "Content-Type": "application/json",
      "X-Api-Key": apiKey,
    },
  });
  const result = await response.json();

  if (result.statusCode != 200) throw new Error(result.statusMessage);

  return result;
}
```
<br/>


#### Getting Blockchain Receipt 

<pre style="background-color: initial; padding: 0 0 20px 0; position: absolute; right:0;">
  <img src="images/megalock-snap-4.png" style="width:95%">
</pre>


Once the blockchain operation has finished, `fetch` method will return all the data you need to access and validate your transaction:

<div class="center-column"></div>

```js
{
    "statusCode": 200,
    "statusMessage": "",
    "info": {
        "status": {
            "Value": "completed"
        },
        "statusMessage": "undefined",
        "request": {
            "contract": "Ethereum.Database.Immutable",
            "version": 2,
            "network": "polygon",
            "operation": "insertBytes32",
            "parameters": {
                "key": "1682957133280",
                "value": "Hello World!"
            }
        },
        "hash": "0x59fc917cebc3f4628ede9b7c50e848e4169d83c592554ddbc8761b6bafa8a963",
        "txnUrl": "https://polygonscan.com/tx/0x59fc917cebc3f4628ede9b7c50e848e4169d83c592554ddbc8761b6bafa8a963",
        "txnSnapshotUrl": "https://s3.amazonaws.com/bws-middleware-prod-website/tx/polygon/0x59fc917cebc3f4628ede9b7c50e848e4169d83c592554ddbc8761b6bafa8a963.jpg",
        "receipt": {
            "blockHash": "0x4a2734767b6fc589f305ead781b305f7d46c6accb6c42b44857e1a367c1d5102",
            "blockNumber": 42182068,
            "contractAddress": null,
            "cumulativeGasUsed": 132699,
            "effectiveGasPrice": 400000000000,
            "from": "0x9089db83f0590ec2ed01a5eb4f8584dd6f4bdac7",
            "gasUsed": 67821,
            "status": true,
            "to": "0x58ca3f44cf5c84c1c29591a483be3288d0a01b7c",
            "transactionHash": "0x59fc917cebc3f4628ede9b7c50e848e4169d83c592554ddbc8761b6bafa8a963",
            "transactionIndex": 1,
            "type": "0x0"
        },
        "networkCurrency": "MATIC",
        "networkCost": 0.03,
        "networkFee": 0.1,
        "networkTotal": 0.13,
        "proofOfRegistryUrl": "https://bws.ninja/tx.html?t=0x59fc917cebc3f4628ede9b7c50e848e4169d83c592554ddbc8761b6bafa8a963",
        "guid": "a1ac1b69-36cd-44ed-aacb-440b31a57dd7",
        "type": {
            "value": "blockchain-job"
        },
        "timestampInMillis": 1682957142984
    }
}
```

<br/>
You can use for example the returned parameter `txnUrl` to check at the network scan website a proof of execution (e.g. [https://polygonscan.com/tx/0x59fc917cebc3f4628ede9b7c50e848e4169d83c592554ddbc8761b6bafa8a963](https://polygonscan.com/tx/0x59fc917cebc3f4628ede9b7c50e848e4169d83c592554ddbc8761b6bafa8a963)).

<br/>
![Megalock.ninja](images/megalock-snap-6.png)

### Getting Data from Ethereum

<pre style="background-color: initial; padding: 0 0 20px 0; position: absolute; right:0;">
  <img src="images/megalock-snap-8.png" style="width:95%">
</pre>

To get data you saved into the blockchain use the same procedure but using `selectString` operation passing the 'key' value you used previously:

<aside class="notice">
Megalock.ninja encrypts the data before sending it to the blockchain.
</aside>

<div class="center-column"></div>

```js
async function callSelectStringBWSAPI(endpoint, key, apiKey) {
  var body = {
    contract: "Ethereum.Database.Mutable",
    version: 1,
    network: "ropsten",
    operation: "selectString",
    parameters: {
      key: key,
    },
  };

  const response = await fetch(endpoint + "/call", {
    method: "post",
    body: JSON.stringify(body),
    headers: {
      "Content-Type": "application/json",
      "X-Api-Key": apiKey,
    },
  });
  const result = await response.json();

  if (result.statusCode != 200) throw new Error(result.statusMessage);

  return result;
}
```
<br/>
Check for completation using `fetch` method, and when status is ```completed``` the fetch operation will also return the value you ask from the blockchain:

<div class="center-column"></div>

```json
{
  "statusCode": 200,
  "statusMessage": "",
  "info": {
      "status": {
          "Value": "completed"
      },
      "statusMessage": "undefined",
      "request": {
          "contract": "Ethereum.Database.Immutable",
          "version": 2,
          "network": "polygon",
          "operation": "selectBytes32",
          "parameters": {
              "key": "1682957133280"
          }
      },
      "result": "Hello World!",
      "networkCost": 0.0,
      "networkFee": 0.0,
      "networkTotal": 0.0,
      "guid": "4807d50e-1a1c-4248-ae03-9c0a3c99e475",
      "type": {
          "value": "blockchain-job"
      },
      "timestampInMillis": 1682966801153
  }
}
```


