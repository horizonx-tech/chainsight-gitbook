---
description: How Chainsight is structured
---

# System Outline

Chainsight is based on Internet Computer's [Chain-key Cryptography](https://support.dfinity.org/hc/en-us/articles/360057605551-What-is-chain-key-cryptography-). This allows data to be kept in sync with any L1/L2, such as Optimism or Scroll, in a trustless manner. Data is first indexed into the storage of canister smart contracts running on top of Internet Computer, and by connecting each canister smart contract like Lego blocks, even more complex data can be handled at low cost. The overall picture of Chainsight is as follows:

<figure><img src="../.gitbook/assets/Screenshot 2023-08-16 at 16.56.33.png" alt=""><figcaption><p>Chainsight Architecture</p></figcaption></figure>

Components deployed by developers using the CLI or UI run on Internet Computer as Composable Data Oracles. Apart from these, Chainsight Management Canisters have been deployed to control the entire network, and incentives for data providers and alerts for corrupt data will be implemented in the future milestone.

