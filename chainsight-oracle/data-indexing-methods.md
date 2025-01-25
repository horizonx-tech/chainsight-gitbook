# Data Indexing Methods

Chainsight supports **three** main ways to bring data into the network, each balancing cost, security, and speed.

### A. Cost-Friendly Backend Ingestion

* **Summary**: A simpler approach where Chainsight’s internal nodes fetch data from an API and push it into the indexer. Minimal overhead.
* **Pros**: Cheaper, faster to set up. Great for frequent updates on less critical data.
* **Cons**: Doesn’t provide advanced cryptographic proofs of authenticity. Best used if cost is the primary concern and you trust the data source or the aggregator.

### B. **zkTLS-Based Ingestion**

* **Summary**: Collaborate with an external cryptographic provider that fetches data, then **proves** it hasn’t been tampered with by generating a zero-knowledge proof.
* **Pros**: Offers high integrity. Even though the node runs off-chain, the proof ensures data authenticity.
* **Cons**: Range of supported data might be smaller; also typically higher overhead. Perfect for real-time pricing with strong security requirements.

### C. **Distributed HTTPS Outcalls (Consensus)**

* **Summary**: A set of distributed nodes each call the same HTTPS endpoint, then reach consensus on the result. If a majority or threshold agrees, the final data is stored.
* **Pros**: No single aggregator. Good for widely used sources like public APIs.
* **Cons**: Must wait a few seconds for consensus, so slower than direct push.
