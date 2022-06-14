# IPerpdexExchange

## Structs

### AddLiquidityParams

```
struct AddLiquidityParams {
    address market;
    uint256 base;
    uint256 quote;
    uint256 minBase;
    uint256 minQuote;
    uint256 deadline;
}
```

Data structure used to input parameters for AddLiquidity function. These attributes are used to add liquidity to the liquidity pool of a market at PerpDEX.

**Attributes:**

| Name     | Type    | Description                                              |
| -------- | ------- | -------------------------------------------------------- |
| market   | address | Market address where liquidity is added                  |
| base     | uint256 | Amount of base token to added                            |
| quote    | uint256 | Amount of quote token to added                           |
| minBase  | uint256 | Minimum base token amount that should be added           |
| minQuote | uint256 | Minimum quote token amount that should be added          |
| deadline | uint256 | Time deadline before which the liquidity should be added |

### RemoveLiquidityParams

```
struct RemoveLiquidityParams {
    address trader;
    address market;
    uint256 liquidity;
    uint256 minBase;
    uint256 minQuote;
    uint256 deadline;
}
```

Data structure to input parameters to RemoveLiquidity function. These attributes are used to remove liquidity from the liquidity pool of a market at PerpDEX.

**Attributes:**

| Name      | Type    | Description                                                 |
| --------- | ------- | ----------------------------------------------------------- |
| trader    | address | Address of user whose liquidity is to be removed            |
| market    | address | Address of market from which liquidity is to be removed     |
| liquidity | uint256 | Amount of liquidity share to be removed                     |
| minBase   | uint256 | Minimum base token amount that should be received by trader |
| minQuote  | uint256 | Minimum quote token amoun that should be received by trader |
| deadline  | uint256 | Time dealine before which liquidity should be removed       |

### TradeParams

```
struct TradeParams {
    address trader;
    address market;
    bool isBaseToQuote;
    bool isExactInput;
    uint256 amount;
    uint256 oppositeAmountBound;
    uint256 deadline;
}
```

Data structure to input parameters to trade function. These are used to open a position in PerpDEX.

**Attributes:**

| Name                | Type    | Description                                                                         |
| ------------------- | ------- | ----------------------------------------------------------------------------------- |
| trader              | address | Address of user who wants to trade                                                  |
| market              | address | Address of market in which user will trade                                          |
| isBaseToQuote       | bool    | True if swap is done from base token to quote token which is short and vice-versa.  |
| isExactInput        | bool    | True if input amount also includes fee in it, otherwise false.                      |
| amount              | uint256 |                                                                                     |
| oppositeAmountBound | uint256 |                                                                                     |
| deadline            | uint256 | Time dealine before which trade should execute                                      |

### PreviewTradeParams

```
struct PreviewTradeParams {
    address trader;
    address market;
    address caller;
    bool isBaseToQuote;
    bool isExactInput;
    uint256 amount;
    uint256 oppositeAmountBound;
}
```

Data structure to input parameters to previewTrade function. This function does not execute trade itself but makes all required calculations.

**Attributes:**

| Name                | Type    | Description                                                                         |
| ------------------- | ------- | ----------------------------------------------------------------------------------- |
| trader              | address | Address of user used to preview trade against.                                      |
| market              | address | Address of market in which trade will be previewed                                  |
| caller              | address | The actual caller of function                                                       |
| isBaseToQuote       | bool    | True if swap is done from base token to quote token which is short and vice-versa.  |
| isExactInput        | bool    | True if input amount also includes fee in it, otherwise false.                      |
| amount              | uint256 |                                                                                     |
| oppositeAmountBound | uint256 |                                                                                     |

### MaxTradeParams

```
struct MaxTradeParams {
    address trader;
    address market;
    address caller;
    bool isBaseToQuote;
    bool isExactInput;
}
```

DESCRIPTION

**Attributes:**

| Name          | Type    | Description |
| ------------- | ------- | ----------- |
| trader        | address |             |
| market        | address |             |
| caller        | address |             |
| isBaseToQuote | bool    |             |
| isExactInput  | bool    |             |



