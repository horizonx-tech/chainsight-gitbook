# Oracle Contract

The final component is the on-chain **Oracle contract** that lives on the destination blockchain. Chainsight typically deploys an `Oracle.sol` contract on each target EVM chain to serve as the on-chain data store for the feeds. This contract is designed to be flexible – it can store arbitrary data values, each identified by a unique key, and it keeps track of the latest value and when it was updated.

```solidity
function updateStateByKey(
        bytes calldata _data,
        bytes32 key
 ) external override {
    // Store the price data under (msg.sender, key).
    // The block timestamp is recorded for checking the updated time.
}

function readAsUint256WithTimestamp(address sender, bytes32 key)
    external view
    returns (uint256, uint64)
{
    // Return the uint256 value plus the timestamp
}

// Overloads for other data types (string, int256, etc.)
```

Every time the Relayer sends an update, it calls the Oracle contract’s function `updateStateByKey(bytes calldata _data, bytes32 key)`. The oracle contract then stores the provided data (a blob of bytes) under the given key, and records the block timestamp of the update internally​. The `key` is typically a `bytes32` that acts as an identifier for the data feed (for example, a price pair symbol or an index name). Notably, the contract uses the combination of the caller’s address (`msg.sender`) and the key as a unique slot for storage, so multiple independent data feeds can use the same contract without interfering (each Chainsight data pipeline would have its own sender address and keys)​.

For consuming applications, the Oracle contract provides **read** functions. The primary one for numeric data is `readAsUint256WithTimestamp(address sender, bytes32 key)`. A dApp can call this view function to get the latest `uint256` value stored under a given `(sender, key)` pair, along with the timestamp of when that value was last updated (the function returns a tuple of `(value, timestamp)`). For example, a DeFi smart contract might call `oracle.readAsUint256WithTimestamp(chainsightFeedAddress, priceFeedKey)` to retrieve the current price and the time of last update. The Chainsight Oracle contract also supports similar read functions for other data types (e.g. `readAsStringWithTimestamp`, `readAsInt256WithTimestamp`, etc.) to handle text data or signed integers. In most cases, price feeds and indicators use unsigned 256-bit integers, which map neatly to the `uint256` type on EVM.



**How to Use the On-Chain Data:** From a developer’s perspective, interacting with Chainsight’s on-chain data is straightforward. To **read** the latest value, your smart contract just calls the appropriate `read...WithTimestamp` function on the Oracle contract. This can be done within contract code (as a view call) or off-chain via JSON-RPC. The returned timestamp allows your application to check data freshness (for instance, ignoring a price if it’s too old). Because these are standard public/view functions, they are gas-free to call off-chain and cost only a minimal amount of gas if called within another contract (no storage writes, just a read).

Under the hood, Chainsight’s distributed node network ensures that `updateStateByKey` is called whenever there’s new data to publish (subject to the Relayer’s filters). Developers don’t need to worry about the mechanics of data delivery – they simply read from the Oracle contract as needed. The combination of **composable data pipelines** and the on-chain Oracle means you get real-time, verified data on-chain, backed by a robust update mechanism. In short, the Oracle contract is the on-chain endpoint where Chainsight’s off-chain and cross-chain data becomes accessible to your smart contracts in a single function call​. This allows any DApp to seamlessly integrate up-to-date prices, indices, or other information by reading from Chainsight’s Oracle, leveraging on-chain data that is fresh, historical when needed, and cryptographically secured by the Chainsight network.

Oracle Contarct on EVM

{% embed url="https://github.com/horizonx-tech/chainsight-management-oracle" %}

{% hint style="info" %}
Solana Oracle will be coming to the pipeline soon. If you have a request to make oracles on Solana or Move VM, please reach out to us.
{% endhint %}

