# Demo4: Malicious Address Tracker

This demo introduces the address checker, which tracks down addresses behaving miraculously.

The U.S. Department of the Treasury released multiple pieces of the latest OFAC sanctions information involving multiple Ethereum, ARB, BSC, and other cryptocurrency addresses.

{% embed url="https://ofac.treasury.gov/recent-actions/20230424" %}

We can track addresses that have received funds over a certain amount from the addresses listed here and repeat the process to update the list of tainted addresses to see where the illicit funds are flowing. This can be used to incorporate dynamic validation into a smart contract so that fraudulent addresses can restrict access to it so they cannot use it. This would be important in DeFi, such as Tornade Cash.
