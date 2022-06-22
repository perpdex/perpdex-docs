# LFF (Liquidation Free Funding)

Many traders in the realm of perpetual futures trading have gone high risks to achieve more but not all succeeded to get there. PerpDEX brings good news to all those risk-takers by introducing a new mechanism called **LFF** (Liquidation Free Funding). With LFF, the rewards accumulated over time via funding payment are added to your base tokens instead of quote tokens. Since your position has a direct effect only on quote tokens, and in case that trade was a bad trade, all funds in quote tokens would be liquidated but since you also accumulated rewards during the trade, you still have those reward tokens.&#x20;

Simply put, in case of liquidation, the rewards you accumulated during the trade won’t be liquidated with the rest of your quote tokens and hence protect you from complete liquidation. This saves you all of that passive income you made during the trade and can be utilized again to start your new high-risk/reward journey.

This can be achieved if the base token is treated as rebase token, which is, to adjust its circulating supply as the funding rate changes. The following equation shows how to adjust the total supply of base tokens with the change in funding rate and base token balance of an individual.



$$
TotalSupply_{BaseToken}(t+1)=TotalSupply_{BaseToken}(t)*(1-fundingRate)
$$

$$
Balance_{BaseToken}=TotalSupply_{BaseToken}(t)*Shares_{BaseToken}
$$

The total supply of base tokens will increase when the funding rate is negative, while the total supply will decrease when the funding rate is positive.
