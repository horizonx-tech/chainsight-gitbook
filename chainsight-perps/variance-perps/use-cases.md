# Use Cases

### How Market Participants Use Variance Perpetuals

Variance perpetuals serve distinct purposes across the trading ecosystem. From active traders capturing volatility regime changes to protocols hedging treasury risk, VAR-BTC and VAR-ETH unlock strategies previously impossible on-chain.

_Note: All volatility figures referenced are annualized percentages unless otherwise specified._

***

### Traders

#### The Volatility Regime Trader

**Strategy:** Capitalize on mean reversion in realized volatility\
**Context:** Bitcoin 30-day realized volatility historically ranges from 30% to 70% annualized, with 50% representing only 5% of historical observations\
**Execution:** Position based on percentile rankings rather than absolute levels

**Example Position:**

* BTC 30-day realized vol at 35% (10th percentile historically)
* Historical mean reversion suggests movement toward 50-60% range
* Long VAR-BTC with 2-3x leverage maximum (variance products are already leveraged to volatility squared)
* Target: 50% realized vol
* Risk management: Size at 2-5% of portfolio given convex payoff structure

#### The Event Volatility Specialist

**Strategy:** Pre-position for binary events where implied volatility systematically underprices realized movement\
**Execution:** Enter 48-72 hours before catalyst when IV/RV spread is narrowest\
**Edge:** Works best when term structure is in backwardation

**High-Probability Events:**

* FOMC meetings with dot plot updates (average RV spike: +12-15 percentage points)
* Major protocol upgrades (Ethereum Merge saw RV move from 45% to 85%)
* Regulatory decisions (ETF approvals typically +20pp RV movement)
* Quarterly earnings from crypto-exposed companies (MSTR, COIN)

#### Correlation Regime Trading

**Strategy:** Trade VAR-BTC vs VAR-ETH spread based on correlation regimes\
**Execution:** During risk-off periods, correlations increase, compressing volatility differentials\
**Edge:** Capture decorrelation as market regimes normalize

***

### Market Makers

#### Variance Risk Premium Harvesting

**Strategy:** Systematic short variance with dynamic hedging\
**Mechanism:** Capture the structural premium between implied and realized volatility

**Implementation:**

* Variance Risk Premium averages +15 points when term structure in contango
* Short VAR positions capture VRP over time
* Hedge tail risk with far OTM options
* Adjust position size based on term structure regime

**P\&L Attribution:**

* VRP capture: +15% annualized (historical average)
* Funding costs: -3-5% (depends on market regime)
* Net expected return: +10-12% before tail events

#### Cross-Product Arbitrage

**Strategy:** Trade variance perp vs replicating portfolio of options\
**Execution:** Exploit pricing discrepancies between synthetic and direct variance exposure

**Implementation:**

* Calculate theoretical variance swap rate from options chain using log-contract methodology
* If VAR-BTC trades rich to replication cost, sell VAR and buy option strip
* Manage bid-ask spread costs through patient execution
* Monitor for convergence opportunities during high volume periods

#### Volatility Dispersion Trading

**Strategy:** Trade index volatility vs constituent volatility\
**Execution:** Long VAR on individual assets, short basket variance when available\
**Edge:** Correlation breakdown creates alpha opportunities

***

### Treasuries & Funds

#### Protocol Treasury Hedging

**Problem:** Native token treasuries face sqrt(N) volatility drag\
**Solution:** Convexity-adjusted variance hedging

**Implementation for $100M Treasury:**

* Calculate treasury beta to BTC/ETH (typically 1.2-1.5x for DeFi tokens)
* Size variance position at 2-3% notional
* During low vol (<40%): Cost averages 40-60bps monthly
* During vol spikes (>70%): Hedge gains can offset 15-25% of treasury drawdown

**Benefits:**

* No need to sell native tokens
* Transparent hedging visible on-chain
* Lower cost than rolling options over time

#### Crypto Fund Risk Overlays

**Strategy:** Add volatility component to traditional long-only crypto portfolios\
**Implementation:** Strategic allocation to long variance as portfolio insurance

**Portfolio Construction:**

* 70% Core positions (BTC, ETH, SOL)
* 20% Satellite positions (selected alts)
* 7% Stable yield strategies
* 3% VAR-BTC/VAR-ETH long as volatility buffer

**Performance Impact:**

* Reduces max drawdown by 15-20%
* Minimal drag during trending markets
* Significant protection during regime changes

#### Structured Product Creation

**Product:** "Volatility Buffer Note"\
**Target:** Institutional allocators seeking volatility exposure with downside protection

**Mechanics:**

* 95% in yield-generating stables
* 5% rolling long variance exposure
* Expected return: Base yield + 0.3x volatility beta
* Marketed as volatility overlay strategy

***

### Ecosystem

#### Lending Protocol Risk Management

**Use Case:** Systemic risk buffer for extreme volatility events\
**Implementation:** Dynamic parameter adjustment based on realized volatility

**Risk Framework:**

* Monitor 7-day realized vol via VAR products
* When VAR > 60%: Reduce max LTVs by 10%
* When VAR > 80%: Pause new loans on volatile collateral
* Resume normal parameters when VAR < 50% for 48 hours

#### Perpetual DEX Dynamic Margin

**Use Case:** Adjust leverage limits based on market volatility regime\
**Implementation:** Automated risk parameters tied to VAR levels

**Margin Schedule:**

* VAR-BTC 30-50%: Standard margins (2% initial, 1% maintenance)
* VAR-BTC 50-70%: Increase initial margin by 50%
* VAR-BTC >70%: Double initial margins, reduce max leverage to 10x

#### Cross-Protocol Strategies

**Use Case:** Composable strategies leveraging variance data\
**Example:** Volatility-adjusted yield farming

**Strategy Flow:**

1. Monitor VAR-ETH levels continuously
2. When VAR < 35: Deploy to high-risk/high-yield farms
3. When VAR > 55: Rotate to stable pools
4. Use VAR profits during transitions to cover switching costs

***

_Disclaimer: Position sizes and return estimates based on historical analysis of Bitcoin and Ethereum markets 2019-2024. Past performance does not guarantee future results. Variance products carry substantial risk of loss._
