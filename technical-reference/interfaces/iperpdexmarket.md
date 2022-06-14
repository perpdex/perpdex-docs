# IPerpdexMarket

PerpDEX Market Interface allows tracking a few market aspects.

## Functions

### symbol

```
function symbol() external view returns (string memory)
```

Returns the symbol of the market.

**Return Values:**

| Type   | Description                        |
| ------ | ---------------------------------- |
| string | Symbol of the market, i.e., BTCUSD |



### exchange

```
function exchange() external view returns (address)
```

Returns the exchange address to which the market belongs to. Exchange is immutable and can only be set via the constructor.&#x20;

**Return Values:**

| Type    | Description                                          |
| ------- | ---------------------------------------------------- |
| address | Smart contract address of deployed PerpDEX Exchange. |



### getMarkPriceX96

```
function getMarkPriceX96() external view returns (uint256)
```

Returns the mark price of a pair based on the current base and quote amount in the market pool.

**Return Values:**

| Type    | Description         |
| ------- | ------------------- |
| uint256 | Mark price of pair  |



## Events

### FundingPaid

```
event FundingPaid(
    int256 fundingRateX96,
    uint32 elapsedSec,
    int256 premiumX96,
    uint256 markPriceX96,
    uint256 cumBasePerLiquidityX96,
    uint256 cumQuotePerLiquidityX96
)
```

Emitted when funding payment is processed during swap or liquidity operation.

**Parameters:**

| Name                    | Type    | Description                                                 |
| ----------------------- | ------- | ----------------------------------------------------------- |
| fundingRateX96          | int256  | Calculated funding rate in Q64.96                           |
| elapsedSec              | uint32  | Time elapsed since the last funding was paid                |
| premiumX96              | int256  | Premium paid in this funding payment in Q64.96              |
| markPriceX96            | uint256 | Mark price of the market assets in Q64.96                   |
| cumBasePerLiquidityX96  | uint256 | Cumulative base amount per liquidity share in Q64.96        |
| cumQuotePerLiquidityX96 | uint256 | Cumulative quote amount share per liquidity share in Q64.96 |

### LiquidityAdded

```
event LiquidityAdded(
    uint256 base, 
    uint256 quote, 
    uint256 liquidity
)
```

Emitted when liquidity is added to the market.

**Parameters:**

| Name      | Type    | Description                                  |
| --------- | ------- | -------------------------------------------- |
| base      | uint256 | The base amount of pair added in liquidity   |
| quote     | uin256  | The quoted amount of pair added in liquidity |
| liquidity | uint256 | Liquidity share minted                       |

### LiquidityRemoved

```
event LiquidityRemoved(
    uint256 base,
    uint256 quote,
    uint256 liquidity
)
```

Emitted when liquidity is removed from the market.

**Parameters:**

| Name      | Type    | Description                                     |
| --------- | ------- | ----------------------------------------------- |
| base      | uint256 | The base amount of pair removed from liquidity  |
| quote     | uint256 | The quote amount of pair removed from liquidity |
| liquidity | uint256 | Liquidity shares burned                         |

### **Swapped**

```
event Swapped(
    bool isBaseToQuote, 
    bool isExactInput, 
    uint256 amount, 
    uint256 oppositeAmount
)
```

Emitted when a trade happens i.e., open position or close position in any market direction.

**Parameters:**

| Name           | Type    | Description                                                                                               |
| -------------- | ------- | --------------------------------------------------------------------------------------------------------- |
| isBaseToQuote  | bool    | True if swap is done from base token to quote token which is short and vice-versa.                        |
| isExactInput   | bool    | True if input amount also includes fee in it, otherwise false.                                            |
| amount         | uint256 | Collateral amount used in swap. It will be base in short and quote in long.                               |
| oppositeAmount | uint256 | The corresponding opposite amount of swap. If amount is base then oppositeAmount is quote and vice-versa. |
