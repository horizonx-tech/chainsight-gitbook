---
description: Are the asset well distributed?
---

# Demo1: Decentralization Assessment

In this demo, we showcase the decentralized degree of token holders using the Herfindahl-Hirschman Index (HHI). A link to the demo will be available soon.

HHI is a widely-used economic indicator that measures a firm's size relative to its industry, quantifying the degree of competition among firms. This metric can also be applied to assess asset holder diversity, where $$s_{n}$$ represents the market share percentage of holder n as a whole number:&#x20;

$$
HHI = s_{1}^{2} + s_{2}^{2} + s_{3}^{2} + ... + s_{n}^{2}
$$

Many tokens exist, but not all are suitable for use as a collateralized asset. For example, tokens with significant allocation biases towards issuers or investors could experience significant price crashes based on the opinions of a few holders. These tokens should not be used as collateral in financial applications. By providing a validator using HHI, on-chain applications can dynamically determine if a token meets quantitative criteria concerning holder decentralization.

The figure below is a flow diagram illustrating how the Indexer and Relayer work together to obtain DAI's HHI-score.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-26 at 11.11.18.png" alt=""><figcaption><p>Dynamic HHI-score calculation flow</p></figcaption></figure>

In this case, we collect DAI data for both Ethereum and Optimism.

First, we index DAI's Transfer events to track past transactions. This raw data is represented by the green diagram. Then, the Algorithm Indexer, represented as the red object, maps which address holds DAI and to what extent in each network. The raw data represented as green cannot tell us each address's balance. The pink object, which is the Algorithm Lens of HHI logic, calculates a dispersion score based on balance biases in each network.

For example, assuming that the total DAI issuance on Ethereum is 100, where 20 tokens are distributed to 5 persons each, and where 20, 20, and 10 DAI on Optimism are distributed to 3 persons each, the values of HHI are as follows:

$$
HHI_{1} = \left({\frac {20} {100}}\right)^2 \times 5 = 0.2
$$

$$
HHI_{2} = \left({\frac {50} {100}}\right)^2 + \left({\frac {30} {100}}\right)^2 + \left({\frac {20} {100}}\right)^2  = 0.38
$$

In this case, HHI1 < HHI2 can be quantitatively determined that HHI1 is relatively more well-distributed. Since these values are constantly changing in response to DAI transactions, the changes over time are stored as time-series data by the Snapshot Indexer, represented by the yellow object. Finally, the Relayer, which is the purple object, carries this value to Polygon, allowing smart contracts on Polygon to dynamically know the HHI value.

#### Cost Estimation

As of April 23, 2023, DAI has approximately 17.2 million Transfer records on Ethereum and 9.1 million records on Optimism. The cost of synchronization for Ethereum is about $50, and for Optimism, it's about $35. With the Interval setting synchronizing the latest block once an hour, the daily running cost is approximately $0.xxx. However, once someone synchronizes an Indexer, referencing that Indexer is free, so not everyone needs to pay this cost each time they want to use the data.
