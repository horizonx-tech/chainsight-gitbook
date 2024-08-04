# Price Feed

Chainsight has a function to distribute crypto asset price information to a designated network in a cost-effective manner. This is made possible through [Chainkey Cryptography](https://support.dfinity.org/hc/en-us/articles/360057605551-What-is-chain-key-cryptography), which enables transactions to be directly written from a distributed node to a designated chain without the need for a specific bridge to be secure.

### Why is Chainsight more affordable than other oracle providers?

Chainsight can offer lower costs compared to other oracle providers due to its network architecture. Once data and logic are indexed on Chainsight, they can be reused multiple times. Thus, as the number of users increases, the administration costs per project decrease due to the network effect.

### How is data securely synchronized from various data sources?

Chainsight indexes data using either way:

1. Consensus with multiple calls\
   Data is indexed by reaching consensus on the results of a GET request sent from a distributed node to the endpoint providing the price data. While this method supports a wide range of data sources, it requires time to wait for consensus for a few seconds.
2. Real-time push with proofs\
   Chainsight is working with [Usher Labs](https://www.usher.so/) to push data to Chainsight in real-time with proofs that the data has not been manipulated. While this method has a limited range of supported data, it is beneficial for real-time data work as no waiting for consensus is necessary.

### Where does the data come from?

Upon user request, the data source can be specified. The recommended option is to obtain synthetic rates from multiple exchanges, such as through CoinGecko. For other minor assets, price data can be obtained from a specified decentralized exchange (DEX) and provided as a time-weighted average price (TWAP).

### Supported networks.

The current supported networks are listed at&#x20;

{% embed url="https://github.com/horizonx-tech/chainsight-management-oracle/blob/main/README.md#chainsight-management-oracle" %}

If you would like to use an oracle on a network not listed, please make a request using the form below.&#x20;

Form: [https://forms.gle/yowZtEtCxXs8g2xDA](https://forms.gle/yowZtEtCxXs8g2xDA)
