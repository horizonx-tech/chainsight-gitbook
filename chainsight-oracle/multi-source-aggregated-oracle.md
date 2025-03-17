# Multi-Source Aggregated Oracle

{% hint style="info" %}
This is currently under code audit. We will release the source code as soon as the audit is finished.
{% endhint %}



<figure><img src="../.gitbook/assets/Frame 48096605.png" alt=""><figcaption></figcaption></figure>

The **Multi-Source Oracle** is one of the features that ChainSight provides on-chain data. It combines price feeds and data points from multiple premier oracle networks into a single, unified source of truth. Instead of relying on one oracle provider, this solution pulls data from **Chainlink**, **Pyth**, and **ChainSight’s own data feeds**, then aggregates them on-chain. By leveraging several sources, the Multi-Source Oracle delivers more reliable and robust data to decentralized applications. Developers and protocols can now access a consolidated feed that automatically balances inputs and filters out anomalies, all through a **single smart contract interface**. This introduction of a multi-source approach marks a significant step forward in ensuring data accuracy and uptime for Web3 projects.

### Benefits

* **Aggregation of Multiple Sources:** Fetches data from Chainlink, Pyth, and ChainSight’s native feeds, combining them into one output. This ensures that no single source dominates the feed – you benefit from the strengths of each provider. For example, Chainlink’s extensive market coverage, Pyth’s high-frequency updates, and ChainSight’s custom data feeds all contribute to a more complete dataset.
* **Timestamp-Based Weighted Averages:** The aggregator uses **timestamp-weighted aggregation** logic. Data points are weighted based on freshness (timestamps) and possibly source reliability metrics. Newer data or sources known for timely updates carry more weight, whereas older or lagging data points are given less influence. This approach ensures the reported value reflects the most current market conditions and reduces lag from slower sources. In practice, if one source updates a few minutes later than others, its data will have slightly less impact on the final value, smoothing out discrepancies in update intervals.
* **Outlier Detection & Fallback Mechanisms:** The Multi-Source Oracle has built-in logic to detect outliers or abnormal data from any source. If one oracle’s price deviates beyond a reasonable range compared to others, the system can automatically down-weight or exclude that data point. This prevents faulty data (due to API downtime, flash crash, or manipulation attempt) from skewing the aggregate. Furthermore, if an entire source fails (e.g., one network is down), the oracle automatically falls back to using the remaining sources. Your applications continue to receive data without interruption, albeit from a reduced set of inputs, until the affected source recovers.
* **Seamless Interface Compatibility:** The aggregated oracle feed is exposed through the **same interface as familiar oracles**. For example, on EVM chains it implements Chainlink’s `AggregatorV3Interface`, so you can call `latestRoundData()` or `decimals()` just as you would for a Chainlink feed. Similarly, it can mirror Pyth’s data access patterns for those using Pyth. This means **no new custom integration** is required – you simply point your existing oracle-reading code to the Multi-Source Oracle’s contract address. Existing Chainlink or Pyth users can switch over by updating the contract address to ChainSight’s aggregator, with all functions working as expected.
