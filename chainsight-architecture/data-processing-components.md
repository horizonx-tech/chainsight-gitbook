---
description: Key components of the network
---

# Data Processing Components

Chainsight empowers developers to access and utilize desired on-chain data through a combination of various data processing components. The system comprises an Indexer that collects on-chain data and stores it, an Algorithm Lens that extracts and references data from the Indexer, and a Relayer that writes the data to other blockchains. Together, these components enable developers to efficiently collect and use a wide range of on-chain data. Indexers can be classified into three types based on their roles, resulting in a total of five components, including the Algorithm Lens and Relayer.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-26 at 10.42.32.png" alt=""><figcaption><p>Three Indexers, Lens, and Relayer</p></figcaption></figure>

* **Snapshot Indexer** - This component can routinely collect data from any source. Periodically query view functions such as smart contracts and algorithmic lenses or periodically call specified endpoints deployed on the Web, and track the results of those calls. Periodic snapshot data can serve as historical data for further analysis.
* **Event Indexer** - Synchronizes event data from a specified blockchain and stores a list of event records. For example, collecting ERC-20 Transfer events can provide a basis for analyzing token transfer history. This data is primarily prepared for use with subsequent components.
* **Algorithm Indexer** - Processes the raw data collected by Event Indexer and Snapshot Indexer for analysis and generates insightful metrics. For instance, the Algorithm Indexer takes the raw data of ERC-20 Transfer events from the Event Indexer and creates separate mapping data on how many tokens are held by each address.

In contrast to the Indexer, the Algorithm Lens and Relayer do not store the state themselves but write to other blockchains.

* **Algorithm Lens** - Retrieves existing data from the Indexer using custom logic, enabling the extraction of specific calculation results or desired synthesized values. For instance, an Algorithm Lens calculates an economic index that evaluates decentralization based on the percentage of token holders.
* **Relayer** - Transfers data to other blockchains using threshold signing schemes like tECDSA. The destination is a data oracle pre-deployed on the target blockchain, which is synchronized in a key-value format at predefined intervals.

By offering a structured architecture for managing data from various blockchains, Chainsight simplifies the process for developers to access and utilize essential on-chain data in their applications. To explore use cases on how to combine these components, please click [here](../use-cases/exploring-chainsights-potential/demo1-decentralization-assessment.md).

The following articles also do a deep dive into the components.

https://chainsight.network/blog/look-into-snapshot-indexer
https://chainsight.network/blog/look-into-relayer

### How to Deploy an Indexer

Users can effortlessly deploy an Indexer through the WebUI by providing essential information such as the target contract address and event name and making a payment without requiring in-depth knowledge about the backend of Chainsight. For example, an Event Indexer can be deployed by entering the target contract's Network ID and the contract address and selecting the target event. For an Algorithm Indexer, deployment is achieved by selecting which Indexer to use as the data source and describing the desired algorithm.

### Synchronization Interval

Indexers and Relayers synchronize data at regular intervals. For example, if an Event Indexer is set to synchronize data every hour, it will synchronize the difference data at that time. Synchronization intervals can be managed by the owner who deployed the Indexer or Relayer. Developers must set appropriate time intervals, taking into account the fees to be consumed and the application requirements.
