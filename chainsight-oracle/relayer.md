# Relayer

Once data has been indexed (and optionally processed by an Advanced Indexer), the next step is to deliver it to a target blockchain (e.g. Ethereum, BSC, etc.). The Relayer component handles this by packaging the latest data and sending a transaction to the on-chain Oracle contract. Notably, Chainsight’s Relayer uses a decentralized signing approach to ensure trustless delivery.

\[TBD: DEMO VIDEO HERE]



**Deviation Threshold Filter:** The Relayer allows configuration of update conditions to avoid unnecessary on-chain transactions. One common setting is a _deviation threshold_ – for example, “**1hr / 3% deviation**.” This means:

1. If the data value changes by **3% or more** since the last on-chain update, the Relayer will trigger a new update immediately (no need to wait the full hour)​.
2. If the data change is **less than 3%**, then no update is sent until at least **1 hour** has elapsed since the last update​.

The effect of such a filter is that during periods of high volatility, updates happen more frequently to reflect rapid changes, while in stable periods, the system skips small changes and only updates once per hour. This saves on gas fees by not pushing insignificant updates​. In other words:

* Tighter thresholds (e.g. _1% or a shorter interval_) result in more frequent updates and higher gas costs (better fidelity to real-time data).
* Looser thresholds (e.g. _5% or a longer interval_) result in fewer updates (lower cost) but data that might lag more behind real-time conditions​.



**Bug Rate Filter:** In addition to deviation thresholds, you can insert custom logic to filter out abnormal or spurious data updates. A "bug rate" filter is a concept where the Relayer checks data quality or consistency before pushing an update. For instance, if the incoming data has too many anomalies or errors in a short span, the Relayer might skip or delay updates until the data stabilizes. This prevents propagating faulty data on-chain. Here’s a simple example in Rust of a filter that drops outlier values:

```rust
fn should_update(new_value: f64, historical: &[f64], k: f64) -> bool {
    let mu = mean(historical);
    let sigma = std_dev(historical, mu);
    let lower_bound = mu - k * sigma;
    let upper_bound = mu + k * sigma;
    println!(
        "Using k = {}: mean = {:.2}, std_dev = {:.2}, acceptable range = [{:.2}, {:.2}]",
        k, mu, sigma, lower_bound, upper_bound
    );
    // Accept the new value if it falls within the range.
    new_value >= lower_bound && new_value <= upper_bound
}

fn mean(data: &[f64]) -> f64 {
    data.iter().sum::<f64>() / data.len() as f64
}

fn std_dev(data: &[f64], data_mean: f64) -> f64 {
    let variance = data.iter().map(|&x| (x - data_mean).powi(2)).sum::<f64>() / (data.len() as f64 - 1.0);
    variance.sqrt()
}
```

In this snippet, `should_update` compares the new value to the average of recent values. If it’s wildly off (here, more than 50% higher or lower than the mean of the last few data points), it treats it as a potential error and returns false (meaning the Relayer would not send this update). In practice, such filters could be more sophisticated – e.g. tracking consecutive failures or using standard deviation thresholds – but the goal is to **prevent glitchy data (“bugs”) from triggering on-chain updates**. By filtering out extreme anomalies or erroneous readings, Chainsight ensures the oracle only relays meaningful, accurate data.



**Threshold Signature Details:** To ensure trustless operation, the Relayer uses a threshold signature scheme when sending transactions. Rather than a single server signing the update transaction, multiple nodes using in Chainsight cooperatively sign it using threshold ECDSA cryptography. Essentially, the private key for the target chain’s oracle account is **sharded among the nodes**, and they produce a signature together – no single node ever possesses the full key. The final signed transaction is then broadcast to the EVM chain, calling `updateStateByKey(...)` on the Oracle contract. No external bridging contract is required, as the node network “natively” signs an Ethereum-compatible transaction​. This design eliminates any single point of failure in the data relay process: even if some nodes fail or a subset is compromised, the remaining honest nodes can still generate a valid signature (as long as a threshold quorum is met). In effect, the Chainsight network itself acts as a distributed oracle signer, providing a very high level of security and decentralization for cross-chain data updates​.
