---
description: Frequently Asked Questions
---

# FAQ

### Q. What is Chainsight in a nutshell?

Chainsight is a cutting-edge on-chain data hub that consolidates data from various markets and provides on-chain accessibility. Learn how to utilize Chainsight [here](https://app.gitbook.com/o/tWKF1BS3PbvW5VBUezX7/s/TVspkMrYiJzUvsCmQwk0/\~/changes/77/chainsight-overview/how-to-use-chainsight).

### Q. What kind of data we can use on Chainsight?

With a few exceptions, any data can be handled. Please contact the Chainsight team for further information.

### **Q. What L1/L2 does Chainsight support now?**

A list of supported networks can be found [here](https://github.com/horizonx-tech/chainsight-management-oracle), but the available data varies between networks. Please feel free to contact us with any requests.

### Q. Is Chainsight a bridge?

No, data is written directly from Chainsight via [DKG](https://eprint.iacr.org/2021/339) and [Chainkey Cryptography](https://support.dfinity.org/hc/en-us/articles/360057605551-What-is-chain-key-cryptography) to oracles deployed on each EVM network.

### Q. Is Chainsight built on an original layer1 or such?

No, Chainsight is not L1, It is a data hub built on Internet Computer. The platform consists of a set of highly customized canister smart contracts. It is composed of not only components that process data, but also various canisters, including a management canister that monitors inter-calls between canisters. Anyone can add data pipelines they need through CLI or UI.

### Q. Why is Chainsight so efficient at capturing data?

Building on-chain data legos, like DeFi's Money Lego, allows reusing indexed data. This lowers user costs as more people use Chainsight.

### Q. How much does it cost to index data?

It depends on the frequency and volume of data synchronization. For more details, please contact the team.

### Q. How often can data be synced?

You can deploy a Relayer that synchronizes data for each user, so you can update it as you wish. It's totally customizable.
