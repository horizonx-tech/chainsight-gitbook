---
description: Why Chainsight Is Cheaper and More Flexible
---

# Overview

<figure><img src="../.gitbook/assets/Screenshot 2025-02-21 at 16.00.34.png" alt=""><figcaption></figcaption></figure>

Oracle comprises a modular pipeline of on-chain components that fetch, process, and deliver data to smart contracts. The pipeline stages are:

* **Data Source:** The origin of the data (could be a web API, blockchain node, etc.), configured in Chainsight to securely ingest external information.
* **Base Indexer:** Retrieves raw data from the source at defined intervals and stores it on-chain for indexing.
* **Advanced Indexer:** Applies custom logic (WebAssembly modules) to the indexed data, enabling complex transformations or analytics.
* **Relayer:** Takes the processed data and transmits it to the target blockchain, using threshold cryptographic signatures for trustless delivery.
* **Oracle:** An on-chain contract on the destination chain that receives and stores the data, providing a read interface for DApps.

**Composability and Data Reusability:** Chainsight indexes data once and allows multiple projects to reuse the same data feed. This network effect means if one project sets up a particular price feed, others can tap into it without duplicating effort, reducing the per-project cost. As more data sets and users join, the average administrative cost per project drops – unlike a typical “one oracle feed per project” scenario

**Threshold Signing (Security):** Rather than relying on a single centralized bridge, Chainsight uses distributed nodes that sign updates **directly on each target chain** via threshold ECDSA. In this scheme, each node holds a share of the private key, and they collectively produce a valid signature for the oracle update. This means no separate bridge contract or single operator is needed – the cryptographic security is shared among multiple nodes. The result is lower trust assumptions (no single party can compromise the feed) and removal of any single point of failure​
