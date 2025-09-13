# Oracle Risk

### Oracle Dependency

All ChainSight perpetual markets rely on external price feeds to calculate funding rates and mark prices. Variance perpetuals specifically require accurate historical price data to calculate 30-day realized volatility.

### Potential Oracle Failures

* **Data source outages**: Temporary unavailability of price feeds
* **Calculation errors**: Incorrect volatility or index computations
* **Manipulation attempts**: Bad actors attempting to influence oracle prices

### HIP-3 Oracle Requirements

As specified in Hyperliquid's documentation, builders must:

* Maintain reliable oracle infrastructure
* Configure appropriate price bands and sanity checks
* Face slashing penalties for oracle manipulation

### Trader Protections

Hyperliquid's core infrastructure includes:

* Position liquidations based on oracle mark prices
* Funding rate calculations using builder-provided feeds
* Emergency pause mechanisms for extreme oracle deviations
