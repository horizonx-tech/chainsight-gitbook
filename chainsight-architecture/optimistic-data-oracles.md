---
description: Constantly updated data oracles
---

# Optimistic Data Oracles

Chainsight provides an on-chain data oracle for each supported blockchain. Networks have varying gas costs, ranging from expensive ones like Ethereum to more affordable sidechains, but minimizing on-chain data is crucial for any network to reduce gas costs. Additionally, most blockchains cannot access data outside their network, requiring an external data source, such as an Oracle contract, and someone to write data to that contract. Chainsight carries data within its network to other chains, eliminating single points of failure by combining distributed node’s derived keys into a threshold signature.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-23 at 12.29.28.png" alt=""><figcaption><p>Data Oracle Contract on the destination chain</p></figcaption></figure>

Data Oracle contracts are pre-deployed on blockchains supported by Chainsight, allowing developers to access data cost-effectively without deploying the Oracle contract themselves.

To write data to the Data Oracle, developers first deploy a Relayer through the WebUI by specifying which data to write and at what time interval. The Relayer continually writes the specified data to the target chain's Data Oracle, using a one-to-one issued Data ID as the key. Any DApp on the target chain can retrieve on-chain insights by referencing the Data Oracle with the Data ID as an argument.

