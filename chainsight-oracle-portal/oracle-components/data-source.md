# Data Source

Chainsight allows you to securely register data from virtually **any source**. Using the Chainsight Portal’s **Data Pipeline Builder (currently shared with only early-access teams)**, a user can add a new data source by specifying an endpoint (for example, a web API URL or a blockchain node RPC). The platform supports sources ranging from simple HTTP(S) APIs to on-chain data queries​. This means developers can bring off-chain data (prices, weather info, etc.) or cross-chain information into Chainsight with ease​.

{% embed url="https://youtu.be/fhjbWNZPTIw" %}



For instance, to add a REST API as a data source, you simply provide the API’s URL in the Pipeline Builder. The system can then pull data from that URL as needed. Setting a custom URL as the endpoint makes data retrieval extremely flexible – **any** data accessible via HTTP(S) can be turned into an on-chain feed. This flexibility allows integration of bespoke data feeds without custom oracle development.

Chainsight ensures the data source is registered securely. When the source is added, you can optionally use verification methods (like cryptographic proofs or consensus, mentioned in the indexer page) to ensure the fetched data is authentic and untampered. In summary, the Data Source stage defines **what** data to fetch and **where** to fetch it from, forming the first step of the Chainsight pipeline.
