---
description: Volatility indicators that are updated automatically on a regular basis
---

# Demo2: Volatility Oracles

This demo showcases each asset's realized volatility (RVOL) and value at risk (VaR) indexes based on historical price. A link to the demo will be available soon.

While implied volatility refers to the market's assessment of future volatility, realized volatility (RVOL) measures what actually happened in the past. The measurement of the volatility depends on the particular situation. For example, one could calculate the realized volatility for the market in March of 2023 by taking the standard deviation of the daily returns within that month.

$$
RVOL_{t} = \sqrt{N_{1}} \times \sqrt{\frac {\sum_{i=1}^N r_{t,i}^2} N}
$$

$$
r_{t,i} = 100 \times ln(P_{t,i}/P_{t,i-1})
$$

where P is the asset price, and N is the number of observations per day.

The figure below is a flow diagram illustrating how the Indexer and Relayer work together to obtain valuable indexes calculated by historical price data.

<figure><img src="../../.gitbook/assets/Screenshot 2023-05-04 at 18.32.55.png" alt=""><figcaption><p>Realized Volatility and Value at Risk Calculation Flow</p></figcaption></figure>

In this example, the data source is the Snapshot Indexer, represented by the yellow object. It retrieves WETH price data from Uniswap on Ethereum, both hourly and daily. The RVOL and VaR indexes are calculated using the WETH time-series data through the Algorithm Lens, depicted by the pink object. Additionally, the RVOL and VaR calculation results can be tracked as time-series data by retaking snapshots. Finally, each value can be transferred to Polygon using the Relayer.

The following table shows the costs incurred by Chainsight in obtaining RVOL, measured every 24 hours.

| Component Type        | Frequency | Cost Per Day |
| --------------------- | --------- | ------------ |
| WETH Snapshot Indexer | Hourly    | $0.17        |
| WETH Snapshot Indexer | Daily     | $0.0071      |
| RVOL Lens             | -         | $0.0000050   |
| RVOL Snapshot Indexer | Hourly    | $0.0000038   |
| RVOL Snapshot Indexer | Daily     | $0.00000016  |
| RVOL Relayer          | Hourly    | $0.0575      |
| RVOL Relayer          | Daily     | $0.0024      |
