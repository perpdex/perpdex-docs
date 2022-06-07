# Lossless AMM

The biggest fear of all makers when providing liquidity to earn passive income is impermanent loss.  PerpDEX offers a solution by introducing Lossless AMM.

### What is Impermanent Loss?

Impermanent loss (IL) happens when an investor provides assets as liquidity to an AMM-based exchange and the price of deposited assets changes as compared to when they were deposited. Crypto assets that have a volatile price are more prune to IL. On the other hand, assets that have less volatility i.e., stable coins or wrapped versions of a coin are fewer prunes to IL.&#x20;

### How does Impermanent Loss happen?

Let's say Alice wants to deposit some ETH and USDC in ETH/USDC pool. Also, let's assume the price of ETH during the deposit is 100 USDC. This pool only accepts an equivalent amount of both assets and the pool currently has 9 ETH and 900 USDC.  Alice proceeds to deposit 1 ETH and 100 USDC which evaluates to a total of $200 ($100 + $100). Adding this new liquidity will result in the pool having a total of 10 ETH and 1000 USDC now. Alice now holds a 10% share of the pool.

Let's say if the price of ETH rises to 400 USDC, the arbitrage traders will come in and balance out the price by putting in USDC and getting ETH at a lower price and making a profit until the price for ETH in the pool rises to 400 USDC. The liquidity in the pool remains constant (10,000) while the ratio of the two assets changes in the pool. This will result in 5 ETH and 2000 USDC in the pool.&#x20;

Alice has a share of 10% in the pool and now she wishes to withdraw her shares. She is entitled to have 0.5 ETH and 200 USDC totaling $400. As you can see, Alice initially deposited 1 ETH and 100 USDC totaling $200, she made a profit of $200 due to the price rise. But what if she never provided liquidity and simply hold her 1 ETH and 100 USDC, that would sum up to $500, right? This difference is known as Impermanent Loss.&#x20;

### How does PerpDEX solve Impermanent Loss?

PerpDEX is inteligent when it comes to IL. PerpDEX offers a solution to such problems with the introduction of Lossless AMM. Instead of bearing loss on the maker side, Lossless AMM calculates the virtual impermanent loss prior to conducting the actual transaction and distributes that difference to each transaction during the swap process and that becomes part of the transaction fee. The maker never suffers an impermanent loss while the overall portfolio is kept maintained.

###
