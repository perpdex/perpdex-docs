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

| Name                | Type    | Description                                                                                                                           |
| ------------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| trader              | address | Address of user who wants to trade                                                                                                    |
| market              | address | Address of market in which user will trade                                                                                            |
| isBaseToQuote       | bool    | True if swap is done from base token to quote token which is short and vice-versa.                                                    |
| isExactInput        | bool    | True if entered amount is to be treated as exact input amount, and if false, entered amount will be treated as desired output amount. |
| amount              | uint256 | Input amount of collateral to trade with.                                                                                             |
| oppositeAmountBound | uint256 | Desired output amount. This is used in conjunction with isExactInput=false                                                            |
| deadline            | uint256 | Time dealine before which trade should execute                                                                                        |

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

| Name                | Type    | Description                                                                                                                           |
| ------------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| trader              | address | Address of user used to preview trade against.                                                                                        |
| market              | address | Address of market in which trade will be previewed                                                                                    |
| caller              | address | The actual caller of function                                                                                                         |
| isBaseToQuote       | bool    | True if swap is done from base token to quote token which is short and vice-versa.                                                    |
| isExactInput        | bool    | True if entered amount is to be treated as exact input amount, and if false, entered amount will be treated as desired output amount. |
| amount              | uint256 | Input amount of collateral to trade with.                                                                                             |
| oppositeAmountBound | uint256 | Desired output amount. This is used in conjunction with isExactInput=false                                                            |

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

These parameters are passed to maxTrade function. It's used to create an ERC4626 long token.

**Attributes:**

| Name          | Type    | Description                                                                                                                           |
| ------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| trader        | address | Account on which call is to be made                                                                                                   |
| market        | address | Market address to for trade                                                                                                           |
| caller        | address | Actual caller of function                                                                                                             |
| isBaseToQuote | bool    | True if swap is done from base token to quote token which is short and vice-versa.                                                    |
| isExactInput  | bool    | True if entered amount is to be treated as exact input amount, and if false, entered amount will be treated as desired output amount. |



## Functions

### deposit

```
function deposit(
    uint256 amount
) external payable
```

The function used to deposit ERC20 token (wETH) as collateral.

**Parameters:**

| Name   | Type    | Description               |
| ------ | ------- | ------------------------- |
| amount | uint256 | Amount of wETH to deposit |

### withdraw

```
function withdraw(
    uint256 amount
) external
```

This function is used to withdraw collateral into the user's wallet.&#x20;

**Parameters:**

| Name   | Type    | Description                        |
| ------ | ------- | ---------------------------------- |
| amount | uint256 | Amount of ETH/wETH to be withdrawn |

### transferInsuranceFund

```
function transferInsuranceFund(
    uint256 amount
) external
```

This function is used to transfer insurance funds into the caller's wallet. This can only be called by the owner.

**Parameters:**

| Name   | Type    | Description                               |
| ------ | ------- | ----------------------------------------- |
| amount | uint256 | Amount of insurance fund to be transfered |

### transferProtocolFee

```
function transferProtocolFee(
    uint256 amount
) external
```

Transfer accumulated protocol fees from the vault into the caller's account. This can only be called by the owner.

**Parameters:**

| Name   | Type    | Description                    |
| ------ | ------- | ------------------------------ |
| amount | uint256 | Amount of fee to be transfered |

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

Add liquidity into the liquidity pool of a market.

**Parameters:**

