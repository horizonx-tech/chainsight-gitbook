# Time-Series Data Retention

One of the core features of Chainsight is **time-series indexing**. Instead of storing just the latest price, we preserve historical data, but in an optimized form:

1. **Minute-By-Minute for the First Hour**
   * Every minute, the indexer fetches a new data point from the chosen source.
   * **Total**: 60 data points for the first hour.
2. **Hourly Aggregation**
   * After 1 hour, the system compresses the previous 60 data points into 1 hourly snapshot.
   * Over a day, that results in **24** hourly data points.
3. **Daily Aggregation**
   * After 1 day passes, the indexer consolidates the 24 hourly points into a single daily point. Over a week, that’s 7 data points.
4. **90-Day Retention**
   * We maintain daily data for up to 90 days. Beyond that, it’s discarded (unless you configure extended storage).

**Implication**: DeFi projects can pull **historical** data easily—from minute-level recency in the last hour to daily aggregates going back \~90 days. This “historical on-chain ledger” is an **uncommon** feature among decentralized oracles, enabling advanced analytics (like generating volatility or rating feeds) without off-chain storage.
