---
description: Frequently Asked Questions
---

# FAQ

{% hint style="warning" %}
Please note that since Chainsight is still under development, specifications may change before the official release.
{% endhint %}

### Q. What is Chainsight in a nutshell?

Chainsight is an interchain composable oracle network. Some indexers store historical snapshot data, and some lens components calculate new data based on the indexers. A large number of components are combined as data logos to efficiently get the desired data you want.

### Q. What is a typical use of Chainsight?

Dynamic DeFi based on data-driven decision-making. For example, when considering a Dynamic Money Market, a feature could be implemented through Chainsight's historical data that would automatically list assets there if they meet specified criteria.

### Q. What kind of data we can use?

For example, you can incorporate volatility calculated based on historical data into your DeFi. It will also be possible to obtain prices for minor assets that cannot be supported by Chainlink, etc., Asset Rating, and long-term interest rates for government bonds.

### **Q. What L1/L2 does Chainsight support**

We first support Ethereum, Avalanche, and Scroll. We will gradually announce partnerships in the future.

### Q. Is Chainsight a bridge?

No, data is written directly from Chainsight via [DKG](https://eprint.iacr.org/2021/339) and [tECDSA](https://internetcomputer.org/docs/current/developer-docs/integrations/t-ecdsa) to oracles deployed on the external EVM network.

### Q. Is Chainsight built on an original layer1 or such?

No, Chainsight is not L1, but a collection of canister smart contracts running on Internet Computer. It is composed of not only components that process data, but also various canisters, including a management canister that monitors inter-calls between canisters.

### Q. Why is Chainsight so efficient at capturing data?

If the on-chain data you want to use has already been indexed by someone else, you can reference that data and you don't need to reconstruct the data again. In other words, by deploying only the necessary parts and reusing the others, new information can be generated inexpensively.

### Q. How much does it cost to index data?

It depends on the data you want to retrieve and the pace of data updating. Please see the cost table for details. For reference, the cost to synchronize 9 million ERC-20 Transfer events is about $50. However, once the data has been indexed by someone else, it is free to use them.

### Q. How often can data be synced?

The user of the data can set it as desired. However, the more frequently the data is updated, the more gas it costs.