| Name   | Type               | Description                                                      |
| ------ | ------------------ | ---------------------------------------------------------------- |
| params | AddLiquidityParams | See [AddLiquidityParams](iperpdexexchange.md#addliquidityparams) |

**Return values:**

| Name      | Type    | Description                                 |
| --------- | ------- | ------------------------------------------- |
| base      | uint256 | Actual base amount added to liquidity pool  |
| quote     | uint256 | Actual quote amount added to liquidity pool |
| liquidity | uint256 | Amount of LP shares received                |

### removeLiquidity

```
function removeLiquidity(
    RemoveLiquidityParams calldata params
) external returns (
    uint256 base, 
    uint256 quote
)
```

Remove liquidity from a market by giving out LP shares to the exchange.

**Parameters:**

| Name   | Type                  | Description                                                            |
| ------ | --------------------- | ---------------------------------------------------------------------- |
| params | RemoveLiquidityParams | See [RemoveLiquidityParams](iperpdexexchange.md#removeliquidityparams) |

**Return values:**

| Name  | Type    | Description                 |
| ----- | ------- | --------------------------- |
| base  | uint256 | Base token amount received  |
| quote | uint256 | Quote token amount received |

### trade

```
function trade(
    TradeParams calldata params
) external returns (
    uint256 oppositeAmount
)
```

This function is used to open a position in a market.

**Parameters:**

| Name   | Type        | Description                                        |
| ------ | ----------- | -------------------------------------------------- |
| params | TradeParams | See [TradeParams](iperpdexexchange.md#tradeparams) |

**Return values:**

| Name           | Type    | Description                                                                                                                                                |
| -------------- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| oppositeAmount | uint256 | Amount of base/quote token received. Base or quote depends on the chosen market side. When going long, quote token will be oppositeAmount, and vice-versa. |

### setMaxMarketsPerAccount

```
function setMaxMarketsPerAccount(
    uint8 value
) external
```

This function is used to set the global maximum number of markets a user can trade at.

**Parameters:**

| Name  | Type  | Description               |
| ----- | ----- | ------------------------- |
| value | uint8 | Maximum number of markets |

### setImRatio

```
function setImRatio(
    uint24 value
) external
```

This function is used to set the global initial margin ratio.

**Parameters:**

| Name  | Type   | Description                  |
| ----- | ------ | ---------------------------- |
| value | uint24 | Initial margin ratio to set. |

### setMmRatio

```
function setMmRatio(
    uint24 value
) external
```

This function is used to set the global maintenance margin ratio.

**Parameters:**

| Name  | Type   | Description                     |
| ----- | ------ | ------------------------------- |
| value | uint24 | Maintenance margin ratio value. |

### setLiquidationRewardConfig

```
function setLiquidationRewardConfig(
    PerpdexStructs.LiquidationRewardConfig calldata value
) external
```

This function is used to configure the liquidation reward ratio and estimated-moving average time.

**Parameters:**

| Name  | Type                    | Description                                                                                                                                          |
| ----- | ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| value | LiquidationRewardConfig | <p>It requires following call data from struct<br><strong>LiquidationRewardConfig</strong> {</p><p>    rewardRatio,<br>    smoothEmaTime</p><p>}</p> |

### setProtocolFeeRatio

```
function setProtocolFeeRatio(
    uint24 value
) external
```

Set the protocol fee to be charged on each trade.

**Parameters:**

| Name  | Type   | Description             |
| ----- | ------ | ----------------------- |
| value | uint24 | Fee ratio to be charged |

### setIsMarketAllowed

```
function setIsMarketAllowed(
    address market, 
    bool value
) external
```

This function is used to enable/disable a market.

**Parameters:**

| Name   | Type    | Description                         |
| ------ | ------- | ----------------------------------- |
| market | address | Address of market to enable/disbale |
| value  | bool    | State (enable/disable) to set       |

### previewTrade

```
function previewTrade(
    PreviewTradeParams calldata params
) external view returns (
    uint256 oppositeAmount
)
```

This function is used to calculate the resultant amount (oppositeAmount) from a given input amount without executing the actual trade. It's a dry run variant of trade function.

**Parameters:**

| Name   | Type               | Description                                                      |
| ------ | ------------------ | ---------------------------------------------------------------- |
| params | PreviewTradeParams | See [PreviewTradeParams](iperpdexexchange.md#previewtradeparams) |

**Return values:**

| Name           | Type    | Description                                                                                                 |
| -------------- | ------- | ----------------------------------------------------------------------------------------------------------- |
| oppositeAmount | uint256 | Calculated output amount. The output amount is the base amount when shorting and quote amount when longing. |

### maxTrade

```
function maxTrade(
    MaxTradeParams calldata params
) external view returns (
    uint256 amount
)
```

This function is used by PerpDEX stable coin. It's used to create an ERC4626 1x long token.

**Parameters:**

| Name   | Type           | Description                                              |
| ------ | -------------- | -------------------------------------------------------- |
| params | MaxTradeParams | See [MaxTradeParams](iperpdexexchange.md#maxtradeparams) |

**Return values:**

| Name   | Type    | Description                              |
| ------ | ------- | ---------------------------------------- |
| amount | uint256 | Amount required to open 1x long position |

### accountInfos

```
function accountInfos(
    address trader
) external view returns (
    PerpdexStructs.VaultInfo memory
)
```

This function returns the collateral balance of an account.

**Parameters:**

| Name   | Type    | Description                           |
| ------ | ------- | ------------------------------------- |
| trader | address | Address of the user to get details of |

**Return values:**

| Name | Type      | Description                                        |
| ---- | --------- | -------------------------------------------------- |
| -    | VaultInfo | _VaultInfo_ struct containing _collateralBalance._ |

### insuranceFundInfo

```
function insuranceFundInfo() external view returns (
    int256 balance, 
    uint256 liquidationRewardBalance
)
```

This function returns the insuranceFundInfo struct values. It contains the balance of the insurance fund and liquidation reward.

**Return values:**

| Name                     | Type    | Description                |
| ------------------------ | ------- | -------------------------- |
| balance                  | int256  | Insurance fund balance     |
| liquidationRewardBalance | uint256 | Liquidation reward balance |

### protocolInfo

```
function protocolInfo() external view returns (
    uint256 protocolFee
)
```

This function returns protocolInfo struct object of PerpDEX exchange.

**Return values:**

| Name        | Type    | Description                                    |
| ----------- | ------- | ---------------------------------------------- |
| protocolFee | uint256 | Total trading fee that protocol has acumulated |

### settlementToken

```
function settlementToken() external view returns (
    address
)
```

This function returns the address of settlement token. Settlement token is the token used for settlement of perpetual futures on PerpDEX.

**Return values:**

| Name | Type    | Description                     |
| ---- | ------- | ------------------------------- |
| -    | address | Address of the settlement token |

### quoteDecimals

```
function quoteDecimals() external view returns (
    uint8
)
```

Returns the number of decimals of the quote token.

**Return values:**

| Name | Type  | Description        |
| ---- | ----- | ------------------ |
| -    | uint8 | Number of decimals |

### maxMarketsPerAccount

```
function maxMarketsPerAccount() external view returns (
    uint8
)
```

This function returns the number of maximum markets per account.

**Return values:**

| Name | Type  | Description                    |
| ---- | ----- | ------------------------------ |
| -    | uint8 | Number of max allowed markets. |

### imRatio

```
function imRatio() external view returns (
    uint24
)
```

This function returns the initial margin ratio of the PerpDEX exchange.

**Return values:**

| Name | Type   | Description                |
| ---- | ------ | -------------------------- |
| -    | uint24 | Initial margin ratio value |

### mmRatio

```
function mmRatio() external view returns (
    uint24
)
```

This function returns the maintenance margin ratio of the PerpDEX exchange.

**Return values:**

| Name | Type   | Description                    |
| ---- | ------ | ------------------------------ |
| -    | uint24 | Maintenance margin ratio value |

### liquidationRewardConfig

```
function liquidationRewardConfig() external view returns (
    uint24 rewardRatio, 
    uint16 smoothEmaTime
)
```

This function is used to get the configuration of the liquidation reward ratio and estimated-moving average time.

**Return values:**

| Name          | Type   | Description                                  |
| ------------- | ------ | -------------------------------------------- |
| rewardRatio   | uint24 | Value of reward ratio for liquidators        |
| smoothEmaTime | uint16 | Estimated moving average time interval value |

### protocolFeeRatio

```
function protocolFeeRatio() external view returns (
    uint24
)
```

Returns the value of the protocol fee ratio to be charged during the trade.

**Return values:**

| Name | Type   | Description        |
| ---- | ------ | ------------------ |
| -    | uint24 | Protocol fee ratio |

### isMarketAllowed

```
function isMarketAllowed(
    address market
) external view returns (
    bool
)
```

Returns true if the market is enabled, or else false if the market is disabled.

**Parameters:**

| Name   | Type    | Description                    |
| ------ | ------- | ------------------------------ |
| market | address | Address of market to check for |

**Return values:**

| Name | Type | Description                               |
| ---- | ---- | ----------------------------------------- |
| -    | bool | True if market is enabled, false elsewise |

### getTakerInfo

```
function getTakerInfo(
    address trader, 
    address market
) external view returns (
    PerpdexStructs.TakerInfo memory
)
```

Returns the details of a specific market of a trader account i.e., base balance share, and quote balance. For details, see PerpdexStructs.TakerInfo struct.

**Parameters:**

| Name   | Type    | Description                                 |
| ------ | ------- | ------------------------------------------- |
| trader | address | Wallet address of trader/user               |
| market | address | Market contract address to get details from |

**Return values:**

| Name | Type      | Description                                                                                              |
| ---- | --------- | -------------------------------------------------------------------------------------------------------- |
| -    | TakerInfo | <p>Returns TakerInfo struct with values<br>{</p><p>    baseBalanceShare,<br>    quoteBalance</p><p>}</p> |

### getMakerInfo

```
function getMakerInfo(
    address trader, 
    address market
) external view returns (
    PerpdexStructs.MakerInfo memory
)
```

Returns the details of provided liquidity in a specific market. Details include the amount of liquidity, cumulative base amount per liquidity, and cumulative quote amount per liquidity.

**Parameters:**

| Name   | Type    | Description                                    |
| ------ | ------- | ---------------------------------------------- |
| trader | address | Wallet address of trader                       |
| market | address | Contract address of market to get details from |

**Return values:**

| Name | Type      | Description                                                                                                                                                          |
| ---- | --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -    | MakerInfo | <p>Returns the MakerInfo struct with the following information<br>{</p><p>    liquidity,<br>    cumBaseSharePerLiquidity,</p><p>    cumQuotePerLiquidity</p><p>}</p> |

### getAccountMarkets

```
function getAccountMarkets(
    address trader
) external view returns (
    address[] memory
)
```

Returns all markets of a trader. These markets are the markets that trader has interacted with.

**Parameters:**

| Name   | Type    | Description                  |
| ------ | ------- | ---------------------------- |
| trader | address | Wallet address of the trader |

**Return values:**

| Name | Type       | Description           |
| ---- | ---------- | --------------------- |
| -    | address\[] | Market addresses list |

### getTotalAccountValue

```
function getTotalAccountValue(
    address trader
) external view returns (
    int256
)
```

Returns the total account value of a trader. This includes all open positions on the taker and maker side and collateral balance.

**Parameters:**

| Name   | Type    | Description              |
| ------ | ------- | ------------------------ |
| trader | address | Wallet address of trader |

**Return values:**

| Name | Type   | Description         |
| ---- | ------ | ------------------- |
| -    | int256 | Total account value |

### getPositionShare

```
function getPositionShare(
    address trader, 
    address market
) external view returns (
    int256
)
```

This function returns the cumulative base position share amount of a trader in a specific market.&#x20;

**Parameters:**

| Name   | Type    | Description                                    |
| ------ | ------- | ---------------------------------------------- |
| trader | address | Wallet address of the trader                   |
| market | address | Contract address of market to get details from |

**Return values:**

| Name | Type   | Description       |
| ---- | ------ | ----------------- |
| -    | int256 | Total base shares |

### getPositionNotional

```
function getPositionNotional(
    address trader, 
    address market
) external view returns (
    int256
)
```

This function returns the calculated dollar amount of total base position shares of a trader in a given market.

**Parameters:**

| Name   | Type    | Description                                    |
| ------ | ------- | ---------------------------------------------- |
| trader | address | Wallet address of a user                       |
| market | address | Contract address of market to get details from |

**Return values:**

| Name | Type   | Description                      |
| ---- | ------ | -------------------------------- |
| -    | int256 | Total base shares notional value |

### getTotalPositionNotional

```
function getTotalPositionNotional(
    address trader
) external view returns (
    uint256
)
```

This function returns the calculated dollar amount of total maker side position shares of a trader in all markets.

**Parameters:**

| Name   | Type    | Description                  |
| ------ | ------- | ---------------------------- |
| trader | address | Wallet address of the trader |

**Return values:**

| Name | Type    | Description                         |
| ---- | ------- | ----------------------------------- |
| -    | uint256 | Total notional value of all markets |

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

| Name   | Type    | Description                     |
| ------ | ------- | ------------------------------- |
| trader | address | Wallet address of the user      |
| market | address | Contract address of the market. |

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

Returns true if given trader's address has enough maintenance margin.

**Parameters:**

| Name   | Type    | Description              |
| ------ | ------- | ------------------------ |
| trader | address | Wallet address of trader |

**Return values:**

| Name | Type | Description                                    |
| ---- | ---- | ---------------------------------------------- |
| -    | bool | True if enough maintenance margin, else false. |

### hasEnoughInitialMargin

```
function hasEnoughInitialMargin(
    address trader
) external view returns (
    bool
)
```

This function checks if a trader has enough initial margin to open a new position and returns true on success.

**Parameters:**

| Name   | Type    | Description                                          |
| ------ | ------- | ---------------------------------------------------- |
| trader | address | Wallet address of trader to check for initial margin |

**Return values:**

| Name | Type | Description                                            |
| ---- | ---- | ------------------------------------------------------ |
| -    | bool | True if user has enough initial margin, elsewise false |

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

Emitted when collateral is deposited by a trader into its account.

**Parameters:**

| Name   | Type    | Description                  |
| ------ | ------- | ---------------------------- |
| trader | address | Wallet address of trader     |
| amount | uint256 | Amount of ETH/wETH deposited |

### Withdrawn

```
event Withdrawn(
    address indexed trader, 
    uint256 amount
)
```

Emitted when collateral is withdrawn from a trader's account.

**Parameters:**

| Name   | Type    | Description                  |
| ------ | ------- | ---------------------------- |
| trader | address | Wallet address of the trader |
| amount | uint256 | Amount of ETH/wETH withdrawn |

### InsuranceFundTransferred

```
event InsuranceFundTransferred(
    address indexed trader, 
    uint256 amount
)
```

Emitted when insurance fund is transfered from insurance fund's vault into a trader's account

**Parameters:**

| Name   | Type    | Description                |
| ------ | ------- | -------------------------- |
| trader | address | Wallet address of trader   |
| amount | uint256 | Amount of funds transfered |

### ProtocolFeeTransferred

```
event ProtocolFeeTransferred(
    address indexed trader, 
    uint256 amount
)
```

Emitted when protocol fee is transferred from fee vault into trader's account vault.

**Parameters:**

| Name   | Type    | Description                          |
| ------ | ------- | ------------------------------------ |
| trader | address | Wallet address of trader             |
| amount | uint256 | Amount of protocol fee transferred.  |

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

Emitted when liquidity is added into the system.

**Parameters:**

| Name                    | Type    | Description                                                                     |
| ----------------------- | ------- | ------------------------------------------------------------------------------- |
| trader                  | address | Wallet address of trader                                                        |
| market                  | address | Contract address of market                                                      |
| base                    | uint256 | Base amount added                                                               |
| quote                   | uint256 | Quote amount added                                                              |
| liquidity               | uint256 | Amount of liquidity shares received                                             |
| cumBasePerLiquidityX96  | uint256 | Amount of base tokens excluded from the pool from the time liquidity was added  |
| cumQuotePerLiquidityX96 | uint256 | Amount of quote tokens excluded from the pool from the time liquidity was added |
| baseBalancePerShareX96  | uint256 | Updated base balance per share after funding                                    |
| sharePriceAfterX96      | uint256 | Price of a share after liquidity has been added.                                |

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

Emitted when liquidity is removed from the system.

**Parameters:**

| Name                   | Type    | Description                                            |
| ---------------------- | ------- | ------------------------------------------------------ |
| trader                 | address | Wallet address of trader                               |
| market                 | address | Contract address of market                             |
| liquidator             | address | Address of liquidator                                  |
| base                   | uint256 | Amount of base tokens removed                          |
| quote                  | uint256 | Amount of quote tokens removed                         |
| liquidity              | uint256 | Amount of liquidity shares removed                     |
| takerBase              | int256  | Total base amount including deleveraged base amount    |
| takerQuote             | int256  | Total quote amount including deleveraged quote amount  |
| realizedPnL            | int256  | Realized profit and loss after removing liquidity      |
| baseBalancePerShareX96 | uint256 | Base amount balance per share of liquidity             |
| sharePriceAfterX96     | uint256 | Price of a share of liquidity after removing liquidity |

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

Emitted when a position has been liquidated.

**Parameters:**

| Name                   | Type    | Description                                            |
| ---------------------- | ------- | ------------------------------------------------------ |
| trader                 | address | Address of trader who's position got liquidated        |
| market                 | address | Contract address of market                             |
| liquidator             | address | Address of liquidator who triggered the liquidation    |
| base                   | int256  | Amount of base tokens liquidated                       |
| quote                  | int256  | Amount of quote tokens liquidated                      |
| realizedPnL            | int256  | Realized profit and loss amount                        |
| protocolFee            | uint256 | Amount of protocol fee charged                         |
| baseBalancePerShareX96 | uint256 | Base amount balance per share of liquidity             |
| sharePriceAfterX96     | uint256 | Price of a share of liquidity after removing liquidity |
| liquidationPenalty     | uint256 | Penalty amount due to liquidation                      |
| liquidationreward      | uint256 | Liquidation reward amount for liquidator               |
| insuranceFundReward    | uint256 | Amount transferred to insurance fund as reward         |

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

Emitted whenever a position is opened, closed, or updated.

**Parameters:**

| Name                   | Type    | Description                                            |
| ---------------------- | ------- | ------------------------------------------------------ |
| trader                 | address | Wallet address of trader                               |
| market                 | address | Contract address of market                             |
| base                   | int256  | Base amount updated                                    |
| quote                  | int256  | Quote amount updated                                   |
| realizedPnL            | int256  | Realized profit and loss amount                        |
| protocolFee            | uint256 | Amount of protocol fee charged                         |
| baseBalancePerShareX96 | uint256 | Base amount balance per share of liquidity             |
| sharePriceAfterX96     | uint256 | Price of a share of liquidity after removing liquidity |

### MaxMarketsPerAccountChanged

```
event MaxMarketsPerAccountChanged(uint8 value)
```

Emitted when number of maximum markets per account has been changed.

**Parameters:**

| Name  | Type  | Description                                           |
| ----- | ----- | ----------------------------------------------------- |
| value | uint8 | The new value of maximum markets allowed per account. |

### ImRatioChanged

```
event ImRatioChanged(uint24 value)
```

Emitted when initial margin ratio is changed.

**Parameters:**

| Name  | Type   | Description                  |
| ----- | ------ | ---------------------------- |
| value | uint24 | The new initial margin ratio |

### MmRatioChanged

```
event MmRatioChanged(uint24 value)
```

Emitted when maintenance margin ratio is updated.

**Parameters:**

| Name  | Type   | Description                      |
| ----- | ------ | -------------------------------- |
| value | uint24 | The new maintenance margin ratio |

### LiquidationRewardConfigChanged

```
event LiquidationRewardConfigChanged(
    uint24 rewardRatio, 
    uint16 smoothEmaTime
)
```

Emitted when liquidation reward configuration is updated.

**Parameters:**

| Name          | Type   | Description                     |
| ------------- | ------ | ------------------------------- |
| rewardRatio   | uint24 | New reward ratio set            |
| smoothEmaTime | uint16 | Exponential moving average time |

### ProtocolFeeRatioChanged

```
event ProtocolFeeRatioChanged(uint24 value)
```

Emitted when protocol fee ratio charged is updated

**Parameters:**

| Name  | Type   | Description             |
| ----- | ------ | ----------------------- |
| value | uint24 | The new fee ratio value |

### IsMarketAllowedChanged

```
event IsMarketAllowedChanged(
    address indexed market, 
    bool isMarketAllowed
)
```

Emitted when a specific market is enabled/disabled.

**Parameters:**

| Name            | Type    | Description                           |
| --------------- | ------- | ------------------------------------- |
| market          | address | Contract address of market            |
| isMarketAllowed | bool    | True if market is enabled, else false |

