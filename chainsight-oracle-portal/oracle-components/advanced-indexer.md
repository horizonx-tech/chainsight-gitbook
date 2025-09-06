# Advanced Indexer

While the Base Indexer handles raw data collection, the Advanced Indexer allows for **historical analysis and custom computations** on that data. This component lets developers upload custom processing logic in WebAssembly (Wasm) modules – typically written in Rust as examples but you can choose whatever – to run on the indexed data. The logic can combine multiple data sources, perform calculations, and produce new derived insights, all on-chain.

**WebAssembly-Based Logic:** By supporting WASM, Chainsight enables user-defined code to execute within its secure on-chain environment. Developers write their data-processing module (e.g. in Rust), and Chainsight’s tooling compiles it to WebAssembly and deploys it into the Advanced Indexer. The platform then **verifies** this module (ensuring it meets performance and security requirements) and runs it against the data stored by the Base Indexer. This means you can trust the results as much as any on-chain computation – the custom logic runs in a decentralized canister, producing deterministic outputs. Developers have full flexibility to incorporate existing libraries and complex math in their Rust logic​, making Chainsight’s data pipeline highly composable and extensible.

For example, you might use an Advanced Indexer to compute a moving average, an index composed of multiple asset prices, or a risk metric derived from the base data. Below are a few sample Rust snippets demonstrating the kinds of calculations an Advanced Indexer can perform:

```rust
// 1. Time-Weighted Average Price (TWAP) calculation over a series of prices
fn calculate_twap(prices: &[f64]) -> f64 {
    let sum: f64 = prices.iter().sum();
    sum / (prices.len() as f64)  // simple average (equal time weights for each price)
}
```

The above function takes a slice of price data (e.g. prices collected each minute over the last hour) and returns the average price. In practice, the Advanced Indexer’s logic would fetch the last N price points from the Base Indexer (say, the last 60 minutes of data) and feed them into this function to compute a 1-hour TWAP.

```rust
// 2. Volatility calculation (Realized Volatility over a period, e.g. daily RVOL)
use primitive_types::U256;

fn calc_realized_volatility(prices: Vec<U256>) -> f64 {
    let mut squared_returns: Vec<f64> = Vec::new();
    // [1] Calculate log returns for each consecutive price pair
    for i in 0..prices.len() - 1 {
        let pt = prices[i + 1].as_u128() as f64;
        let pt_minus_1 = prices[i].as_u128() as f64;
        let r = (pt / pt_minus_1).ln() * 100.0;
        squared_returns.push(r * r);
    }
    // [2] Compute average of squared returns, then take square root (std deviation)
    let avg_squared = squared_returns.iter().sum::<f64>() / (squared_returns.len() as f64);
    (avg_squared).sqrt() * (squared_returns.len() as f64).sqrt()
}
```

This function computes realized volatility from a vector of prices (here using `U256` for big integer prices). It calculates the log return between each consecutive price point, squares those returns, then computes the square root of the average squared return. The final multiplication by √N (where N is the number of returns) scales the result to the desired time window. For example, if the input prices are hourly and you compute over 24 hours, multiplying by √24 annualizes the daily volatility. In code form, this matches the standard formula for realized volatility. Using an Advanced Indexer, you could run this logic daily to produce a rolling volatility indicator on-chain.

```rust
// 3. Category Index creation (e.g., an index aggregating multiple asset prices)
fn calc_index(prices: &[f64], weights: &[f64]) -> f64 {
    // Compute weighted average of the asset prices
    prices.iter()
          .zip(weights.iter())
          .map(|(price, w)| price * w)
          .sum::<f64>()
}
```

In this snippet, `prices` might be a list of current prices for a set of assets (e.g. all tokens in a sector) and `weights` is a corresponding list of weights for each asset (for example, based on market capitalization or a fixed allocation). The function returns the weighted sum of the prices, which represents a composite index value. An Advanced Indexer can use such logic to maintain a **custom market index** (like a DeFi index or a “Chainsight 20” crypto index) by periodically pulling the latest prices of all components from Base Indexers and updating the index value.

Beyond these examples, Advanced Indexers can be programmed for virtually any aggregation or analysis. For instance, one could compute risk metrics like **Value at Risk (VaR)** by processing a distribution of returns, create composite **asset ratings** by combining volatility, liquidity, and other factors, or perform cross-asset analytics such as correlation between different price feeds. All such computations run on-chain in a verifiable manner, leveraging the historical data stored by the Base Indexer. This ability to deploy arbitrary analysis logic makes Chainsight’s oracle system extremely powerful for bespoke data synthesis and on-chain analytics.