## Functions

### deposit

```
function deposit(
    uint256 amount
) external payable
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| amount | uint256 |             |

### withdraw

```
function withdraw(
    uint256 amount
) external
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| amount | uint256 |             |

### transferInsuranceFund

```
function transferInsuranceFund(
    uint256 amount
) external
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| amount | uint256 |             |

### transferProtocolFee

```
function transferProtocolFee(
    uint256 amount
) external
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| amount | uint256 |             |

### addLiquidity

```
function addLiquidity(
      AddLiquidityParams calldata params
  ) external returns (
      uint256 base,
      uint256 quote,
      uint256 liquidity
)
```

DESCRIPTION

**Parameters:**

| Name   | Type               | Description |
| ------ | ------------------ | ----------- |
| params | AddLiquidityParams |             |

**Return values:**

| Name      | Type    | Description |
| --------- | ------- | ----------- |
| base      | uint256 |             |
| quote     | uint256 |             |
| liquidity | uint256 |             |

### removeLiquidity

```
function removeLiquidity(
    RemoveLiquidityParams calldata params
) external returns (
    uint256 base, 
    uint256 quote
)
```

DESCRIPTION

**Parameters:**

| Name   | Type                  | Description |
| ------ | --------------------- | ----------- |
| params | RemoveLiquidityParams |             |

**Return values:**

| Name  | Type    | Description |
| ----- | ------- | ----------- |
| base  | uint256 |             |
| quote | uint256 |             |

### trade

```
function trade(
    TradeParams calldata params
) external returns (
    uint256 oppositeAmount
)
```

DESCRIPTION

**Parameters:**

| Name   | Type        | Description |
| ------ | ----------- | ----------- |
| params | TradeParams |             |

**Return values:**

| Name           | Type    | Description |
| -------------- | ------- | ----------- |
| oppositeAmount | uint256 |             |

### setMaxMarketsPerAccount

```
function setMaxMarketsPerAccount(
    uint8 value
) external
```

DESCRIPTION

**Parameters:**

| Name  | Type  | Description |
| ----- | ----- | ----------- |
| value | uint8 |             |

### setImRatio

```
function setImRatio(
    uint24 value
) external
```

DESCRIPTION

**Parameters:**

| Name  | Type   | Description |
| ----- | ------ | ----------- |
| value | uint24 |             |

### setMmRatio

```
function setMmRatio(
    uint24 value
) external
```

DESCRIPTION

**Parameters:**

| Name  | Type   | Description |
| ----- | ------ | ----------- |
| value | uint24 |             |

### setLiquidationRewardConfig

```
function setLiquidationRewardConfig(
    PerpdexStructs.LiquidationRewardConfig calldata value
) external
```

DESCRIPTION

**Parameters:**

| Name  | Type                    | Description |
| ----- | ----------------------- | ----------- |
| value | LiquidationRewardConfig |             |
|       |                         |             |
|       |                         |             |

### setProtocolFeeRatio

```
function setProtocolFeeRatio(
    uint24 value
) external
```

DESCRIPTION

**Parameters:**

| Name  | Type   | Description |
| ----- | ------ | ----------- |
| value | uint24 |             |

### setIsMarketAllowed

