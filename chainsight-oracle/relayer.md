# Relayer

When pushing data from Chainsight to a target chain, you can set **sync conditions**:

* **Example**: `1hr / 3% deviation threshold`
  1. If the data changes by **3% or more** from the last update, the next transaction is triggered immediately (no need to wait an hour).
  2. If the data change is <3%, no update is sent until **1 hour** passes since the last update.
* **Effect**:
  * In times of high volatility, updates happen more frequently (to reflect rapid price changes).
  * In stable periods, you save on gas by updating only once per hour.
* **Cost–Performance Tradeoff**:
  * Tighter thresholds (like 1%) = more frequent updates, higher gas usage.
  * Looser thresholds or longer intervals = cheaper, but data might lag behind real-time conditions.
