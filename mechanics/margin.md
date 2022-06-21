---
description: Margin ratio and PnL
---

# Margin

There are two different margin ratios to keep track of.&#x20;

* Initial Margin Ratio
* Maintenance Margin Ratio

### Initial Margin Ratio

The initial margin ratio is the ratio of margin required to increase a position or open a position. If an account doesn't have enough initial margin ratio, the trader won't be able to open a new position. The initial margin ratio is set to **10%**. This means that an account needs to have at least 10% of free margin to open a position. The initial margin ratio can be calculated by

$$
IMR=1/Maximum Leverage
$$

For maximum leverage of 10x, the initial margin ratio calculated is 1/10=10%.

### Maintenance Margin Ratio

The maintenance margin ratio is the required margin ratio below which an account could be liquidated. This helps stop the spread of losses from a bad trade. By default, the maintenance margin ratio in PerpDEX is set to **5%**. This means if an account has a leverage of 1/5%=20x, the account will be liquidated by the liquidator.