```
function setIsMarketAllowed(
    address market, 
    bool value
) external
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| market | address |             |
| value  | bool    |             |
|        |         |             |

### previewTrade

```
function previewTrade(
    PreviewTradeParams calldata params
) external view returns (
    uint256 oppositeAmount
)
```

DESCRIPTION

**Parameters:**

| Name   | Type               | Description |
| ------ | ------------------ | ----------- |
| params | PreviewTradeParams |             |

**Return values:**

| Name           | Type    | Description |
| -------------- | ------- | ----------- |
| oppositeAmount | uint256 |             |

### maxTrade

```
function maxTrade(
    MaxTradeParams calldata params
) external view returns (
    uint256 amount
)
```

DESCRIPTION

**Parameters:**

| Name   | Type           | Description |
| ------ | -------------- | ----------- |
| params | MaxTradeParams |             |

**Return values:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| amount | uint256 |             |

### accountInfos

```
function accountInfos(
    address trader
) external view returns (
    PerpdexStructs.VaultInfo memory
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| trader | address |             |

**Return values:**

| Name | Type      | Description |
| ---- | --------- | ----------- |
| -    | VaultInfo |             |

### insuranceFundInfo

```
function insuranceFundInfo() external view returns (
    int256 balance, 
    uint256 liquidationRewardBalance
)
```

DESCRIPTION

**Return values:**

| Name                     | Type    | Description |
| ------------------------ | ------- | ----------- |
| balance                  | int256  |             |
| liquidationRewardBalance | uint256 |             |

### protocolInfo

```
function protocolInfo() external view returns (
    uint256 protocolFee
)
```

DESCRIPTION

**Return values:**

| Name        | Type    | Description |
| ----------- | ------- | ----------- |
| protocolFee | uint256 |             |

### settlementToken

```
function settlementToken() external view returns (
    address
)
```

DESCRIPTION

**Return values:**

| Name | Type    | Description |
| ---- | ------- | ----------- |
| -    | address |             |

### quoteDecimals

```
function quoteDecimals() external view returns (
    uint8
)
```

DESCRIPTION

**Return values:**

| Name | Type  | Description |
| ---- | ----- | ----------- |
| -    | uint8 |             |

### maxMarketsPerAccount

```
function maxMarketsPerAccount() external view returns (
    uint8
)
```

DESCRIPTION

**Return values:**

| Name | Type  | Description |
| ---- | ----- | ----------- |
| -    | uint8 |             |

### imRatio

```
function imRatio() external view returns (
    uint24
)
```

DESCRIPTION

**Return values:**

| Name | Type   | Description |
| ---- | ------ | ----------- |
| -    | uint24 |             |

### mmRatio

```
function mmRatio() external view returns (
    uint24
)
```

DESCRIPTION

**Return values:**

| Name | Type   | Description |
| ---- | ------ | ----------- |
| -    | uint24 |             |

### liquidationRewardConfig

```
function liquidationRewardConfig() external view returns (
    uint24 rewardRatio, 
    uint16 smoothEmaTime
)
```

DESCRIPTION

**Return values:**

| Name          | Type   | Description |
| ------------- | ------ | ----------- |
| rewardRatio   | uint24 |             |
| smoothEmaTime | uint16 |             |

### protocolFeeRatio

```
function protocolFeeRatio() external view returns (
    uint24
)
```

DESCRIPTION

**Return values:**

| Name | Type   | Description |
| ---- | ------ | ----------- |
| -    | uint24 |             |

### isMarketAllowed

```
function isMarketAllowed(
    address market
) external view returns (
    bool
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| market | address |             |

**Return values:**

| Name | Type | Description |
| ---- | ---- | ----------- |
| -    | bool |             |

### getTakerInfo

```
function getTakerInfo(
    address trader, 
    address market
) external view returns (
    PerpdexStructs.TakerInfo memory
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| trader | address |             |
| market | address |             |

**Return values:**

| Name | Type      | Description |
| ---- | --------- | ----------- |
| -    | TakerInfo |             |

### getMakerInfo

```
function getMakerInfo(
    address trader, 
    address market
) external view returns (
    PerpdexStructs.MakerInfo memory
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| trader | address |             |
| market | address |             |

**Return values:**

| Name | Type      | Description |
| ---- | --------- | ----------- |
| -    | MakerInfo |             |

### getAccountMarkets

```
function getAccountMarkets(
    address trader
) external view returns (
    address[] memory
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| trader | address |             |

**Return values:**

| Name | Type       | Description |
| ---- | ---------- | ----------- |
| -    | address\[] |             |

### getTotalAccountValue

```
function getTotalAccountValue(
    address trader
) external view returns (
    int256
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| trader | address |             |

**Return values:**

| Name | Type   | Description |
| ---- | ------ | ----------- |
| -    | int256 |             |

### getPositionShare

```
function getPositionShare(
    address trader, 
    address market
) external view returns (
    int256
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| trader | address |             |
| market | address |             |

**Return values:**

| Name | Type   | Description |
| ---- | ------ | ----------- |
| -    | int256 |             |

### getPositionNotional

```
function getPositionNotional(
    address trader, 
    address market
) external view returns (
    int256
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| trader | address |             |
| market | address |             |

**Return values:**

| Name | Type   | Description |
| ---- | ------ | ----------- |
| -    | int256 |             |

### getTotalPositionNotional

```
function getTotalPositionNotional(
    address trader
) external view returns (
    uint256
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| trader | address |             |

**Return values:**

| Name | Type    | Description |
| ---- | ------- | ----------- |
| -    | uint256 |             |

### getOpenPositionShare

```
function getOpenPositionShare(
    address trader, 
    address market
) external view returns (
    uint256
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| trader | address |             |
| market | address |             |

**Return values:**

| Name | Type    | Description |
| ---- | ------- | ----------- |
| -    | uint256 |             |

### getOpenPositionNotional

```
function getOpenPositionNotional(
    address trader, 
    address market
) external view returns (
    uint256
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| trader | address |             |
| market | address |             |

**Return values:**

| Name | Type    | Description |
| ---- | ------- | ----------- |
| -    | uint256 |             |

### getTotalOpenPositionNotional

```
function getTotalOpenPositionNotional(
    address trader
) external view returns (
    uint256
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| trader | address |             |

**Return values:**

| Name | Type    | Description |
| ---- | ------- | ----------- |
| -    | uint256 |             |

### hasEnoughMaintenanceMargin

```
function hasEnoughMaintenanceMargin(
    address trader
) external view returns (
    bool
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| trader | address |             |

**Return values:**

| Name | Type | Description |
| ---- | ---- | ----------- |
| -    | bool |             |

### hasEnoughInitialMargin

```
function hasEnoughInitialMargin(
    address trader
) external view returns (
    bool
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| trader | address |             |

**Return values:**

| Name | Type | Description |
| ---- | ---- | ----------- |
| -    | bool |             |

****

****

## Events

### Deposited

```
event Deposited(
    address indexed trader, 
    uint256 amount
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| trader | address |             |
| amount | uint256 |             |

### Withdrawn

```
event Withdrawn(
    address indexed trader, 
    uint256 amount
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| trader | address |             |
| amount | uint256 |             |

### InsuranceFundTransferred

```
event InsuranceFundTransferred(
    address indexed trader, 
    uint256 amount
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| trader | address |             |
| amount | uint256 |             |

### ProtocolFeeTransferred

```
event ProtocolFeeTransferred(
    address indexed trader, 
    uint256 amount
)
```

DESCRIPTION

**Parameters:**

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| trader | address |             |
| amount | uint256 |             |

### LiquidityAdded

```
event LiquidityAdded(
    address indexed trader,
    address indexed market,
    uint256 base,
    uint256 quote,
    uint256 liquidity,
    uint256 cumBasePerLiquidityX96,
    uint256 cumQuotePerLiquidityX96,
    uint256 baseBalancePerShareX96,
    uint256 sharePriceAfterX96
)
```

DESCRIPTION

**Parameters:**

| Name                    | Type    | Description |
| ----------------------- | ------- | ----------- |
| trader                  | address |             |
| market                  | address |             |
| base                    | uint256 |             |
| quote                   | uint256 |             |
| liquidity               | uint256 |             |
| cumBasePerLiquidityX96  | uint256 |             |
| cumQuotePerLiquidityX96 | uint256 |             |
| baseBalancePerShareX96  | uint256 |             |
| sharePriceAfterX96      | uint256 |             |

### LiquidityRemoved

```
event LiquidityRemoved(
    address indexed trader,
    address indexed market,
    address liquidator,
    uint256 base,
    uint256 quote,
    uint256 liquidity,
    int256 takerBase,
    int256 takerQuote,
    int256 realizedPnl,
    uint256 baseBalancePerShareX96,
    uint256 sharePriceAfterX96
)
```

DESCRIPTION

**Parameters:**

| Name                   | Type    | Description |
| ---------------------- | ------- | ----------- |
| trader                 | address |             |
| market                 | address |             |
| liquidator             | address |             |
| base                   | uint256 |             |
| quote                  | uint256 |             |
| liquidity              | uint256 |             |
| takerBase              | int256  |             |
| takerQuote             | int256  |             |
| realizedPnL            | int256  |             |
| baseBalancePerShareX96 | uint256 |             |
| sharePriceAfterX96     | uint256 |             |

### PositionLiquidated

```
event PositionLiquidated(
    address indexed trader,
    address indexed market,
    address indexed liquidator,
    int256 base,
    int256 quote,
    int256 realizedPnl,
    uint256 protocolFee,
    uint256 baseBalancePerShareX96,
    uint256 sharePriceAfterX96,
    uint256 liquidationPenalty,
    uint256 liquidationReward,
    uint256 insuranceFundReward
)
```

DESCRIPTION

**Parameters:**

| Name                   | Type    | Description |
| ---------------------- | ------- | ----------- |
| trader                 | address |             |
| market                 | address |             |
| liquidator             | address |             |
| base                   | int256  |             |
| quote                  | int256  |             |
| realizedPnL            | int256  |             |
| protocolFee            | uint256 |             |
| baseBalancePerShareX96 | uint256 |             |
| sharePriceAfterX96     | uint256 |             |
| liquidationPenalty     | uint256 |             |
| liquidationreward      | uint256 |             |
| insuranceFundReward    | uint256 |             |

### PositionChanged

```
event PositionChanged(
    address indexed trader,
    address indexed market,
    int256 base,
    int256 quote,
    int256 realizedPnl,
    uint256 protocolFee,
    uint256 baseBalancePerShareX96,
    uint256 sharePriceAfterX96
)
```

DESCRIPTION

**Parameters:**

| Name                   | Type    | Description |
| ---------------------- | ------- | ----------- |
| trader                 | address |             |
| market                 | address |             |
| base                   | int256  |             |
| quote                  | int256  |             |
| realizedPnL            | int256  |             |
| protocolFee            | uint256 |             |
| baseBalancePerShareX96 | uint256 |             |
| sharePriceAfterX96     | uint256 |             |

### MaxMarketsPerAccountChanged

```
event MaxMarketsPerAccountChanged(uint8 value)
```

DESCRIPTION

**Parameters:**

| Name  | Type  | Description |
| ----- | ----- | ----------- |
| value | uint8 |             |

### ImRatioChanged

```
event ImRatioChanged(uint24 value)
```

DESCRIPTION

**Parameters:**

| Name  | Type   | Description |
| ----- | ------ | ----------- |
| value | uint24 |             |

### MmRatioChanged

```
event MmRatioChanged(uint24 value)
```

DESCRIPTION

**Parameters:**

| Name  | Type   | Description |
| ----- | ------ | ----------- |
| value | uint24 |             |

### LiquidationRewardConfigChanged

```
event LiquidationRewardConfigChanged(
    uint24 rewardRatio, 
    uint16 smoothEmaTime
)
```

DESCRIPTION

**Parameters:**

| Name          | Type   | Description |
| ------------- | ------ | ----------- |
| rewardRatio   | uint24 |             |
| smoothEmaTime | uint16 |             |

### ProtocolFeeRatioChanged

```
event ProtocolFeeRatioChanged(uint24 value)
```

DESCRIPTION

**Parameters:**

| Name  | Type   | Description |
| ----- | ------ | ----------- |
| value | uint24 |             |

### IsMarketAllowedChanged

```
event IsMarketAllowedChanged(
    address indexed market, 
    bool isMarketAllowed
)
```

DESCRIPTION

**Parameters:**

| Name            | Type    | Description |
| --------------- | ------- | ----------- |
| market          | address |             |
| isMarketAllowed | bool    |             |

