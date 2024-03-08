---
description: Frequently Asked Questions
---

# FAQ

{% hint style="warning" %}
Please note that since Chainsight is still under development, specifications may change before the official release.
{% endhint %}

### Q. What is Chainsight in a nutshell?

Chainsight is data service platform with composable oracles that bridge between chains or on-chain and off-chain.

An indexer takes data from any on-chain or web source and stores it as a snapshot, a lens component computes and generates new indices/data from the stored snapshots, a relayer propagates the data to the different chains.

This combination of numerous components allows for efficient computation and propagation of the data required.

### Q. What is a typical use of Chainsight?

This is effective for any Dapps that handle "data" in a creative way. A typical example is Dynamic DeFi based on data-driven decision-making. When considering a Dynamic Money Market, a feature could be implemented through Chainsight's historical data that would automatically list assets there if they meet specified criteria. Not just for DeFi, users can target and leverage any data, including data queries from Web2 social media APIs, sports/sports data for betting applications, etc.

### Q. What kind of data we can use?

For example, you can incorporate volatility calculated based on historical data into your DeFi. It will also be possible to obtain prices for minor assets that cannot be supported by Chainlink, etc., Asset Rating, and long-term interest rates for government bonds.

### **Q. What L1/L2 does Chainsight support**

We support EVM-based chains at the moment, and expanding our horizons to Bitcoin L2 and Non-EVM chains. We plan to announce partnerships in due course.

### Q. Is Chainsight a bridge?

No, data is written directly from Chainsight via [DKG](https://eprint.iacr.org/2021/339) and [tECDSA](https://internetcomputer.org/docs/current/developer-docs/integrations/t-ecdsa) to oracles deployed on the external EVM network.

### Q. Is Chainsight built on an original layer1 or such?

No, Chainsight is not L1, It is a data platform built on the Internet Computer Blockchain. The platform consists of a set of highly customized canister smart contracts. It is composed of not only components that process data, but also various canisters, including a management canister that monitors inter-calls between canisters. Users can add the data pipeline they need through simple tools and UI.

### Q. Why is Chainsight so efficient at capturing data?

If the on-chain data you want to use has already been indexed by someone else, you can reference that data and you don't need to reconstruct the data again. In other words, by deploying only the necessary parts and reusing the others, new information can be generated inexpensively.

### Q. How much does it cost to index data?

It depends on the data you want to retrieve and the pace of data updating. Please see the cost table for details. For reference, the cost to synchronize 9 million ERC-20 Transfer events is about $50. However, once the data has been indexed by someone else, it is free to use them.

### Q. How often can data be synced?

The user of the data can set it as desired. However, the more frequently the data is updated, the more gas it costs.
