---
description: Why Chainsight Is Cheaper and More Flexible
---

# Overview

### **Network Effect for Reusing Indexed Data**

Chainsight indexes the data once, allowing multiple projects to reuse it. For example, if one project sets up a particular price feed, any other user can tap into the same feed with minimal overhead. As more data sets and users appear, the administrative cost per project **drops**, unlike a typical “1:1 oracle feed” scenario.

### **Direct Crypto Signing to Each Chain**

Rather than funneling transactions through a custom “bridge,” Chainsight’s distributed node network uses **chain-key cryptography** (backed by threshold ECDSA). Each node collectively signs updates for the target chain’s oracle contract. This means:

* No reliance on a single bridging operator or separate bridging contract.
* Lower trust assumptions: the cryptographic security is shared among distributed nodes.
