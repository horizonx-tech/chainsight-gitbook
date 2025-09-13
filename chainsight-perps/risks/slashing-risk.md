# Slashing Risk

### What is Slashing?

Slashing is HIP-3's primary enforcement mechanism for ensuring builders maintain market integrity. When builders deploy perpetual markets on Hyperliquid, their 1 million HYPE stake serves as collateral that can be partially or fully slashed for protocol violations.

### Slashing Conditions

According to Hyperliquid's HIP-3 documentation, slashing may occur for:

* Oracle manipulation or prolonged oracle failure
* Malicious market parameter updates
* Failure to maintain required infrastructure
* Actions that compromise market integrity

### Impact on Traders

If ChainSight's stake is slashed:

* Markets may be paused or delisted
* Open positions would follow Hyperliquid's standard settlement procedures
* Traders maintain custody of their collateral in Hyperliquid's smart contracts

### Mitigation

ChainSight implements redundant oracle systems and monitoring infrastructure to prevent slashing events. However, traders should understand that builder slashing remains a protocol-level risk.

_For complete slashing parameters, refer to_ [_Hyperliquid's HIP-3 documentation_](https://hyperliquid.gitbook.io/hyperliquid-docs/hyperliquid-improvement-proposals-hips/hip-3-builder-deployed-perpetuals)
