# Funding Rate

Since, trade for a common perpetual future i.e., BTC/USD could be happening at so many different exchanges, a price divergence could happen due to different markets and their supply & demand in that specific market platform. In order to cover those price differences and make them in line in all of these scattered markets, a process called **funding payment** is introduced. Funding payments help converge the prices of futures assets to an index/mark price.&#x20;

PerpDEX calculates the price difference to distribute funding payments every hour of the day. If there's a positive funding rate, long position holders will pay and short position holders will receive, and vice-versa.

The funding rate is calculated via the following equation

$$
FundingRate=premium *  \left (\frac {timeElapsed} {rolloverPeriod}\right)
$$
