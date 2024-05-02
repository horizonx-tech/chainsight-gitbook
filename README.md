---
description: Indexes on-chain data and makes it widely available
---

# Introduction

Welcome to Chainsight - an on-chain data hub that can be integrated with smart contracts.

### Various data can now be accessed from smart contracts

<figure><img src=".gitbook/assets/Screenshot 2024-04-24 at 18.43.17.png" alt=""><figcaption></figcaption></figure>

Chainsight allows you to access various data from your smart contracts, such as volatility based on historical data, RWA price feeds, and a customizable crypto market index (Chainsight20). These data can be accessed from any blockchain, and with the Chainsight CLI, you can index any data you need yourself. Please contact our [X account](https://twitter.com/Chainsight\_) if you need any help.



### Stablecoin Rating

Quantitative analysis of stablecoins from on-chain data that is updated daily. For example, it evaluates six indicators as time-series data, including how close it moves from $1, how quickly it recovers when it deviates from $1, and the degree to which a user is a price taker.

<figure><img src=".gitbook/assets/Screenshot 2024-05-01 at 15.22.12.png" alt=""><figcaption></figcaption></figure>

These rating results are available from on-chain apps, which means you can write dynamic logic based on the rating information.

Academic paper: [https://drive.google.com/file/d/1xuwyY9KmAGaTYNmlqvk27XNsZAINe04A/view?usp=sharing](https://drive.google.com/file/d/1xuwyY9KmAGaTYNmlqvk27XNsZAINe04A/view?usp=sharing)



### Cost-effective due to Data LEGO

<figure><img src=".gitbook/assets/Screenshot 2024-04-24 at 21.17.09.png" alt=""><figcaption></figcaption></figure>

Let's first assume that the green components are deployed on Chainsight: the Daily Volatility Calculator is used to calculate volatility based on historical data for the three Stablecoins. After scoring this through a separate logic for Rating, your smart contract can use this result.&#x20;

If you want to create a different Rating based on the Volatility information, you can rebuild it using a separate blue component (Rating B). The green component can be reused. Similarly, if you want to change the definition of Volatility, you can add red components (Monthly Volatility Calculator & Rating C). If someone else has registered the data you need, you can just reuse it.



### Custom Dashboard to view your data

<figure><img src=".gitbook/assets/Screenshot 2024-04-24 at 21.50.14.png" alt=""><figcaption></figcaption></figure>

The Chainsight UI allows you to view and check the data deployed on Chainsight. The panels for viewing data are customizable, allowing you to add any information you wish to your own dashboard.



### Easy steps to create new data

<figure><img src=".gitbook/assets/Screenshot 2024-04-24 at 21.56.50.png" alt=""><figcaption></figcaption></figure>

By specifying any data source from the UI, you can deploy the data you need on Chainsight. The UI is currently only available to Early Access Users; if you want to try, please apply for Early Access Users from [here](https://twitter.com/Chainsight\_/status/1767584718567133363).

You can also deploy more complex data logic using the Chainsight CLI. Please see the [README](https://github.com/horizonx-tech/chainsight-cli) for details.



***

Please follow us below and wait for more updates!

Early Access: [https://forms.gle/hEkeUZfNMgsubQvt6](https://forms.gle/hEkeUZfNMgsubQvt6)

X Account: [https://twitter.com/Chainsight\_](https://twitter.com/Chainsight\_)
