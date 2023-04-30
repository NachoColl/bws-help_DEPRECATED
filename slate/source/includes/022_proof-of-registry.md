# Proof Of Registry

> Use proofOfRegistryUrl to access/share Proof of Registry website

```javascript
{
    "statusCode": 200,
    "info": {
        ...
        "request": {
            "contract": "Ethereum.Database.Immutable",
            "version": 2,
            "network": "mumbai",
            "operation": "insertBytes32",
            "parameters": {
                "key": "1681656626141",
                "value": "Hello BWS!"
            }
        },
        ...
        "receipt": {
            "blockHash": "0xf5cc369697dbcef...02953c03be46a505bd0d",
            "blockNumber": 34173980,
            ...
            "transactionHash": "0x4a36cc0a3b1...1ed92688034",
            "transactionIndex": 0,
            "type": "0x0"
        },
        "proofOfRegistryUrl": "https://staging.bws.ninja/tx.html?t=0x16b3c7e996c2e650d28fadca3cc74a26e506869234de8754121f013586d11a92"
    }
}
```

Use Blockchain Web Services Proof of Registry to easily and securely validate your Blockchain transactions. A user-friendly interface that allows you to share your transaction as a proof of its inclusion in the Blockchain registry. 

This proof can be used to demonstrate the validity and authenticity of your transaction, providing confidence and trust to all parties involved. 

Additionally, by including the Identity domain of the caller in the proof, we provide an additional layer of transparency, ensuring that all transactions are legitimate and verifiable. 

You can check an example <a href="https://staging.bws.ninja/tx.html?t=0x16b3c7e996c2e650d28fadca3cc74a26e506869234de8754121f013586d11a92" target="_blank">here</a>.

<br/>
![Proof of Registry](images/proof-of-registry-snapshot-help.png)