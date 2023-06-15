## Database.Mutable

> Mutable insertString operation parameters call example.

```javascript
var parameters = {
  solution: "Database.Mutable",
  version: 1,
  network: "sepolia",
  operation: "insertString",
  parameters: {
    key: "a-key",
    value: "Hello World!",
  },
};
```

This solution simplifies interactions with blockchain networks, providing a seamless way to store data on a blockchain.

It abstracts the complexities of blockchain transactions and network fees, allowing users to focus solely on their data.

<p class="product-header">Solution</p>

"_This is in contrast to a mutable object (changeable object), which can be modified after it is created._"

<p class="product-author">Author</p>

<p class="s2">Blockchain Web Services</p>

<p class="product-title">Description</p>

Mutable insert operations can overwrite previously saved data and the same insert/select operations are available for `Ethereum.Database.Mutable` contract (you just need to replace `contract` and `version` parameter to use Mutable or Immutable contract).

<p class="product-title">Networks</p>

<p class="product-network">Ethereum</p>

Click on Contract Address to check verified contract at `etherscan.io`.

| Network Id | Contract Address                                                                                                                   | Version |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------- | ------- |
| ethereum   | [0x1aFEe6DD9A1D4af90c39CD8B09296FC505beA00d](https://etherscan.io/address/0x1aFEe6DD9A1D4af90c39CD8B09296FC505beA00d)              | 1       |
| sepolia    | [0x58ca3f44cF5c84C1C29591A483be3288D0A01b7C](https://sepolia.etherscan.io/address/0x58ca3f44cF5c84C1C29591A483be3288D0A01b7C) | 1       |

<p class="product-network">Polygon</p>

Click on Contract Address to check verified contract at `polygonscan.com`.

| Network Id | Contract Address                                                                                                                   | Version |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------- | ------- |
| polygon   | [0xEF28790d1C8ac0833e8c05BB4344e479Da8a4Dd3](https://polygonscan.com/address/0xEF28790d1C8ac0833e8c05BB4344e479Da8a4Dd3)               | 1       |
| mumbai    | [0xEF28790d1C8ac0833e8c05BB4344e479Da8a4Dd3](https://mumbai.polygonscan.com/address/0xEF28790d1C8ac0833e8c05BB4344e479Da8a4Dd3) | 1       |

<p class="product-title">Operations</p>

You can use the same operations as for `Database.Immutable` service, changing the parameter solution to `Database.Mutable`.

<br/><br/>
<span class="login-text">Login to your BWS account and test this solution using Postman.<span>
<br/><br/>
<span class="button button-small">
<a href="https://prod.bws.ninja/front-sign-in.html">Log In</a>
</span>