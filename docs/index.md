# Solidity API

## AaveHandler

This contract represent the Aave position handler

### PROPOSAL_TIME_INTERVAL

```solidity
uint256 PROPOSAL_TIME_INTERVAL
```

@notice the time interval needed to changed the AAVE contract

### USDO

```solidity
address USDO
```

USDO contract address

### sUSDO

```solidity
address sUSDO
```

sUSDO contract address

### AAVE

```solidity
address AAVE
```

AAVE protocl Pool.sol contract address

### TREASURY

```solidity
address TREASURY
```

Protocol treasury

### totalSuppliedUSDC

```solidity
uint256 totalSuppliedUSDC
```

Amount of total supplied USDC

### totalSuppliedUSDT

```solidity
uint256 totalSuppliedUSDT
```

Amount of total supplied USDT

### proposedAave

```solidity
address proposedAave
```

@notice the proposed new spender

### aaveProposalTime

```solidity
uint256 aaveProposalTime
```

@notice the last aave proposal time

### teamAllocationProposalTime

```solidity
uint256 teamAllocationProposalTime
```

@notice the last team allocation proposal time

### proposedTeamAllocation

```solidity
uint8 proposedTeamAllocation
```

@notice the proposed team allocation percentage

### onlyProtocol

```solidity
modifier onlyProtocol()
```

### constructor

```solidity
constructor(address admin, address treasury, address usdo, address susdo) internal
```

The constructor

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| admin | address | The contract admin |
| treasury | address | The protocol treasury |
| usdo | address | The USDO contract |
| susdo | address |  |

### adminWithdraw

```solidity
function adminWithdraw(uint256 amountUsdc, uint256 amountUsdt) external
```

Withraw funds from AAVE protocol

_Use with caution, it will forward all the user funds to the protocol token (funds are safu)
It requires equal amounts in input_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| amountUsdc | uint256 | The amount to withdraw intended as USDC |
| amountUsdt | uint256 | The amount to withdraw intended as USDCT |

### compound

```solidity
function compound() external
```

Compound funds from-to AAVE protocol

_This method assumes that USDC and USDT decimals are less or equal 18
We track the user deposited funds with totalSuppliedUSDC/T and leverage
the dynamic balance of AAVE aToken in order to compute the gains_

### supply

```solidity
function supply(uint256 amountUsdc, uint256 amountUsdt) external
```

Supply funds to AAVE protocol

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| amountUsdc | uint256 | The amount to supply intended as USDC |
| amountUsdt | uint256 | The amount to supply intended as USDT |

### proposeNewAave

```solidity
function proposeNewAave(address aave) external
```

Propose a new AAVE contract

_Can not be zero address_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| aave | address | The new AAVE address |

### proposeNewTeamAllocation

```solidity
function proposeNewTeamAllocation(uint8 proposedTeamAllocation_) external
```

Propose a new AAVE contract

_Can not be zero address_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| proposedTeamAllocation_ | uint8 | The new proposed team allocation |

### acceptProposedAave

```solidity
function acceptProposedAave() external
```

Accept the proposed AAVE contract

### acceptProposedTeamAllocation

```solidity
function acceptProposedTeamAllocation() external
```

Accept the proposed team allocation

### updateTreasury

```solidity
function updateTreasury(address treasury) external
```

Update protocol treasury

_Does not harm protocol users_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| treasury | address | The new treasury address |

### adminSwapPosition

```solidity
function adminSwapPosition() external
```

Swap the current stable coins position into a blue chip (WETH)

### approveAave

```solidity
function approveAave(uint256 amount) public
```

Approve aave spending

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount | uint256 | The amount to allow aave as spender |

### approveStakingUSDO

```solidity
function approveStakingUSDO(uint256 amount) public
```

Approve Staked USDO spending

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount | uint256 | The amount to allow sUSDO as spender |

### approveUSDO

```solidity
function approveUSDO(uint256 amount) public
```

Approve USDO spending

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount | uint256 | The amount to allow USDO as spender |

### withdraw

```solidity
function withdraw(uint256 amountUsdc, uint256 amountUsdt) public
```

Withraw funds from AAVE protocol, the public interface for allowed callers

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| amountUsdc | uint256 | The amount to withdraw intended as USDC |
| amountUsdt | uint256 | The amount to withdraw intended as USDCT |

### renounceOwnership

```solidity
function renounceOwnership() public view
```

Renounce contract ownership

_Reverts by design_

### _withdrawInternal

```solidity
function _withdrawInternal(uint256 amountUsdc, uint256 amountUsdt, address recipient) internal
```

Withraw funds to AAVE protocol

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| amountUsdc | uint256 | The amount to withdraw intended as USDC |
| amountUsdt | uint256 | The amount to withdraw intended as USDCT |
| recipient | address | The collateral recipient |

## Constants

Define utils constants

### USDC

```solidity
address USDC
```

USDC eth mainnet contract address

### USDT

```solidity
address USDT
```

USDT eth mainnet contract address

### AUSDC

```solidity
address AUSDC
```

aUSDC eth mainnet contract address

### AUSDT

```solidity
address AUSDT
```

aUSDT eth mainnet contract address

### WETH

```solidity
address WETH
```

WETH eth mainnet contract address

### AWETH

```solidity
address AWETH
```

aWETH eth mainnet contract address

### UNI_SWAP_ROUTER_V2

```solidity
address UNI_SWAP_ROUTER_V2
```

Uniswap SwapRouterV2

### UNI_QUOTER_V2

```solidity
address UNI_QUOTER_V2
```

Uniswap QuoterV2

## ISwapRouter02

### ExactInputSingleParams

```solidity
struct ExactInputSingleParams {
  address tokenIn;
  address tokenOut;
  uint24 fee;
  address recipient;
  uint256 amountIn;
  uint256 amountOutMinimum;
  uint160 sqrtPriceLimitX96;
}
```

### exactInputSingle

```solidity
function exactInputSingle(struct ISwapRouter02.ExactInputSingleParams params) external payable returns (uint256 amountOut)
```

### ExactOutputSingleParams

```solidity
struct ExactOutputSingleParams {
  address tokenIn;
  address tokenOut;
  uint24 fee;
  address recipient;
  uint256 amountOut;
  uint256 amountInMaximum;
  uint160 sqrtPriceLimitX96;
}
```

### exactOutputSingle

```solidity
function exactOutputSingle(struct ISwapRouter02.ExactOutputSingleParams params) external payable returns (uint256 amountIn)
```

## PositionSwapper

This contract works as a helper utility for AaveHandler to swap Aave
positions. This usage won't affect the security of user's funds as the new position
will still belong to the backing contract.

### SwapUniswapInsufficientBalance

```solidity
error SwapUniswapInsufficientBalance()
```

### SwapUniswapAaveWithdrawFailed

```solidity
error SwapUniswapAaveWithdrawFailed()
```

### _swap

```solidity
function _swap(struct PositionSwapperParams params) internal returns (uint256)
```

Swap all the aUSDC, aUSDT position into aWETH.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| params | struct PositionSwapperParams | A PositionSwapperParams struct containing all the needed swap informations |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | The amount of out token put back into Aave |

## PositionSwapperParams

### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |

```solidity
struct PositionSwapperParams {
  address usdc;
  address ausdc;
  address usdt;
  address ausdt;
  address outToken;
  address aavePool;
  address router;
  address quoter;
  uint256 amountUsdc;
  uint256 amountUsdt;
  address beneficiary;
  uint16 aaveRefCode;
}
```

## USDOBacking

This contract represent the backing allocations manager

### notProtocolAssets

```solidity
modifier notProtocolAssets(address asset)
```

### constructor

```solidity
constructor(address admin, address treasury, address usdo, address susdo) public
```

The constructor

_It accepts to be the USDO collateral spender_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| admin | address | The contract admin |
| treasury | address | The contract treasury |
| usdo | address | The USDO contract |
| susdo | address | The sUSDO contract |

### recoverAsset

```solidity
function recoverAsset(address asset, uint256 amount) external
```

Recover asset from the contract

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| asset | address | The asset to approve |
| amount | uint256 | The spender amount |

## IAaveHandlerDefs

### AaveHandlerZeroAddressException

```solidity
error AaveHandlerZeroAddressException()
```

### AaveHandlerSameAddressException

```solidity
error AaveHandlerSameAddressException()
```

### AaveHandlerCantRenounceOwnership

```solidity
error AaveHandlerCantRenounceOwnership()
```

### AaveHandlerOperationNotAllowed

```solidity
error AaveHandlerOperationNotAllowed()
```

### AaveHandlerAaveWithrawFailed

```solidity
error AaveHandlerAaveWithrawFailed()
```

### AaveHandlerInsufficientBalance

```solidity
error AaveHandlerInsufficientBalance()
```

### AaveIntervalNotRespected

```solidity
error AaveIntervalNotRespected()
```

### AaveActionFailed

```solidity
event AaveActionFailed(string message, bytes reason)
```

### AaveWithdraw

```solidity
event AaveWithdraw(uint256 usdc, uint256 usdt)
```

### AaveSupply

```solidity
event AaveSupply(uint256 usdc, uint256 usdt)
```

### AaveNewAave

```solidity
event AaveNewAave(address addr)
```

### AaveNewTeamAllocation

```solidity
event AaveNewTeamAllocation(uint8 amount)
```

### AaveNewTreasury

```solidity
event AaveNewTreasury(address addr)
```

### AaveSwapPosition

```solidity
event AaveSwapPosition(uint256 usdc, uint256 usdt, uint256 out)
```

## IUSDO

### acceptProposedCollateralSpender

```solidity
function acceptProposedCollateralSpender() external
```

### mint

```solidity
function mint(struct MintRedeemManagerTypes.Order order) external
```

## IUSDOBackingDefs

### USDOBackingZeroAddressException

```solidity
error USDOBackingZeroAddressException()
```

### USDOBackingCantRenounceOwnership

```solidity
error USDOBackingCantRenounceOwnership()
```

### USDOBackingOperationNotAllowed

```solidity
error USDOBackingOperationNotAllowed()
```

### USDOSpenderAccepted

```solidity
event USDOSpenderAccepted()
```

## IsUSDO

### transferInRewards

```solidity
function transferInRewards(uint256 amount) external
```

## ICurveStableSwapPool

### add_liquidity

```solidity
function add_liquidity(uint256[2] amounts, uint256 min_mint_amount) external
```

### get_virtual_price

```solidity
function get_virtual_price() external returns (uint256)
```

## ICurveStableSwapTriPool

### add_liquidity

```solidity
function add_liquidity(uint256[3] amounts, uint256 min_mint_amount) external
```

### get_virtual_price

```solidity
function get_virtual_price() external returns (uint256)
```

## CurveLiquidityProxy

### addStableSwap

```solidity
function addStableSwap(contract ICurveStableSwapPool pool, contract IERC20 lp, contract IERC20 token0, contract IERC20 token1, uint256 amount0, uint256 amount1) external
```

### addTriStableSwap

```solidity
function addTriStableSwap(contract ICurveStableSwapTriPool pool, contract IERC20 lp, contract IERC20 token0, contract IERC20 token1, contract IERC20 token2, uint256 amount0, uint256 amount1, uint256 amount2) external
```

_This works only for https://etherscan.io/address/0xbebc44782c7db0a1a60cb6fe97d0b483032ff1c7#readContract
User must send the amounts to this contract first_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pool | contract ICurveStableSwapTriPool | The Curve fi pool |
| lp | contract IERC20 | The Curve fi liquidity pool token |
| token0 | contract IERC20 | DAI address |
| token1 | contract IERC20 | USDC address |
| token2 | contract IERC20 | USDT address |
| amount0 | uint256 | DAI amount |
| amount1 | uint256 | USDC amount |
| amount2 | uint256 | USDT amount |

## ICurvePool

### balances

```solidity
function balances(uint256 index) external view returns (uint256)
```

### coins

```solidity
function coins(uint256 index) external view returns (address)
```

## IERC20Decimals

### decimals

```solidity
function decimals() external view returns (uint8)
```

## CurveStableStake

Curve finance stable swap pool lp staking contract implementation.
This contract supports multiple staking pools to be deployed in the same contract sharing the reward token.

### rewardsPerSecondMultiplierNum

```solidity
mapping(address => uint256) rewardsPerSecondMultiplierNum
```

The emitted amount of reward for each second multiplier numerator.

### rewardsPerSecondMultiplierDen

```solidity
mapping(address => uint256) rewardsPerSecondMultiplierDen
```

The emitted amount of reward for each second multiplier denominator.

### nCoinsTracker

```solidity
mapping(address => mapping(address => uint8)) nCoinsTracker
```

Track number of stable coins held inside Curve pools.

### curvePools

```solidity
mapping(address => contract ICurvePool) curvePools
```

Curve pools associated to Curve lps.

### SECONDS_IN_YEAR

```solidity
uint256 SECONDS_IN_YEAR
```

The seconds in a year.

### constructor

```solidity
constructor(address admin) public
```

Contract constructor.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| admin | address | The contract admin |

### addWithNumCoinsAndPool

```solidity
function addWithNumCoinsAndPool(contract IERC20 stakedAsset, contract IERC20 rewardAsset, uint256 allocationPoints, uint8 numCoins, contract ICurvePool pool, uint256 endTime, bool vested, bool update) external
```

Add a new pool and track the total coins held inside the Curve pool.

_It reverts if the starting time is set to zero_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| stakedAsset | contract IERC20 | the wanted lp token. |
| rewardAsset | contract IERC20 | the reward that will be payed out. |
| allocationPoints | uint256 | the weight of the added pool. |
| numCoins | uint8 | the total stable coins held inside the Curve pool. |
| pool | contract ICurvePool | the Curve pool associated to this lp. |
| endTime | uint256 | the ending time for this pool. 0 to ignore. |
| vested | bool | a boolean flag stating if harvest and withdraw have to wait for the end of the pool. |
| update | bool | a boolean flag stating if update or not old pools. |

### setRewardForStakedAssets

```solidity
function setRewardForStakedAssets(contract IERC20 rewardAsset, uint256 rewardRateNum, uint256 rewardRateDen) external
```

Set a reward rate.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardAsset | contract IERC20 | the reward. |
| rewardRateNum | uint256 | the new reward rate numerator. |
| rewardRateDen | uint256 | the new reward rate denominator. |

### pendingReward

```solidity
function pendingReward(uint256 pid, address user) public view returns (uint256)
```

Get the pending reward for a given pool and user.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pid | uint256 | the pool identifier. |
| user | address | the participant. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | the pending reward for given pool and user. |

### updatePool

```solidity
function updatePool(uint256 pid) internal
```

Update pool infos.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pid | uint256 | the pool identifier. |

### rewardsForStakedAssets

```solidity
function rewardsForStakedAssets(contract IERC20 staked, contract IERC20 reward) internal view returns (uint256)
```

Get the reward amount for second based on the total staked liquidity.

_If the staked amount is less than 1 ether or less than a second then the emitted amount will be zero._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| staked | contract IERC20 | the staked asset. |
| reward | contract IERC20 | the reward asset. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | the emitted reward for staked asset for second. |

## Liquidity

Liquidity contract implementation.

### poolInfo

```solidity
struct ILiquidityDefs.PoolInfo[] poolInfo
```

The pool info.

### userInfo

```solidity
mapping(uint256 => mapping(address => struct ILiquidityDefs.UserInfo)) userInfo
```

The users info.

### startTime

```solidity
uint256 startTime
```

The starting time for rewards.

### rewardsPerSecond

```solidity
mapping(address => uint256) rewardsPerSecond
```

The emitted amount of reward for each second.

### activeRewards

```solidity
mapping(address => bool) activeRewards
```

Currently active reward.

### totalAllocPointsPerReward

```solidity
mapping(address => uint256) totalAllocPointsPerReward
```

The total allocation points for each reward.

### bonusMultiplier

```solidity
uint256 bonusMultiplier
```

The bonus multiplier.

### referralBonus

```solidity
uint8 referralBonus
```

Referral bonus percentage.

_5%_

### selfReferralBonus

```solidity
uint16 selfReferralBonus
```

Referral bonus percentage.

_2.5%_

### referral

```solidity
contract IOvaReferral referral
```

Referral contract.

### constructor

```solidity
constructor(address admin) public
```

Contract constructor.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| admin | address | The contract admin |

### updateStartTime

```solidity
function updateStartTime(uint256 startTime_) external
```

Update the rewards starting time.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| startTime_ | uint256 | the new start time. |

### updateReferralBonus

```solidity
function updateReferralBonus(uint8 referralBonus_) external
```

Update the referral bonus amount.

_It can not be over 100 (100%)._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| referralBonus_ | uint8 | the bonus amount. |

### updateSelfReferralBonus

```solidity
function updateSelfReferralBonus(uint16 selfReferralBonus_) external
```

Update the referral bonus amount.

_It can not be over 1000 (100%)._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| selfReferralBonus_ | uint16 | the bonus amount. |

### updateReferral

```solidity
function updateReferral(contract IOvaReferral referral_) external
```

Update the referral contract.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| referral_ | contract IOvaReferral | the referral contract. |

### updateMultiplier

```solidity
function updateMultiplier(uint256 bonusMultiplier_) external
```

Update the multiplier value.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| bonusMultiplier_ | uint256 | the new multiplier value. |

### setReward

```solidity
function setReward(contract IERC20 rewardAsset, uint256 rewardRate) external
```

Set a reward rate.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardAsset | contract IERC20 | the reward. |
| rewardRate | uint256 | the new reward rate. |

### setPoolAllocPoints

```solidity
function setPoolAllocPoints(uint256 pid, uint256 newPoints, bool update) external returns (uint256 newTotal)
```

Modify the allocation points for a pool.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pid | uint256 | the pool pid. |
| newPoints | uint256 | the new weight. |
| update | bool |  |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| newTotal | uint256 | the new total allocation. |

### withdraw

```solidity
function withdraw(uint256 pid, uint256 amount) external
```

/**
Withdraw from the pool with harvest.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pid | uint256 | the pool identifier. |
| amount | uint256 | the amount to withdraw. |

### harvestFor

```solidity
function harvestFor(uint256 pid, address target) external
```

Harvest reward for an account.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pid | uint256 | the pool identifier. |
| target | address | the user to be harvested. |

### harvest

```solidity
function harvest(uint256 pid) external
```

Harvest reward.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pid | uint256 | the pool identifier. |

### emergencyWithdraw

```solidity
function emergencyWithdraw(uint256 pid) external
```

Emergency withdraw all the deposited funds.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pid | uint256 | the pool identifier. |

### poolLength

```solidity
function poolLength() external view returns (uint256)
```

Get the pool lenght.

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | the lenght of the liquidity info. |

### getTotalStakedInPool

```solidity
function getTotalStakedInPool(uint256 pid) external view returns (uint256)
```

Get the total amount of tokens staked inside a pool.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pid | uint256 | the pool identifier. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | the amount of token staked inside the given pool. |

### deposit

```solidity
function deposit(uint256 pid, uint256 amount) public
```

Deposit into the pool with harvest.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pid | uint256 | the pool identifier. |
| amount | uint256 | the amount to deposit. |

### add

```solidity
function add(contract IERC20 stakedAsset, contract IERC20 rewardAsset, uint256 allocationPoints, uint256 endTime, bool vested, bool update) public
```

Add a new pool

_It reverts if the starting time is set to zero
A vesting pool can not have endTime equal to 0_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| stakedAsset | contract IERC20 | the wanted lp token. |
| rewardAsset | contract IERC20 | the reward that will be payed out. |
| allocationPoints | uint256 | the weight of the added pool. |
| endTime | uint256 | the ending time for this pool. 0 to ignore. |
| vested | bool | a boolean flag stating if harvest and withdraw have to wait for the end of the pool. |
| update | bool | a boolean flag stating if update or not old pools. |

### pendingReward

```solidity
function pendingReward(uint256 pid, address user) public view virtual returns (uint256)
```

Get the pending reward for a given pool and user.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pid | uint256 | the pool identifier. |
| user | address | the participant. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | the pending reward for given pool and user. |

### pendingRewardsReferral

```solidity
function pendingRewardsReferral(string code, uint256 pid, uint256 startIndex, uint256 endIndex) public view returns (uint256)
```

Retrieve all the pending rewards under a given referral code.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| code | string | The referral code |
| pid | uint256 | The pool id |
| startIndex | uint256 | The start referred array index to query from |
| endIndex | uint256 | The end referred array index to query from |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | The total pending rewards |

### _massUpdatePools

```solidity
function _massUpdatePools() internal
```

Update all the pools.

### _payReward

```solidity
function _payReward(contract IERC20 rewardAsset, address to, uint256 amount) internal
```

Pay the reward.

_The reward asset is directly minted from the reward token_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardAsset | contract IERC20 | the reward token. |
| to | address | the reward receiver. |
| amount | uint256 | the amount to be payed. |

### _returnStakedTokens

```solidity
function _returnStakedTokens(contract IERC20 token, address to, uint256 amount) internal
```

Return the staked tokens.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| token | contract IERC20 | the staked token. |
| to | address | the reward receiver. |
| amount | uint256 | the amount to be returned. |

### _payBonus

```solidity
function _payBonus(uint256 originalAmount, contract IERC20 asset, address source) internal
```

Pay bonus referral tokens

_The self bonus will be payed only if the current user is referred._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| originalAmount | uint256 | the original amount. |
| asset | contract IERC20 |  |
| source | address | the reward source address. |

### updatePool

```solidity
function updatePool(uint256 pid) internal virtual
```

Update pool infos.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pid | uint256 | the pool identifier. |

### _getMultiplier

```solidity
function _getMultiplier(uint256 from, uint256 to) internal view returns (uint256)
```

Get the multiplier value calculated between two times.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| from | uint256 | the starting time. |
| to | uint256 | the ending time. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | The difference between the two sides multiplied for the bonus. |

## SingleStableStake

Single stable coin staking contract implementation.
This contract supports multiple staking pools to be deployed in the same contract sharing the reward token.

### rewardsPerSecondMultiplierNum

```solidity
mapping(address => uint256) rewardsPerSecondMultiplierNum
```

The emitted amount of reward for each second multiplier numerator.

### rewardsPerSecondMultiplierDen

```solidity
mapping(address => uint256) rewardsPerSecondMultiplierDen
```

The emitted amount of reward for each second multiplier denominator.

### SECONDS_IN_YEAR

```solidity
uint256 SECONDS_IN_YEAR
```

The seconds in a year.

### constructor

```solidity
constructor(address admin) public
```

Contract constructor.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| admin | address | The contract admin |

### setRewardForStakedAssets

```solidity
function setRewardForStakedAssets(contract IERC20 rewardAsset, uint256 rewardRateNum, uint256 rewardRateDen) external
```

Set a reward rate.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardAsset | contract IERC20 | the reward. |
| rewardRateNum | uint256 | the new reward rate numerator. |
| rewardRateDen | uint256 | the new reward rate denominator. |

### pendingReward

```solidity
function pendingReward(uint256 pid, address user) public view returns (uint256)
```

Get the pending reward for a given pool and user.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pid | uint256 | the pool identifier. |
| user | address | the participant. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | the pending reward for given pool and user. |

### updatePool

```solidity
function updatePool(uint256 pid) internal
```

Update pool infos.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pid | uint256 | the pool identifier. |

### rewardsForStakedAssets

```solidity
function rewardsForStakedAssets(contract IERC20 staked, contract IERC20 reward) internal view returns (uint256)
```

Get the reward amount for second based on the total staked liquidity.

_If the staked amount is less than 1 ether or less than a second then the emitted amount will be zero._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| staked | contract IERC20 | the staked asset. |
| reward | contract IERC20 | the reward asset. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | the emitted reward for staked asset for second. |

## ILiquidityDefs

### UserInfo

Info on each user.

```solidity
struct UserInfo {
  uint256 amount;
  uint256 rewardDebt;
}
```

### PoolInfo

Info on each pool.

```solidity
struct PoolInfo {
  contract IERC20 stakedAsset;
  contract IERC20 rewardAsset;
  uint256 allocPoints;
  uint256 lastRewardTime;
  uint256 accRewardPerShare;
  uint256 endTimeStamp;
  bool vesting;
}
```

### Deposit

```solidity
event Deposit(address user, uint256 pid, uint256 amount)
```

### Withdraw

```solidity
event Withdraw(address user, uint256 pid, uint256 amount)
```

### Harvest

```solidity
event Harvest(address user, uint256 pid, uint256 amount)
```

### EmergencyWithdraw

```solidity
event EmergencyWithdraw(address user, uint256 pid, uint256 amount)
```

### NewBonusMultiplier

```solidity
event NewBonusMultiplier(uint256 multiplier)
```

### NewReferralBonus

```solidity
event NewReferralBonus(uint8 bonus)
```

### NewSelfReferralBonus

```solidity
event NewSelfReferralBonus(uint16 bonus)
```

### NewReferral

```solidity
event NewReferral(contract IOvaReferral referral)
```

### BonusPayed

```solidity
event BonusPayed(address recipient, uint256 amount)
```

### SelfBonusPayed

```solidity
event SelfBonusPayed(address recipient, uint256 amount)
```

### NotAllowed

```solidity
error NotAllowed()
```

### VestingPool

```solidity
error VestingPool()
```

### InvalidAmount

```solidity
error InvalidAmount()
```

### InvalidPid

```solidity
error InvalidPid()
```

### InvalidZeroAddress

```solidity
error InvalidZeroAddress()
```

### InvactiveReward

```solidity
error InvactiveReward()
```

### LiquidityNotActive

```solidity
error LiquidityNotActive()
```

### InvalidTimeRange

```solidity
error InvalidTimeRange()
```

### PoolNotActive

```solidity
error PoolNotActive()
```

### poolLength

```solidity
function poolLength() external view returns (uint256)
```

### deposit

```solidity
function deposit(uint256 pid, uint256 amount) external
```

### withdraw

```solidity
function withdraw(uint256 pid, uint256 amount) external
```

### harvest

```solidity
function harvest(uint256 pid) external
```

### harvestFor

```solidity
function harvestFor(uint256 pid, address target) external
```

### pendingReward

```solidity
function pendingReward(uint256 pid, address _user) external view returns (uint256)
```

### userInfo

```solidity
function userInfo(uint256 pid, address _user) external view returns (uint256, uint256)
```

### emergencyWithdraw

```solidity
function emergencyWithdraw(uint256 pid) external
```

## IRewardAsset

### mint

```solidity
function mint(address to, uint256 amount) external
```

## FixedSupplyERC20

### constructor

```solidity
constructor(uint256 initialSupply, string name, string symbol) public
```

## MintableERC20

### minter

```solidity
mapping(address => bool) minter
```

_Minter addresses._

### onlyMinter

```solidity
modifier onlyMinter()
```

### constructor

```solidity
constructor(uint256 initialSupply, string name, string symbol) public
```

### setMinter

```solidity
function setMinter(address _minter) external
```

_Set a new minter._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _minter | address | The minter address. |

### removeMinter

```solidity
function removeMinter(address _minter) external
```

_Remove a minter._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _minter | address | The minter address. |

### mint

```solidity
function mint(uint256 _amount) external returns (uint256 newSupply)
```

_Mint new supply._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _amount | uint256 | the amount to be minted. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| newSupply | uint256 | the new totalSupply. |

### burn

```solidity
function burn(uint256 _amount) external returns (uint256 newSupply)
```

_Burn supply._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _amount | uint256 | the amount to be minted. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| newSupply | uint256 | the new totalSupply. |

## MintableERC20WithFixedTotalSupply

### minter

```solidity
mapping(address => bool) minter
```

_Minter addresses._

### maxSupply

```solidity
uint256 maxSupply
```

_The maximum total supply._

### onlyMinter

```solidity
modifier onlyMinter()
```

### constructor

```solidity
constructor(uint256 initialSupply, uint256 maxTotalSupply, string name, string symbol) public
```

### setMinter

```solidity
function setMinter(address _minter) external
```

_Set a new minter._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _minter | address | The minter address. |

### removeMinter

```solidity
function removeMinter(address _minter) external
```

_Remove a minter._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _minter | address | The minter address. |

### mint

```solidity
function mint(uint256 _amount) external returns (uint256 newSupply)
```

_Mint new supply._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _amount | uint256 | the amount to be minted. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| newSupply | uint256 | the new totalSupply. |

### burn

```solidity
function burn(uint256 _amount) external returns (uint256 newSupply)
```

_Burn supply._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _amount | uint256 | the amount to be minted. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| newSupply | uint256 | the new totalSupply. |

## IMintableERC20

### mint

```solidity
function mint(uint256 _amount) external returns (uint256)
```

### burn

```solidity
function burn(uint256 _amount) external returns (uint256)
```

## SixDecimalsUsd

### constructor

```solidity
constructor(uint256 _initialSupply, string _name, string _symbol) public
```

### decimals

```solidity
function decimals() public view virtual returns (uint8)
```

_Returns the number of decimals used to get its user representation.
For example, if `decimals` equals `2`, a balance of `505` tokens should
be displayed to a user as `5.05` (`505 / 10 ** 2`).

Tokens usually opt for a value of 18, imitating the relationship between
Ether and Wei. This is the default value returned by this function, unless
it's overridden.

NOTE: This information is only used for _display_ purposes: it in
no way affects any of the arithmetic of the contract, including
{IERC20-balanceOf} and {IERC20-transfer}._

## TokenLP_A_B

### constructor

```solidity
constructor(uint256 _initialSupply, string _name, string _symbol) public
```

## TokenReward

### constructor

```solidity
constructor(uint256 _initialSupply, string _name, string _symbol) public
```

## SingleAdminAccessControl

SingleAdminAccessControl is a contract that provides a single admin role
This contract is a simplified alternative to OpenZeppelin's AccessControlDefaultAdminRules

### notAdmin

```solidity
modifier notAdmin(bytes32 role)
```

### transferAdmin

```solidity
function transferAdmin(address newAdmin) external
```

Transfer the admin role to a new address
This can ONLY be executed by the current admin

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| newAdmin | address | address |

### acceptAdmin

```solidity
function acceptAdmin() external
```

### grantRole

```solidity
function grantRole(bytes32 role, address account) public
```

grant a role
can only be executed by the current single admin
admin role cannot be granted externally

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| role | bytes32 | bytes32 |
| account | address | address |

### revokeRole

```solidity
function revokeRole(bytes32 role, address account) public
```

revoke a role
can only be executed by the current admin
admin role cannot be revoked

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| role | bytes32 | bytes32 |
| account | address | address |

### renounceRole

```solidity
function renounceRole(bytes32 role, address account) public virtual
```

renounce the role of msg.sender
admin role cannot be renounced

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| role | bytes32 | bytes32 |
| account | address | address |

### owner

```solidity
function owner() public view virtual returns (address)
```

_See {IERC5313-owner}._

### _grantRole

```solidity
function _grantRole(bytes32 role, address account) internal returns (bool)
```

no way to change admin without removing old admin first

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| role | bytes32 | The role |
| account | address | The account address |

## ISingleAdminAccessControl

### InvalidAdminChange

```solidity
error InvalidAdminChange()
```

### NotPendingAdmin

```solidity
error NotPendingAdmin()
```

### AdminTransferred

```solidity
event AdminTransferred(address oldAdmin, address newAdmin)
```

Emitted when the admin role has been transfered

### AdminTransferRequested

```solidity
event AdminTransferRequested(address oldAdmin, address newAdmin)
```

Emitted when an admin role transfer has been requested

## Collateral

This contract handles the collateral for USDO

### CollateralInvalidZeroAddress

```solidity
error CollateralInvalidZeroAddress()
```

### CollateralInvalidDecimals

```solidity
error CollateralInvalidDecimals()
```

### usdt

```solidity
struct MintRedeemManagerTypes.StableCoin usdt
```

Supported assets

### usdc

```solidity
struct MintRedeemManagerTypes.StableCoin usdc
```

### constructor

```solidity
constructor(address admin, struct MintRedeemManagerTypes.StableCoin usdc_, struct MintRedeemManagerTypes.StableCoin usdt_) internal
```

## CollateralSpenderManager

This contract handles the collateral spender for USDO

### CollateralSpenderManagerInvalidAdminAddress

```solidity
error CollateralSpenderManagerInvalidAdminAddress()
```

### CollateralSpenderManagerInvalidSpenderAddress

```solidity
error CollateralSpenderManagerInvalidSpenderAddress()
```

### CollateralSpenderManagerIntervalNotRespected

```solidity
error CollateralSpenderManagerIntervalNotRespected()
```

### CollateralSpenderManagerOperatioNotAllowed

```solidity
error CollateralSpenderManagerOperatioNotAllowed()
```

### COLLATERAL_MANAGER_ROLE

```solidity
bytes32 COLLATERAL_MANAGER_ROLE
```

role enabling to transfer collateral to custody wallets

### PROPOSAL_TIME_INTERVAL

```solidity
uint256 PROPOSAL_TIME_INTERVAL
```

@notice the time interval needed to changed a spender address

### approvedCollateralSpender

```solidity
address approvedCollateralSpender
```

@notice the unique approved collateral spender

### proposedSpender

```solidity
address proposedSpender
```

@notice the proposed new spender

### proposalTime

```solidity
uint256 proposalTime
```

@notice the last proposal time

### constructor

```solidity
constructor(address admin, struct MintRedeemManagerTypes.StableCoin usdc_, struct MintRedeemManagerTypes.StableCoin usdt_) internal
```

### getSpender

```solidity
function getSpender() public view returns (address)
```

@notice View the spender

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | address | The active spender |

### proposeNewCollateralSpender

```solidity
function proposeNewCollateralSpender(address spender) external
```

@notice Propose a new spender

_Can not be zero address_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| spender | address | The proposed new spender |

### acceptProposedCollateralSpender

```solidity
function acceptProposedCollateralSpender() external
```

@notice The proposed spender accepts to be the spender

_If it is the initial spender, the PROPOSAL_TIME_INTERVAL is not respected_

## GovernanceTokenBase

This token represent a mintable token by an allowed minter.

### ZeroAddressException

```solidity
error ZeroAddressException()
```

### OnlyMinter

```solidity
error OnlyMinter()
```

### CantRenounceOwnership

```solidity
error CantRenounceOwnership()
```

### OperationNotAllowed

```solidity
error OperationNotAllowed()
```

### MinterStateChanged

```solidity
event MinterStateChanged(address minter_, bool _event)
```

### minter

```solidity
mapping(address => bool) minter
```

The allowed minter

### constructor

```solidity
constructor(address admin, string name, string symbol) public
```

The constructor

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| admin | address | The contract admin |
| name | string | The token name |
| symbol | string | The token symbol |

### setMinter

```solidity
function setMinter(address minter_) external
```

Set a new minter

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| minter_ | address | The new minter address |

### removeMinter

```solidity
function removeMinter(address minter_) external
```

Set a new minter

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| minter_ | address | The new minter address |

### mint

```solidity
function mint(address to, uint256 amount) external
```

Mint tokens

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| to | address | The recipient address |
| amount | uint256 | The amount to be minted |

### renounceOwnership

```solidity
function renounceOwnership() public view
```

Renounce contract ownership

_Reverts by design_

## MintRedeemManager

This contract mints and redeems the USDO contract that inherits this contract

### _decimals

```solidity
uint256 _decimals
```

Parent token decimals

### mintedPerBlock

```solidity
mapping(uint256 => uint256) mintedPerBlock
```

USDO minted per block

### redeemedPerBlock

```solidity
mapping(uint256 => uint256) redeemedPerBlock
```

USDO redeemed per block

### maxMintPerBlock

```solidity
uint256 maxMintPerBlock
```

max minted USDO allowed per block

### maxRedeemPerBlock

```solidity
uint256 maxRedeemPerBlock
```

@notice max redeemed USDO allowed per block

### belowMaxMintPerBlock

```solidity
modifier belowMaxMintPerBlock(uint256 mintAmount)
```

ensure that the already minted USDO in the actual block plus the amount to be minted is below the maxMintPerBlock var

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| mintAmount | uint256 | The USDO amount to be minted |

### belowMaxRedeemPerBlock

```solidity
modifier belowMaxRedeemPerBlock(uint256 redeemAmount)
```

ensure that the already redeemed USDO in the actual block plus the amount to be redeemed is below the maxRedeemPerBlock var

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| redeemAmount | uint256 | The USDO amount to be redeemed |

### constructor

```solidity
constructor(struct MintRedeemManagerTypes.StableCoin usdc_, struct MintRedeemManagerTypes.StableCoin usdt_, address admin, uint256 decimals, uint256 maxMintPerBlock_, uint256 maxRedeemPerBlock_) internal
```

### receive

```solidity
receive() external payable
```

Fallback function to receive ether

### approveCollateral

```solidity
function approveCollateral() external
```

Approve an external spender for USDC and USDT

_The spender is handled by the CollateralSpenderManager contract_

### setMaxMintPerBlock

```solidity
function setMaxMintPerBlock(uint256 maxMintPerBlock_) external
```

Sets the max mintPerBlock limit

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| maxMintPerBlock_ | uint256 | The new max value |

### setMaxRedeemPerBlock

```solidity
function setMaxRedeemPerBlock(uint256 maxRedeemPerBlock_) external
```

Sets the max redeemPerBlock limit

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| maxRedeemPerBlock_ | uint256 | The new max value |

### disableMint

```solidity
function disableMint() external
```

Disables the mint and redeem

### removeCollateralManagerRole

```solidity
function removeCollateralManagerRole(address collateralManager) external
```

Removes the collateral manager role from an account, this can ONLY be executed by the gatekeeper role

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| collateralManager | address | The address to remove the collateralManager role from |

### supplyToBacking

```solidity
function supplyToBacking() external
```

Supply funds to the active backing contract (aka approvedCollateralSpender)

_the approveCollateralSpender will colect the funds, as the only entity allowed to do so_

### pause

```solidity
function pause() external
```

Pause the contract

_This call is used only to lock the supplyToBacking public call_

### unpause

```solidity
function unpause() external
```

Unpause the contract

_This call is used only to unlock the supplyToBacking public call_

### _validateInvariant

```solidity
function _validateInvariant(struct MintRedeemManagerTypes.Order order) internal view
```

Check mint and redeem invariant

_The minimum amount is 1 USDC and 1 USDT. This invariant holds only if _decimasl >= usdc.decimals >= usdt.decimals_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| order | struct MintRedeemManagerTypes.Order | A struct containing the order |

### _managerMint

```solidity
function _managerMint(struct MintRedeemManagerTypes.Order order) internal
```

Mint stablecoins from assets

_Order benefactor is not used as we constraint it to be the msg.sender at higher level_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| order | struct MintRedeemManagerTypes.Order | A struct containing the mint order |

### _managerRedeem

```solidity
function _managerRedeem(struct MintRedeemManagerTypes.Order order) internal returns (uint256 amountToBurn, uint256 usdcBack, uint256 usdtBack)
```

Redeem stablecoins for assets

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| order | struct MintRedeemManagerTypes.Order | struct containing order details and confirmation from server |

### _withdrawFromProtocol

```solidity
function _withdrawFromProtocol(uint256 amount) internal returns (uint256 checkedBurnAmount, uint256 usdcBack, uint256 usdtBack)
```

Redeem collateral from the protocol

_It will trigger the backing contract (aka approvedCollateralSpender) withdraw method if the collateral is not sufficient_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount | uint256 | The amount of USDO to be unmint |

### _transferToBeneficiary

```solidity
function _transferToBeneficiary(address beneficiary, address asset, uint256 amount) internal
```

transfer supported asset to beneficiary address

_This contract needs to have available funds_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| beneficiary | address | The redeem beneficiary |
| asset | address | The redeemed asset |
| amount | uint256 | The redeemed amount |

### _transferCollateral

```solidity
function _transferCollateral(uint256 amount, address asset, address recipient) internal
```

transfer supported asset to target addresses

_User must have approved this contract for allowance_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount | uint256 | The amount to be transfered |
| asset | address | The asset to be transfered |
| recipient | address | The destination address |

### _setMaxMintPerBlock

```solidity
function _setMaxMintPerBlock(uint256 maxMintPerBlock_) internal
```

Sets the max mintPerBlock limit

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| maxMintPerBlock_ | uint256 | The new max value |

### _setMaxRedeemPerBlock

```solidity
function _setMaxRedeemPerBlock(uint256 maxRedeemPerBlock_) internal
```

Sets the max redeemPerBlock limit

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| maxRedeemPerBlock_ | uint256 | The new max value |

## OVA

This token represent the governance OVAG token.

### constructor

```solidity
constructor(address admin) public
```

The constructor

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| admin | address | The contract admin |

## OvaReferral

This token tracks the referral points for OVA airdrop.

### referredFrom

```solidity
mapping(address => address) referredFrom
```

Track the referral source for given address

### referredUsers

```solidity
mapping(address => address[]) referredUsers
```

Track all the referred users for a given address

### generatedPoints

```solidity
mapping(address => uint256) generatedPoints
```

Track all the generated referral points for given address

### allowedPointsTrackers

```solidity
mapping(address => bool) allowedPointsTrackers
```

External entities who can control the points tracking

### referralCodes

```solidity
mapping(string => address) referralCodes
```

Referral code to its creator address

### referralCodesRev

```solidity
mapping(address => string) referralCodesRev
```

Referral code creator address to code

### codes

```solidity
string[] codes
```

All the referral codes

### stakingPools

```solidity
address[] stakingPools
```

All staking pools where this token is emitted from

### Referral

```solidity
event Referral(address source, address consumer)
```

### NewCode

```solidity
event NewCode(string code, address holder)
```

### AddTracker

```solidity
event AddTracker(address tracker)
```

### RemoveTracker

```solidity
event RemoveTracker(address tracker)
```

### OvaReferralAlreadyReferred

```solidity
error OvaReferralAlreadyReferred()
```

### OvaReferralZeroAddress

```solidity
error OvaReferralZeroAddress()
```

### OvaReferralNotAllowed

```solidity
error OvaReferralNotAllowed()
```

### OvaReferralCodeNotValid

```solidity
error OvaReferralCodeNotValid()
```

### OvaReferralCodeAlreadyUsed

```solidity
error OvaReferralCodeAlreadyUsed()
```

### OvaReferralAlreadyCreatedACode

```solidity
error OvaReferralAlreadyCreatedACode()
```

### OvaReferralStakingPoolsNotSet

```solidity
error OvaReferralStakingPoolsNotSet()
```

### onlyTracker

```solidity
modifier onlyTracker()
```

### constructor

```solidity
constructor(address admin) public
```

The constructor

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| admin | address | The contract admin |

### getStakingPools

```solidity
function getStakingPools() external view returns (address[])
```

### setStakingPools

```solidity
function setStakingPools(address[] pools_) external
```

### consumeReferral

```solidity
function consumeReferral(string code, address consumer) external
```

Consume a referral code. This action will harvest all the user positions in the staking pools

_Code holders can not use any code
Staking pools must be set_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| code | string | The referral code |
| consumer | address | The referral consumer |

### track

```solidity
function track(address source, uint256 amount) external
```

Track a new points update

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| source | address | The user address to track |
| amount | uint256 | The amount of points to be tracked |

### addPointsTracker

```solidity
function addPointsTracker(address tracker) external
```

Add a new points tracker

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tracker | address | The tracker address |

### addCode

```solidity
function addCode(string code, address holder) external
```

Add a new referral code

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| code | string | The tracker address |
| holder | address | The code owner |

### addCodeSelf

```solidity
function addCodeSelf(string code) external
```

Add a new referral code for the caller

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| code | string | The tracker address |

### removePointsTracker

```solidity
function removePointsTracker(address tracker) external
```

Remove a points tracker

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tracker | address | The tracker address |

### seeReferred

```solidity
function seeReferred(address source) external view returns (address[])
```

Retrieve all the referred user for a given address

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| source | address | The query key |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | address[] | All the referred user addresses |

### seeReferredByCode

```solidity
function seeReferredByCode(string code) external view returns (address[])
```

Retrieve all the referred user for a given address

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| code | string | The query key |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | address[] | All the referred user addresses |

### codeTotalPoints

```solidity
function codeTotalPoints(string code) external view returns (uint256)
```

Retrieve all points earned by a given code

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| code | string | The referral code |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | The total points |

### allCodes

```solidity
function allCodes() external view returns (string[])
```

Retrieve all the active referral codes

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | string[] | The active referral codes |

### totalCodes

```solidity
function totalCodes() external view returns (uint256)
```

Retrieve referral codes count

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | The active referral codes count |

## StakedUSDO

_This contract is intended to be inherited in order to define custom vesting aka cooldowns policies_

### vestingAmount

```solidity
uint256 vestingAmount
```

The amount of the last asset distribution from the controller contract into this
contract + any unvested remainder at that time

### lastDistributionTimestamp

```solidity
uint256 lastDistributionTimestamp
```

The timestamp of the last asset distribution from the controller contract into this contract

### notZero

```solidity
modifier notZero(uint256 amount)
```

ensure input amount nonzero

### notOwner

```solidity
modifier notOwner(address target)
```

ensures blacklist target is not owner

### constructor

```solidity
constructor(contract IERC20 asset, address initialRewarder, address admin, uint256 vestingPeriod) internal
```

Constructor for StakedUSDO contract.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| asset | contract IERC20 | The address of the USDO token. |
| initialRewarder | address | The address of the initial rewarder. |
| admin | address | The address of the admin role. |
| vestingPeriod | uint256 | The rewards vesting period |

### transferInRewards

```solidity
function transferInRewards(uint256 amount) external
```

Allows the owner to transfer rewards from the controller contract into this contract.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount | uint256 | The amount of rewards to transfer. |

### addToBlacklist

```solidity
function addToBlacklist(address target, bool isFullBlacklisting) external
```

Allows the owner (DEFAULT_ADMIN_ROLE) and blacklist managers to blacklist addresses.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| target | address | The address to blacklist. |
| isFullBlacklisting | bool | Soft or full blacklisting level. |

### removeFromBlacklist

```solidity
function removeFromBlacklist(address target, bool isFullBlacklisting) external
```

Allows the owner (DEFAULT_ADMIN_ROLE) and blacklist managers to un-blacklist addresses.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| target | address | The address to un-blacklist. |
| isFullBlacklisting | bool | Soft or full blacklisting level. |

### rescueTokens

```solidity
function rescueTokens(address token, uint256 amount, address to) external
```

Allows the owner to rescue tokens accidentally sent to the contract.
Note that the owner cannot rescue USDO tokens because they functionally sit here
and belong to stakers but can rescue staked USDO as they should never actually
sit in this contract and a staker may well transfer them here by accident.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| token | address | The token to be rescued. |
| amount | uint256 | The amount of tokens to be rescued. |
| to | address | Where to send rescued tokens |

### redistributeLockedAmount

```solidity
function redistributeLockedAmount(address from, address to) external
```

_Burns the full restricted user amount and mints to the desired owner address._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| from | address | The address to burn the entire balance, with the FULL_RESTRICTED_STAKER_ROLE |
| to | address | The address to mint the entire balance of "from" parameter. |

### totalAssets

```solidity
function totalAssets() public view returns (uint256)
```

Returns the amount of USDO tokens that are vested in the contract.

### getUnvestedAmount

```solidity
function getUnvestedAmount() public view returns (uint256)
```

Returns the amount of USDO tokens that are unvested in the contract.

### decimals

```solidity
function decimals() public pure returns (uint8)
```

_Necessary because both ERC20 (from ERC20Permit) and ERC4626 declare decimals()_

### renounceRole

```solidity
function renounceRole(bytes32, address) public virtual
```

_Remove renounce role access from AccessControl, to prevent users to resign roles._

### _checkMinShares

```solidity
function _checkMinShares() internal view
```

ensures a small non-zero amount of shares does not remain, exposing to donation attack

### _deposit

```solidity
function _deposit(address caller, address receiver, uint256 assets, uint256 shares) internal
```

_Deposit/mint common workflow._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| caller | address | sender of assets |
| receiver | address | where to send shares |
| assets | uint256 | assets to deposit |
| shares | uint256 | shares to mint |

### _withdraw

```solidity
function _withdraw(address caller, address receiver, address sharesOwner, uint256 assets, uint256 shares) internal
```

_Withdraw/redeem common workflow._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| caller | address | tx sender |
| receiver | address | where to send assets |
| sharesOwner | address | where to burn shares from |
| assets | uint256 | asset amount to transfer out |
| shares | uint256 | shares to burn |

### _updateVestingAmount

```solidity
function _updateVestingAmount(uint256 newVestingAmount) internal
```

### _update

```solidity
function _update(address from, address to, uint256 value) internal virtual
```

_See {IERC20-_update}._

## StakedUSDOFront

The StakedUSDOFront contract allows users to
stake USDO tokens and earn a portion of protocol yield. This is the public entrypoint

_If cooldown duration is set to
zero, the StakedUSDOFront behavior changes to follow ERC4626 standard and
disables cooldownShares and cooldownAssets methods. If cooldown duration is
greater than zero, the ERC4626 withdrawal and redeem functions are disabled,
breaking the ERC4626 standard, and enabling the cooldownShares and the
cooldownAssets functions._

### cooldowns

```solidity
mapping(address => struct UserCooldown) cooldowns
```

### SILO

```solidity
contract USDOSilo SILO
```

### MAX_COOLDOWN_DURATION

```solidity
uint24 MAX_COOLDOWN_DURATION
```

### cooldownDuration

```solidity
uint24 cooldownDuration
```

### ensureCooldownOff

```solidity
modifier ensureCooldownOff()
```

ensure cooldownDuration is zero

### ensureCooldownOn

```solidity
modifier ensureCooldownOn()
```

ensure cooldownDuration is gt 0

### constructor

```solidity
constructor(contract IERC20 _asset, address initialRewarder, address _owner, uint256 vestingPeriod) public
```

Constructor for StakedUSDOFront contract.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _asset | contract IERC20 | The address of the USDO token. |
| initialRewarder | address | The address of the initial rewarder. |
| _owner | address | The address of the admin role. |
| vestingPeriod | uint256 | The rewards vesting period |

### withdraw

```solidity
function withdraw(uint256 assets, address receiver, address _owner) public virtual returns (uint256)
```

_See {IERC4626-withdraw}._

### redeem

```solidity
function redeem(uint256 shares, address receiver, address _owner) public virtual returns (uint256)
```

_See {IERC4626-redeem}._

### unstake

```solidity
function unstake(address receiver) external
```

Claim the staking amount after the cooldown has finished. The address can only retire the full amount of assets.

_unstake can be called after cooldown have been set to 0, to let accounts to be able to claim remaining assets locked at Silo_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| receiver | address | Address to send the assets by the staker |

### cooldownAssets

```solidity
function cooldownAssets(uint256 assets) external returns (uint256 shares)
```

redeem assets and starts a cooldown to claim the converted underlying asset

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| assets | uint256 | assets to redeem |

### cooldownShares

```solidity
function cooldownShares(uint256 shares) external returns (uint256 assets)
```

redeem shares into assets and starts a cooldown to claim the converted underlying asset

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| shares | uint256 | shares to redeem |

### setCooldownDuration

```solidity
function setCooldownDuration(uint24 duration) external
```

Set cooldown duration. If cooldown duration is set to zero, the StakedUSDOFront behavior changes to follow ERC4626 standard and disables
cooldownShares and cooldownAssets methods. If cooldown duration is greater than zero, the ERC4626 withdrawal and redeem functions are disabled,
breaking the ERC4626 standard, and enabling the cooldownShares and the cooldownAssets functions.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| duration | uint24 | Duration of the cooldown |

## USDO

USDO The starting point...

### blacklist

```solidity
mapping(address => bool) blacklist
```

blacklisted accounts

### notDisabled

```solidity
modifier notDisabled(address account)
```

### constructor

```solidity
constructor(address admin, struct MintRedeemManagerTypes.StableCoin usdc_, struct MintRedeemManagerTypes.StableCoin usdt_, uint256 maxMintPerBlock_, uint256 maxRedeemPerBlock_) public
```

### mint

```solidity
function mint(struct MintRedeemManagerTypes.Order order) external
```

Mint tokens

_Can be paused by the admin_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| order | struct MintRedeemManagerTypes.Order | A struct containing the mint order |

### redeem

```solidity
function redeem(struct MintRedeemManagerTypes.Order order) external
```

Redeem collateral

_Can not be paused_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| order | struct MintRedeemManagerTypes.Order | A struct containing the mint order |

### disableAccount

```solidity
function disableAccount(address account) external
```

Disable an account from performing transactions

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| account | address | The account to be disabled |

### enableAccount

```solidity
function enableAccount(address account) external
```

Enable an account from performing transactions

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| account | address | The account to be enabled |

### _update

```solidity
function _update(address from, address to, uint256 value) internal
```

_Transfers a `value` amount of tokens from `from` to `to`, or alternatively mints (or burns) if `from`
(or `to`) is the zero address. All customizations to transfers, mints, and burns should be done by overriding
this function.

Emits a {Transfer} event._

## USDOSilo

The Silo allows to store USDO during the stake cooldown process.

### USDOSiloZeroAddressException

```solidity
error USDOSiloZeroAddressException()
```

### constructor

```solidity
constructor(address stakingVault, address USDO) public
```

### onlyStakingVault

```solidity
modifier onlyStakingVault()
```

### withdraw

```solidity
function withdraw(address to, uint256 amount) external
```

## IAirdropOVAReceipt

### RewardsReceived

```solidity
event RewardsReceived(uint256 amount)
```

Event emitted when the rewards are received

### LockedAmountRedistributed

```solidity
event LockedAmountRedistributed(address from, address to, uint256 amount)
```

Event emitted when the balance from an FULL_RESTRICTED_STAKER_ROLE user are redistributed

### InvalidAmount

```solidity
error InvalidAmount()
```

Error emitted shares or assets equal zero.

### InvalidToken

```solidity
error InvalidToken()
```

Error emitted when owner attempts to rescue USDO tokens.

### MinSharesViolation

```solidity
error MinSharesViolation()
```

Error emitted when a small non-zero share amount remains, which risks donations attack

### OperationNotAllowed

```solidity
error OperationNotAllowed()
```

Error emitted when owner is not allowed to perform an operation

### StillVesting

```solidity
error StillVesting()
```

Error emitted when there is still unvested amount

### CantBlacklistOwner

```solidity
error CantBlacklistOwner()
```

Error emitted when owner or blacklist manager attempts to blacklist owner

### InvalidZeroAddress

```solidity
error InvalidZeroAddress()
```

Error emitted when the zero address is given

### rescueTokens

```solidity
function rescueTokens(address token, uint256 amount, address to) external
```

## IMintRedeemManagerDefs

### MintRedeemManagerInvalidZeroAddress

```solidity
error MintRedeemManagerInvalidZeroAddress()
```

### MintRedeemManagerInvalidDecimals

```solidity
error MintRedeemManagerInvalidDecimals()
```

### MintRedeemManagerInvalidAssetAmounts

```solidity
error MintRedeemManagerInvalidAssetAmounts()
```

### MintRedeemManagerDifferentAssetsAmounts

```solidity
error MintRedeemManagerDifferentAssetsAmounts()
```

### MintRedeemManagerUnsupportedAsset

```solidity
error MintRedeemManagerUnsupportedAsset()
```

### MintRedeemManagerMaxMintPerBlockExceeded

```solidity
error MintRedeemManagerMaxMintPerBlockExceeded()
```

### MintRedeemManagerMaxRedeemPerBlockExceeded

```solidity
error MintRedeemManagerMaxRedeemPerBlockExceeded()
```

### MintRedeemManagerSupplyAmountNotReached

```solidity
error MintRedeemManagerSupplyAmountNotReached()
```

### MintRedeemManagerInvalidMaxRedeemAmount

```solidity
error MintRedeemManagerInvalidMaxRedeemAmount()
```

### MintRedeemManagerInvalidBenefactor

```solidity
error MintRedeemManagerInvalidBenefactor()
```

## IMintRedeemManagerEvents

### Received

```solidity
event Received(address, uint256)
```

Event emitted when contract receives ETH

### Mint

```solidity
event Mint(address minter, address benefactor, address beneficiary, address collateral_usdc, address collateral_usdt, uint256 collateral_usdc_amount, uint256 collateral_usdt_amount, uint256 usdo_amount)
```

Event emitted when USDO is minted

### Redeem

```solidity
event Redeem(address redeemer, address benefactor, address beneficiary, address collateral_usdc, address collateral_usdt, uint256 collateral_usdc_amount, uint256 collateral_usdt_amount, uint256 usdo_amount)
```

Event emitted when funds are redeemed

### CustodyTransfer

```solidity
event CustodyTransfer(address wallet, address asset, uint256 amount)
```

Event emitted when assets are moved to custody provider wallet

### MaxMintPerBlockChanged

```solidity
event MaxMintPerBlockChanged(uint256 oldMaxMintPerBlock, uint256 newMaxMintPerBlock)
```

Event emitted when the max mint per block is changed

### MaxRedeemPerBlockChanged

```solidity
event MaxRedeemPerBlockChanged(uint256 oldMaxRedeemPerBlock, uint256 newMaxRedeemPerBlock)
```

Event emitted when the max redeem per block is changed

### SuppliedToBacking

```solidity
event SuppliedToBacking(address supplier, uint256 amountUsdc, uint256 amountUsdt)
```

Event emitted when collateral has been supplied to the backing contract

## IOvaReferral

### referredFrom

```solidity
function referredFrom(address user) external view returns (address)
```

### referralCodes

```solidity
function referralCodes(string code) external view returns (address)
```

### seeReferred

```solidity
function seeReferred(address user) external view returns (address[])
```

### generatedPoints

```solidity
function generatedPoints(address user) external view returns (uint256)
```

### track

```solidity
function track(address user, uint256 amount) external
```

### consumeReferral

```solidity
function consumeReferral(string code, address consumer) external
```

## IStakedUSDO

### RewardsReceived

```solidity
event RewardsReceived(uint256 amount)
```

Event emitted when the rewards are received

### LockedAmountRedistributed

```solidity
event LockedAmountRedistributed(address from, address to, uint256 amount)
```

Event emitted when the balance from an FULL_RESTRICTED_STAKER_ROLE user are redistributed

### StakedUSDOInvalidAmount

```solidity
error StakedUSDOInvalidAmount()
```

Error emitted shares or assets equal zero.

### StakedUSDOInvalidToken

```solidity
error StakedUSDOInvalidToken()
```

Error emitted when owner attempts to rescue USDO tokens.

### StakedUSDOMinSharesViolation

```solidity
error StakedUSDOMinSharesViolation()
```

Error emitted when a small non-zero share amount remains, which risks donations attack

### StakedUSDOOperationNotAllowed

```solidity
error StakedUSDOOperationNotAllowed()
```

Error emitted when owner is not allowed to perform an operation

### StakedUSDOStillVesting

```solidity
error StakedUSDOStillVesting()
```

Error emitted when there is still unvested amount

### StakedUSDOCantBlacklistOwner

```solidity
error StakedUSDOCantBlacklistOwner()
```

Error emitted when owner or blacklist manager attempts to blacklist owner

### StakedUSDOInvalidZeroAddress

```solidity
error StakedUSDOInvalidZeroAddress()
```

Error emitted when the zero address is given

### transferInRewards

```solidity
function transferInRewards(uint256 amount) external
```

### rescueTokens

```solidity
function rescueTokens(address token, uint256 amount, address to) external
```

### getUnvestedAmount

```solidity
function getUnvestedAmount() external view returns (uint256)
```

## UserCooldown

```solidity
struct UserCooldown {
  uint104 cooldownEnd;
  uint152 underlyingAmount;
}
```

## IStakedUSDOCooldown

### IStakedUSDOCooldownDurationUpdated

```solidity
event IStakedUSDOCooldownDurationUpdated(uint24 previousDuration, uint24 newDuration)
```

Event emitted when cooldown duration updates

### IStakedUSDOCooldownExcessiveRedeemAmount

```solidity
error IStakedUSDOCooldownExcessiveRedeemAmount()
```

Error emitted when the shares amount to redeem is greater than the shares balance of the owner

### IStakedUSDOCooldownExcessiveWithdrawAmount

```solidity
error IStakedUSDOCooldownExcessiveWithdrawAmount()
```

Error emitted when the shares amount to withdraw is greater than the shares balance of the owner

### IStakedUSDOCooldownInvalidCooldown

```solidity
error IStakedUSDOCooldownInvalidCooldown()
```

Error emitted when cooldown value is invalid

### cooldownAssets

```solidity
function cooldownAssets(uint256 assets) external returns (uint256 shares)
```

### cooldownShares

```solidity
function cooldownShares(uint256 shares) external returns (uint256 assets)
```

### unstake

```solidity
function unstake(address receiver) external
```

### setCooldownDuration

```solidity
function setCooldownDuration(uint24 duration) external
```

## IUSDOBacking

### supply

```solidity
function supply(uint256 amountA, uint256 amountB) external
```

### withdraw

```solidity
function withdraw(uint256 amountA, uint256 amountB) external
```

## IUSDODefs

### USDOZeroAddressException

```solidity
error USDOZeroAddressException()
```

Zero address not allowed

### USDOInvalidDecimals

```solidity
error USDOInvalidDecimals()
```

The asset decimals can not be larger that the underlying decimals

### USDOAccountDisabled

```solidity
error USDOAccountDisabled()
```

An account has been disabled from performing transactions

### DisableAccount

```solidity
event DisableAccount(address account)
```

A blacklist event

### EnableAccount

```solidity
event EnableAccount(address account)
```

A reverted blacklist event

## IUSDOEvents

### MinterUpdated

```solidity
event MinterUpdated(address newMinter, address oldMinter)
```

This event is fired when the minter changes

## IUSDOM

### mint

```solidity
function mint(struct MintRedeemManagerTypes.Order order) external
```

### redeem

```solidity
function redeem(struct MintRedeemManagerTypes.Order order) external
```

## IUSDOMDefs

### ZeroAddressException

```solidity
error ZeroAddressException()
```

Zero address not allowed

## IUSDOSiloDefinitions

### OnlyStakingVault

```solidity
error OnlyStakingVault()
```

Error emitted when the staking vault is not the caller

## MintRedeemManagerTypes

### Order

```solidity
struct Order {
  address benefactor;
  address beneficiary;
  address collateral_usdt;
  address collateral_usdc;
  uint256 collateral_usdt_amount;
  uint256 collateral_usdc_amount;
  uint256 usdo_amount;
}
```

### StableCoin

```solidity
struct StableCoin {
  address addr;
  uint256 decimals;
}
```

## INonfungiblePositionManager

### MintParams

```solidity
struct MintParams {
  address token0;
  address token1;
  uint24 fee;
  int24 tickLower;
  int24 tickUpper;
  uint256 amount0Desired;
  uint256 amount1Desired;
  uint256 amount0Min;
  uint256 amount1Min;
  address recipient;
  uint256 deadline;
}
```

### mint

```solidity
function mint(struct INonfungiblePositionManager.MintParams params) external payable returns (uint256 tokenId, uint128 liquidity, uint256 amount0, uint256 amount1)
```

### IncreaseLiquidityParams

```solidity
struct IncreaseLiquidityParams {
  uint256 tokenId;
  uint256 amount0Desired;
  uint256 amount1Desired;
  uint256 amount0Min;
  uint256 amount1Min;
  uint256 deadline;
}
```

### increaseLiquidity

```solidity
function increaseLiquidity(struct INonfungiblePositionManager.IncreaseLiquidityParams params) external payable returns (uint128 liquidity, uint256 amount0, uint256 amount1)
```

### DecreaseLiquidityParams

```solidity
struct DecreaseLiquidityParams {
  uint256 tokenId;
  uint128 liquidity;
  uint256 amount0Min;
  uint256 amount1Min;
  uint256 deadline;
}
```

### decreaseLiquidity

```solidity
function decreaseLiquidity(struct INonfungiblePositionManager.DecreaseLiquidityParams params) external payable returns (uint256 amount0, uint256 amount1)
```

### CollectParams

```solidity
struct CollectParams {
  uint256 tokenId;
  address recipient;
  uint128 amount0Max;
  uint128 amount1Max;
}
```

### collect

```solidity
function collect(struct INonfungiblePositionManager.CollectParams params) external payable returns (uint256 amount0, uint256 amount1)
```

### safeTransferFrom

```solidity
function safeTransferFrom(address from, address to, uint256 tokenId, bytes data) external
```

### ownerOf

```solidity
function ownerOf(uint256 tokenId) external view returns (address)
```

## ISwapRouter02

### ExactInputSingleParams

```solidity
struct ExactInputSingleParams {
  address tokenIn;
  address tokenOut;
  uint24 fee;
  address recipient;
  uint256 amountIn;
  uint256 amountOutMinimum;
  uint160 sqrtPriceLimitX96;
}
```

### exactInputSingle

```solidity
function exactInputSingle(struct ISwapRouter02.ExactInputSingleParams params) external payable returns (uint256 amountOut)
```

### ExactOutputSingleParams

```solidity
struct ExactOutputSingleParams {
  address tokenIn;
  address tokenOut;
  uint24 fee;
  address recipient;
  uint256 amountOut;
  uint256 amountInMaximum;
  uint160 sqrtPriceLimitX96;
}
```

### exactOutputSingle

```solidity
function exactOutputSingle(struct ISwapRouter02.ExactOutputSingleParams params) external payable returns (uint256 amountIn)
```

## IUniswapV3Staker

### IncentiveKey

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |

```solidity
struct IncentiveKey {
  contract IERC20Minimal rewardToken;
  contract IUniswapV3Pool pool;
  uint256 startTime;
  uint256 endTime;
  address refundee;
}
```

### maxIncentiveDuration

```solidity
function maxIncentiveDuration() external view returns (uint256)
```

The max duration of an incentive in seconds

### maxIncentiveStartLeadTime

```solidity
function maxIncentiveStartLeadTime() external view returns (uint256)
```

The max amount of seconds into the future the incentive startTime can be set

### incentives

```solidity
function incentives(bytes32 incentiveId) external view returns (uint256 totalRewardUnclaimed, uint160 totalSecondsClaimedX128, uint96 numberOfStakes)
```

Represents a staking incentive

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| incentiveId | bytes32 | The ID of the incentive computed from its parameters |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| totalRewardUnclaimed | uint256 | The amount of reward token not yet claimed by users |
| totalSecondsClaimedX128 | uint160 | Total liquidity-seconds claimed, represented as a UQ32.128 |
| numberOfStakes | uint96 | The count of deposits that are currently staked for the incentive |

### deposits

```solidity
function deposits(uint256 tokenId) external view returns (address owner, uint48 numberOfStakes, int24 tickLower, int24 tickUpper)
```

Returns information about a deposited NFT

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| owner | address | The owner of the deposited NFT |
| numberOfStakes | uint48 | Counter of how many incentives for which the liquidity is staked |
| tickLower | int24 | The lower tick of the range |
| tickUpper | int24 | The upper tick of the range |

### stakes

```solidity
function stakes(uint256 tokenId, bytes32 incentiveId) external view returns (uint160 secondsPerLiquidityInsideInitialX128, uint128 liquidity)
```

Returns information about a staked liquidity NFT

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The ID of the staked token |
| incentiveId | bytes32 | The ID of the incentive for which the token is staked |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| secondsPerLiquidityInsideInitialX128 | uint160 | secondsPerLiquidity represented as a UQ32.128 |
| liquidity | uint128 | The amount of liquidity in the NFT as of the last time the rewards were computed |

### stakedLiquidity

```solidity
function stakedLiquidity(bytes32 h) external view returns (uint256)
```

### rewards

```solidity
function rewards(contract IERC20Minimal rewardToken, address owner) external view returns (uint256 rewardsOwed)
```

Returns amounts of reward tokens owed to a given address according to the last time all stakes were updated

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardToken | contract IERC20Minimal | The token for which to check rewards |
| owner | address | The owner for which the rewards owed are checked |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardsOwed | uint256 | The amount of the reward token claimable by the owner |

### createIncentive

```solidity
function createIncentive(struct IUniswapV3Staker.IncentiveKey key, uint256 reward) external
```

Creates a new liquidity mining incentive program

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | Details of the incentive to create |
| reward | uint256 | The amount of reward tokens to be distributed |

### endIncentive

```solidity
function endIncentive(struct IUniswapV3Staker.IncentiveKey key) external returns (uint256 refund)
```

Ends an incentive after the incentive end time has passed and all stakes have been withdrawn

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | Details of the incentive to end |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| refund | uint256 | The remaining reward tokens when the incentive is ended |

### transferDeposit

```solidity
function transferDeposit(uint256 tokenId, address to) external
```

Transfers ownership of a deposit from the sender to the given recipient

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The ID of the token (and the deposit) to transfer |
| to | address | The new owner of the deposit |

### withdrawToken

```solidity
function withdrawToken(uint256 tokenId, address to, bytes data) external
```

Withdraws a Uniswap V3 LP token `tokenId` from this contract to the recipient `to`

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The unique identifier of an Uniswap V3 LP token |
| to | address | The address where the LP token will be sent |
| data | bytes | An optional data array that will be passed along to the `to` address via the NFT safeTransferFrom |

### stakeToken

```solidity
function stakeToken(struct IUniswapV3Staker.IncentiveKey key, uint256 tokenId) external
```

Stakes a Uniswap V3 LP token

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | The key of the incentive for which to stake the NFT |
| tokenId | uint256 | The ID of the token to stake |

### unstakeToken

```solidity
function unstakeToken(struct IUniswapV3Staker.IncentiveKey key, uint256 tokenId) external
```

Unstakes a Uniswap V3 LP token

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | The key of the incentive for which to unstake the NFT |
| tokenId | uint256 | The ID of the token to unstake |

### claimReward

```solidity
function claimReward(contract IERC20Minimal rewardToken, address to, uint256 amountRequested) external returns (uint256 reward)
```

Transfers `amountRequested` of accrued `rewardToken` rewards from the contract to the recipient `to`

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardToken | contract IERC20Minimal | The token being distributed as a reward |
| to | address | The address where claimed rewards will be sent to |
| amountRequested | uint256 | The amount of reward tokens to claim. Claims entire reward amount if set to 0. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| reward | uint256 | The amount of reward tokens claimed |

### getRewardInfo

```solidity
function getRewardInfo(struct IUniswapV3Staker.IncentiveKey key, uint256 tokenId) external view returns (uint256 reward, uint160 secondsInsideX128)
```

Calculates the reward amount that will be received for the given stake

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | The key of the incentive |
| tokenId | uint256 | The ID of the token |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| reward | uint256 | The reward accrued to the NFT for the given incentive thus far |
| secondsInsideX128 | uint160 |  |

## IWETH

### deposit

```solidity
function deposit() external payable
```

### withdraw

```solidity
function withdraw(uint256 amount) external
```

## UNIV3_POSITION_MANAGER

```solidity
address UNIV3_POSITION_MANAGER
```

## UniswapV3LiquidityProxy

_This a test helper contract. Do not use in prod_

### nonfungiblePositionManager

```solidity
contract INonfungiblePositionManager nonfungiblePositionManager
```

### Mint

```solidity
event Mint(uint256 tokenId, uint128 liquidity, uint256 amount0, uint256 amount1, uint24 fee)
```

### onERC721Received

```solidity
function onERC721Received(address operator, address from, uint256 tokenId, bytes) external returns (bytes4)
```

### mintNewPosition

```solidity
function mintNewPosition(address token0, address token1, uint256 amount0ToAdd, uint256 amount1ToAdd, uint24 fee) external returns (uint256 tokenId, uint128 liquidity, uint256 amount0, uint256 amount1)
```

Mint a new liquidity position

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| token0 | address | The first liquidity token |
| token1 | address | The second liquidity token |
| amount0ToAdd | uint256 | The amount of the first token |
| amount1ToAdd | uint256 | The amount of the second token |
| fee | uint24 | The fee amount |

### collectAllFees

```solidity
function collectAllFees(uint256 tokenId) external returns (uint256 amount0, uint256 amount1)
```

Collect a position fees

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The position token id |

### increaseLiquidityCurrentRange

```solidity
function increaseLiquidityCurrentRange(address token0, address token1, uint256 tokenId, uint256 amount0ToAdd, uint256 amount1ToAdd) external returns (uint128 liquidity, uint256 amount0, uint256 amount1)
```

Increase the current range liquidity position

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| token0 | address | The first liquidity token |
| token1 | address | The second liquidity token |
| tokenId | uint256 | The position token id |
| amount0ToAdd | uint256 | The amount of the first token |
| amount1ToAdd | uint256 | The amount of the second token |

### decreaseLiquidityCurrentRange

```solidity
function decreaseLiquidityCurrentRange(uint256 tokenId, uint128 liquidity) external returns (uint256 amount0, uint256 amount1)
```

Decrease the current range liquidity position

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The position token id |
| liquidity | uint128 | The amount of liquidity |

## SWAP_ROUTER_02

```solidity
address SWAP_ROUTER_02
```

## WETH

```solidity
address WETH
```

## DAI

```solidity
address DAI
```

## USDC

```solidity
address USDC
```

## USDT

```solidity
address USDT
```

## FEE

```solidity
uint24 FEE
```

## UniswapV3SingleHopSwap

_This a test helper contract. Do not use in prod_

### swapExactInputSingleHop

```solidity
function swapExactInputSingleHop(uint256 amountIn, uint256 amountOutMin, uint8 code) external
```

### swapExactOutputSingleHop

```solidity
function swapExactOutputSingleHop(uint256 amountOut, uint256 amountInMax, uint8 code) external
```

## Enumerable

This codes were copied from https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/extensions/ERC721Enumerable.sol, and did some changes.

_This implements an optional extension of defined in the EIP that adds
enumerability of all the token ids in the contract as well as all token ids owned by each
account._

### tokenOfOwnerByIndex

```solidity
function tokenOfOwnerByIndex(address owner, uint256 index) public view returns (uint256)
```

### balanceOf

```solidity
function balanceOf(address owner) public view returns (uint256)
```

### addToken

```solidity
function addToken(address from, uint256 tokenId) internal
```

### removeToken

```solidity
function removeToken(address from, uint256 tokenId) internal
```

## MasterChefV3

### PoolInfo

```solidity
struct PoolInfo {
  uint256 allocPoint;
  contract IPancakeV3Pool v3Pool;
  address token0;
  address token1;
  uint24 fee;
  uint256 totalLiquidity;
  uint256 totalBoostLiquidity;
}
```

### UserPositionInfo

```solidity
struct UserPositionInfo {
  uint128 liquidity;
  uint128 boostLiquidity;
  int24 tickLower;
  int24 tickUpper;
  uint256 rewardGrowthInside;
  uint256 reward;
  address user;
  uint256 pid;
  uint256 boostMultiplier;
}
```

### poolLength

```solidity
uint256 poolLength
```

### poolInfo

```solidity
mapping(uint256 => struct MasterChefV3.PoolInfo) poolInfo
```

Info of each MCV3 pool.

### userPositionInfos

```solidity
mapping(uint256 => struct MasterChefV3.UserPositionInfo) userPositionInfos
```

userPositionInfos[tokenId] => UserPositionInfo

_TokenId is unique, and we can query the pid by tokenId._

### v3PoolPid

```solidity
mapping(address => mapping(address => mapping(uint24 => uint256))) v3PoolPid
```

v3PoolPid[token0][token1][fee] => pid

### v3PoolAddressPid

```solidity
mapping(address => uint256) v3PoolAddressPid
```

v3PoolAddressPid[v3PoolAddress] => pid

### CAKE

```solidity
contract IERC20 CAKE
```

Address of CAKE contract.

### WETH

```solidity
address WETH
```

Address of WETH contract.

### receiver

```solidity
address receiver
```

Address of Receiver contract.

### nonfungiblePositionManager

```solidity
contract INonfungiblePositionManager nonfungiblePositionManager
```

### LMPoolDeployer

```solidity
contract ILMPoolDeployer LMPoolDeployer
```

Address of liquidity mining pool deployer contract.

### FARM_BOOSTER

```solidity
contract IFarmBooster FARM_BOOSTER
```

Address of farm booster contract.

### emergency

```solidity
bool emergency
```

Only use for emergency situations.

### totalAllocPoint

```solidity
uint256 totalAllocPoint
```

Total allocation points. Must be the sum of all pools' allocation points.

### latestPeriodNumber

```solidity
uint256 latestPeriodNumber
```

### latestPeriodStartTime

```solidity
uint256 latestPeriodStartTime
```

### latestPeriodEndTime

```solidity
uint256 latestPeriodEndTime
```

### latestPeriodCakePerSecond

```solidity
uint256 latestPeriodCakePerSecond
```

### operatorAddress

```solidity
address operatorAddress
```

Address of the operator.

### PERIOD_DURATION

```solidity
uint256 PERIOD_DURATION
```

Default period duration.

### MAX_DURATION

```solidity
uint256 MAX_DURATION
```

### MIN_DURATION

```solidity
uint256 MIN_DURATION
```

### PRECISION

```solidity
uint256 PRECISION
```

### BOOST_PRECISION

```solidity
uint256 BOOST_PRECISION
```

Basic boost factor, none boosted user's boost factor

### MAX_BOOST_PRECISION

```solidity
uint256 MAX_BOOST_PRECISION
```

Hard limit for maxmium boost factor, it must greater than BOOST_PRECISION

### Q128

```solidity
uint256 Q128
```

### MAX_U256

```solidity
uint256 MAX_U256
```

### cakeAmountBelongToMC

```solidity
uint256 cakeAmountBelongToMC
```

Record the cake amount belong to MasterChefV3.

### ZeroAddress

```solidity
error ZeroAddress()
```

### NotOwnerOrOperator

```solidity
error NotOwnerOrOperator()
```

### NoBalance

```solidity
error NoBalance()
```

### NotPancakeNFT

```solidity
error NotPancakeNFT()
```

### InvalidNFT

```solidity
error InvalidNFT()
```

### NotOwner

```solidity
error NotOwner()
```

### NoLiquidity

```solidity
error NoLiquidity()
```

### InvalidPeriodDuration

```solidity
error InvalidPeriodDuration()
```

### NoLMPool

```solidity
error NoLMPool()
```

### InvalidPid

```solidity
error InvalidPid()
```

### DuplicatedPool

```solidity
error DuplicatedPool(uint256 pid)
```

### NotEmpty

```solidity
error NotEmpty()
```

### WrongReceiver

```solidity
error WrongReceiver()
```

### InconsistentAmount

```solidity
error InconsistentAmount()
```

### InsufficientAmount

```solidity
error InsufficientAmount()
```

### AddPool

```solidity
event AddPool(uint256 pid, uint256 allocPoint, contract IPancakeV3Pool v3Pool, contract ILMPool lmPool)
```

### SetPool

```solidity
event SetPool(uint256 pid, uint256 allocPoint)
```

### Deposit

```solidity
event Deposit(address from, uint256 pid, uint256 tokenId, uint256 liquidity, int24 tickLower, int24 tickUpper)
```

### Withdraw

```solidity
event Withdraw(address from, address to, uint256 pid, uint256 tokenId)
```

### UpdateLiquidity

```solidity
event UpdateLiquidity(address from, uint256 pid, uint256 tokenId, int128 liquidity, int24 tickLower, int24 tickUpper)
```

### NewOperatorAddress

```solidity
event NewOperatorAddress(address operator)
```

### NewLMPoolDeployerAddress

```solidity
event NewLMPoolDeployerAddress(address deployer)
```

### NewReceiver

```solidity
event NewReceiver(address receiver)
```

### NewPeriodDuration

```solidity
event NewPeriodDuration(uint256 periodDuration)
```

### Harvest

```solidity
event Harvest(address sender, address to, uint256 pid, uint256 tokenId, uint256 reward)
```

### NewUpkeepPeriod

```solidity
event NewUpkeepPeriod(uint256 periodNumber, uint256 startTime, uint256 endTime, uint256 cakePerSecond, uint256 cakeAmount)
```

### UpdateUpkeepPeriod

```solidity
event UpdateUpkeepPeriod(uint256 periodNumber, uint256 oldEndTime, uint256 newEndTime, uint256 remainingCake)
```

### UpdateFarmBoostContract

```solidity
event UpdateFarmBoostContract(address farmBoostContract)
```

### SetEmergency

```solidity
event SetEmergency(bool emergency)
```

### onlyOwnerOrOperator

```solidity
modifier onlyOwnerOrOperator()
```

### onlyValidPid

```solidity
modifier onlyValidPid(uint256 _pid)
```

### onlyReceiver

```solidity
modifier onlyReceiver()
```

### onlyBoostContract

```solidity
modifier onlyBoostContract()
```

_Throws if caller is not the boost contract._

### constructor

```solidity
constructor(contract IERC20 _CAKE, contract INonfungiblePositionManager _nonfungiblePositionManager, address _WETH) public
```

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _CAKE | contract IERC20 | The CAKE token contract address. |
| _nonfungiblePositionManager | contract INonfungiblePositionManager | the NFT position manager contract address. |
| _WETH | address |  |

### getLatestPeriodInfoByPid

```solidity
function getLatestPeriodInfoByPid(uint256 _pid) public view returns (uint256 cakePerSecond, uint256 endTime)
```

Returns the cake per second , period end time.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _pid | uint256 | The pool pid. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| cakePerSecond | uint256 | Cake reward per second. |
| endTime | uint256 | Period end time. |

### getLatestPeriodInfo

```solidity
function getLatestPeriodInfo(address _v3Pool) public view returns (uint256 cakePerSecond, uint256 endTime)
```

Returns the cake per second , period end time. This is for liquidity mining pool.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _v3Pool | address | Address of the V3 pool. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| cakePerSecond | uint256 | Cake reward per second. |
| endTime | uint256 | Period end time. |

### pendingCake

```solidity
function pendingCake(uint256 _tokenId) external view returns (uint256 reward)
```

View function for checking pending CAKE rewards.

_The pending cake amount is based on the last state in LMPool. The actual amount will happen whenever liquidity changes or harvest._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _tokenId | uint256 | Token Id of NFT. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| reward | uint256 | Pending reward. |

### setEmergency

```solidity
function setEmergency(bool _emergency) external
```

For emergency use only.

### setReceiver

```solidity
function setReceiver(address _receiver) external
```

### setLMPoolDeployer

```solidity
function setLMPoolDeployer(contract ILMPoolDeployer _LMPoolDeployer) external
```

### add

```solidity
function add(uint256 _allocPoint, contract IPancakeV3Pool _v3Pool, bool _withUpdate) external
```

Add a new pool. Can only be called by the owner.
One v3 pool can only create one pool.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _allocPoint | uint256 | Number of allocation points for the new pool. |
| _v3Pool | contract IPancakeV3Pool | Address of the V3 pool. |
| _withUpdate | bool | Whether call "massUpdatePools" operation. |

### set

```solidity
function set(uint256 _pid, uint256 _allocPoint, bool _withUpdate) external
```

Update the given pool's CAKE allocation point. Can only be called by the owner.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _pid | uint256 | The id of the pool. See `poolInfo`. |
| _allocPoint | uint256 | New number of allocation points for the pool. |
| _withUpdate | bool | Whether call "massUpdatePools" operation. |

### DepositCache

```solidity
struct DepositCache {
  address token0;
  address token1;
  uint24 fee;
  int24 tickLower;
  int24 tickUpper;
  uint128 liquidity;
}
```

### onERC721Received

```solidity
function onERC721Received(address, address _from, uint256 _tokenId, bytes) external returns (bytes4)
```

Upon receiving a ERC721

### harvest

```solidity
function harvest(uint256 _tokenId, address _to) external returns (uint256 reward)
```

harvest cake from pool.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _tokenId | uint256 | Token Id of NFT. |
| _to | address | Address to. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| reward | uint256 | Cake reward. |

### harvestOperation

```solidity
function harvestOperation(struct MasterChefV3.UserPositionInfo positionInfo, uint256 _tokenId, address _to) internal returns (uint256 reward)
```

### withdraw

```solidity
function withdraw(uint256 _tokenId, address _to) external returns (uint256 reward)
```

Withdraw LP tokens from pool.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _tokenId | uint256 | Token Id of NFT to deposit. |
| _to | address | Address to which NFT token to withdraw. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| reward | uint256 | Cake reward. |

### updateLiquidity

```solidity
function updateLiquidity(uint256 _tokenId) external
```

Update liquidity for the NFT position.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _tokenId | uint256 | Token Id of NFT to update. |

### updateBoostMultiplier

```solidity
function updateBoostMultiplier(uint256 _tokenId, uint256 _newMultiplier) external
```

Update farm boost multiplier for the NFT position.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _tokenId | uint256 | Token Id of NFT to update. |
| _newMultiplier | uint256 | New boost multiplier. |

### updateLiquidityOperation

```solidity
function updateLiquidityOperation(struct MasterChefV3.UserPositionInfo positionInfo, uint256 _tokenId, uint256 _newMultiplier) internal
```

### increaseLiquidity

```solidity
function increaseLiquidity(struct INonfungiblePositionManagerStruct.IncreaseLiquidityParams params) external payable returns (uint128 liquidity, uint256 amount0, uint256 amount1)
```

Increases the amount of liquidity in a position, with tokens paid by the `msg.sender`

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| params | struct INonfungiblePositionManagerStruct.IncreaseLiquidityParams | tokenId The ID of the token for which liquidity is being increased, amount0Desired The desired amount of token0 to be spent, amount1Desired The desired amount of token1 to be spent, amount0Min The minimum amount of token0 to spend, which serves as a slippage check, amount1Min The minimum amount of token1 to spend, which serves as a slippage check, deadline The time by which the transaction must be included to effect the change |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| liquidity | uint128 | The new liquidity amount as a result of the increase |
| amount0 | uint256 | The amount of token0 to acheive resulting liquidity |
| amount1 | uint256 | The amount of token1 to acheive resulting liquidity |

### pay

```solidity
function pay(address _token, uint256 _amount) internal
```

Pay.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _token | address | The token to pay |
| _amount | uint256 | The amount to pay |

### refund

```solidity
function refund(address _token, uint256 _amount) internal
```

Refund.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _token | address | The token to refund |
| _amount | uint256 | The amount to refund |

### decreaseLiquidity

```solidity
function decreaseLiquidity(struct INonfungiblePositionManagerStruct.DecreaseLiquidityParams params) external returns (uint256 amount0, uint256 amount1)
```

Decreases the amount of liquidity in a position and accounts it to the position

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| params | struct INonfungiblePositionManagerStruct.DecreaseLiquidityParams | tokenId The ID of the token for which liquidity is being decreased, amount The amount by which liquidity will be decreased, amount0Min The minimum amount of token0 that should be accounted for the burned liquidity, amount1Min The minimum amount of token1 that should be accounted for the burned liquidity, deadline The time by which the transaction must be included to effect the change |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount0 | uint256 | The amount of token0 accounted to the position's tokens owed |
| amount1 | uint256 | The amount of token1 accounted to the position's tokens owed |

### collect

```solidity
function collect(struct INonfungiblePositionManagerStruct.CollectParams params) external returns (uint256 amount0, uint256 amount1)
```

Collects up to a maximum amount of fees owed to a specific position to the recipient

_Warning!!! Please make sure to use multicall to call unwrapWETH9 or sweepToken when set recipient address(0), or you will lose your funds.
amount0Max The maximum amount of token0 to collect,
amount1Max The maximum amount of token1 to collect_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| params | struct INonfungiblePositionManagerStruct.CollectParams | tokenId The ID of the NFT for which tokens are being collected, recipient The account that should receive the tokens, |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount0 | uint256 | The amount of fees collected in token0 |
| amount1 | uint256 | The amount of fees collected in token1 |

### collectTo

```solidity
function collectTo(struct INonfungiblePositionManagerStruct.CollectParams params, address to) external returns (uint256 amount0, uint256 amount1)
```

Collects up to a maximum amount of fees owed to a specific position to the recipient, then refund.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| params | struct INonfungiblePositionManagerStruct.CollectParams | CollectParams. |
| to | address | Refund recipent. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount0 | uint256 | The amount of fees collected in token0 |
| amount1 | uint256 | The amount of fees collected in token1 |

### transferToken

```solidity
function transferToken(address _token, address _to) internal
```

Transfer token from MasterChef V3.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _token | address | The token to transfer. |
| _to | address | The to address. |

### unwrapWETH9

```solidity
function unwrapWETH9(uint256 amountMinimum, address recipient) external
```

Unwraps the contract's WETH9 balance and sends it to recipient as ETH.

_The amountMinimum parameter prevents malicious contracts from stealing WETH9 from users._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| amountMinimum | uint256 | The minimum amount of WETH9 to unwrap |
| recipient | address | The address receiving ETH |

### sweepToken

```solidity
function sweepToken(address token, uint256 amountMinimum, address recipient) external
```

Transfers the full amount of a token held by this contract to recipient

_The amountMinimum parameter prevents malicious contracts from stealing the token from users_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| token | address | The contract address of the token which will be transferred to `recipient` |
| amountMinimum | uint256 | The minimum amount of token required for a transfer |
| recipient | address | The destination address of the token |

### burn

```solidity
function burn(uint256 _tokenId) external
```

Burns a token ID, which deletes it from the NFT contract. The token must have 0 liquidity and all tokens
must be collected first.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _tokenId | uint256 | The ID of the token that is being burned |

### upkeep

```solidity
function upkeep(uint256 _amount, uint256 _duration, bool _withUpdate) external
```

Upkeep period.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _amount | uint256 | The amount of cake injected. |
| _duration | uint256 | The period duration. |
| _withUpdate | bool | Whether call "massUpdatePools" operation. |

### massUpdatePools

```solidity
function massUpdatePools() internal
```

Update cake reward for all the liquidity mining pool.

### updatePools

```solidity
function updatePools(uint256[] pids) external
```

Update cake reward for the liquidity mining pool.

_Avoid too many pools, and a single transaction cannot be fully executed for all pools._

### setOperator

```solidity
function setOperator(address _operatorAddress) external
```

Set operator address.

_Callable by owner_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _operatorAddress | address | New operator address. |

### setPeriodDuration

```solidity
function setPeriodDuration(uint256 _periodDuration) external
```

Set period duration.

_Callable by owner_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _periodDuration | uint256 | New period duration. |

### updateFarmBoostContract

```solidity
function updateFarmBoostContract(address _newFarmBoostContract) external
```

Update farm boost contract address.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _newFarmBoostContract | address | The new farm booster address. |

### safeTransferETH

```solidity
function safeTransferETH(address to, uint256 value) internal
```

Transfer ETH in a safe way

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| to | address |  |
| value | uint256 |  |

### _safeTransfer

```solidity
function _safeTransfer(address _to, uint256 _amount) internal
```

Safe Transfer CAKE.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _to | address | The CAKE receiver address. |
| _amount | uint256 | Transfer CAKE amounts. |

### receive

```solidity
receive() external payable
```

## IFarmBooster

### getUserMultiplier

```solidity
function getUserMultiplier(uint256 _tokenId) external view returns (uint256)
```

### whiteList

```solidity
function whiteList(uint256 _pid) external view returns (bool)
```

### updatePositionBoostMultiplier

```solidity
function updatePositionBoostMultiplier(uint256 _tokenId) external returns (uint256 _multiplier)
```

### removeBoostMultiplier

```solidity
function removeBoostMultiplier(address _user, uint256 _tokenId, uint256 _pid) external
```

## ILMPool

### updatePosition

```solidity
function updatePosition(int24 tickLower, int24 tickUpper, int128 liquidityDelta) external
```

### getRewardGrowthInside

```solidity
function getRewardGrowthInside(int24 tickLower, int24 tickUpper) external view returns (uint256 rewardGrowthInsideX128)
```

### accumulateReward

```solidity
function accumulateReward(uint32 currTimestamp) external
```

## ILMPoolDeployer

### deploy

```solidity
function deploy(contract IPancakeV3Pool pool) external returns (contract ILMPool lmPool)
```

## IMasterChefV2

### deposit

```solidity
function deposit(uint256 _pid, uint256 _amount) external
```

### withdraw

```solidity
function withdraw(uint256 _pid, uint256 _amount) external
```

### pendingCake

```solidity
function pendingCake(uint256 _pid, address _user) external view returns (uint256)
```

### userInfo

```solidity
function userInfo(uint256 _pid, address _user) external view returns (uint256, uint256, uint256)
```

### emergencyWithdraw

```solidity
function emergencyWithdraw(uint256 _pid) external
```

### updateBoostMultiplier

```solidity
function updateBoostMultiplier(address _user, uint256 _pid, uint256 _newBoostMulti) external
```

## INonfungiblePositionManager

### positions

```solidity
function positions(uint256 tokenId) external view returns (uint96 nonce, address operator, address token0, address token1, uint24 fee, int24 tickLower, int24 tickUpper, uint128 liquidity, uint256 feeGrowthInside0LastX128, uint256 feeGrowthInside1LastX128, uint128 tokensOwed0, uint128 tokensOwed1)
```

Returns the position information associated with a given token ID.

_Throws if the token ID is not valid._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The ID of the token that represents the position |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| nonce | uint96 | The nonce for permits |
| operator | address | The address that is approved for spending |
| token0 | address | The address of the token0 for a specific pool |
| token1 | address | The address of the token1 for a specific pool |
| fee | uint24 | The fee associated with the pool |
| tickLower | int24 | The lower end of the tick range for the position |
| tickUpper | int24 | The higher end of the tick range for the position |
| liquidity | uint128 | The liquidity of the position |
| feeGrowthInside0LastX128 | uint256 | The fee growth of token0 as of the last action on the individual position |
| feeGrowthInside1LastX128 | uint256 | The fee growth of token1 as of the last action on the individual position |
| tokensOwed0 | uint128 | The uncollected amount of token0 owed to the position as of the last computation |
| tokensOwed1 | uint128 | The uncollected amount of token1 owed to the position as of the last computation |

### increaseLiquidity

```solidity
function increaseLiquidity(struct INonfungiblePositionManagerStruct.IncreaseLiquidityParams params) external payable returns (uint128 liquidity, uint256 amount0, uint256 amount1)
```

Increases the amount of liquidity in a position, with tokens paid by the `msg.sender`

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| params | struct INonfungiblePositionManagerStruct.IncreaseLiquidityParams | tokenId The ID of the token for which liquidity is being increased, amount0Desired The desired amount of token0 to be spent, amount1Desired The desired amount of token1 to be spent, amount0Min The minimum amount of token0 to spend, which serves as a slippage check, amount1Min The minimum amount of token1 to spend, which serves as a slippage check, deadline The time by which the transaction must be included to effect the change |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| liquidity | uint128 | The new liquidity amount as a result of the increase |
| amount0 | uint256 | The amount of token0 to acheive resulting liquidity |
| amount1 | uint256 | The amount of token1 to acheive resulting liquidity |

### decreaseLiquidity

```solidity
function decreaseLiquidity(struct INonfungiblePositionManagerStruct.DecreaseLiquidityParams params) external payable returns (uint256 amount0, uint256 amount1)
```

Decreases the amount of liquidity in a position and accounts it to the position

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| params | struct INonfungiblePositionManagerStruct.DecreaseLiquidityParams | tokenId The ID of the token for which liquidity is being decreased, amount The amount by which liquidity will be decreased, amount0Min The minimum amount of token0 that should be accounted for the burned liquidity, amount1Min The minimum amount of token1 that should be accounted for the burned liquidity, deadline The time by which the transaction must be included to effect the change |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount0 | uint256 | The amount of token0 accounted to the position's tokens owed |
| amount1 | uint256 | The amount of token1 accounted to the position's tokens owed |

### collect

```solidity
function collect(struct INonfungiblePositionManagerStruct.CollectParams params) external payable returns (uint256 amount0, uint256 amount1)
```

Collects up to a maximum amount of fees owed to a specific position to the recipient

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| params | struct INonfungiblePositionManagerStruct.CollectParams | tokenId The ID of the NFT for which tokens are being collected, recipient The account that should receive the tokens, amount0Max The maximum amount of token0 to collect, amount1Max The maximum amount of token1 to collect |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount0 | uint256 | The amount of fees collected in token0 |
| amount1 | uint256 | The amount of fees collected in token1 |

### burn

```solidity
function burn(uint256 tokenId) external payable
```

Burns a token ID, which deletes it from the NFT contract. The token must have 0 liquidity and all tokens
must be collected first.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The ID of the token that is being burned |

### refundETH

```solidity
function refundETH() external payable
```

## INonfungiblePositionManagerStruct

### IncreaseLiquidityParams

```solidity
struct IncreaseLiquidityParams {
  uint256 tokenId;
  uint256 amount0Desired;
  uint256 amount1Desired;
  uint256 amount0Min;
  uint256 amount1Min;
  uint256 deadline;
}
```

### DecreaseLiquidityParams

```solidity
struct DecreaseLiquidityParams {
  uint256 tokenId;
  uint128 liquidity;
  uint256 amount0Min;
  uint256 amount1Min;
  uint256 deadline;
}
```

### CollectParams

```solidity
struct CollectParams {
  uint256 tokenId;
  address recipient;
  uint128 amount0Max;
  uint128 amount1Max;
}
```

## IPancakeV3Pool

### factory

```solidity
function factory() external view returns (address)
```

### token0

```solidity
function token0() external view returns (address)
```

### token1

```solidity
function token1() external view returns (address)
```

### fee

```solidity
function fee() external view returns (uint24)
```

### lmPool

```solidity
function lmPool() external view returns (address)
```

## IWETH

### deposit

```solidity
function deposit() external payable
```

Deposit ether to get wrapped ether

### withdraw

```solidity
function withdraw(uint256) external
```

Withdraw wrapped ether to get ether

## SafeCast

_Wrappers over Solidity's uintXX/intXX casting operators with added overflow
checks.

Downcasting from uint256/int256 in Solidity does not revert on overflow. This can
easily result in undesired exploitation or bugs, since developers usually
assume that overflows raise errors. `SafeCast` restores this intuition by
reverting the transaction when such an operation overflows.

Using this library instead of the unchecked operations eliminates an entire
class of bugs, so it's recommended to use it always.

Can be combined with {SafeMath} and {SignedSafeMath} to extend it to smaller types, by performing
all math on `uint256` and `int256` and then downcasting._

### toUint128

```solidity
function toUint128(uint256 value) internal pure returns (uint128)
```

_Returns the downcasted uint128 from uint256, reverting on
overflow (when the input is greater than largest uint128).

Counterpart to Solidity's `uint128` operator.

Requirements:

- input must fit into 128 bits_

## Address

_Collection of functions related to the address type_

### isContract

```solidity
function isContract(address account) internal view returns (bool)
```

_Returns true if `account` is a contract.

[IMPORTANT]
====
It is unsafe to assume that an address for which this function returns
false is an externally-owned account (EOA) and not a contract.

Among others, `isContract` will return false for the following
types of addresses:

 - an externally-owned account
 - a contract in construction
 - an address where a contract will be created
 - an address where a contract lived, but was destroyed
====

[IMPORTANT]
====
You shouldn't rely on `isContract` to protect against flash loan attacks!

Preventing calls from contracts is highly discouraged. It breaks composability, breaks support for smart wallets
like Gnosis Safe, and does not provide security since it can be circumvented by calling from a contract
constructor.
====_

### sendValue

```solidity
function sendValue(address payable recipient, uint256 amount) internal
```

_Replacement for Solidity's `transfer`: sends `amount` wei to
`recipient`, forwarding all available gas and reverting on errors.

https://eips.ethereum.org/EIPS/eip-1884[EIP1884] increases the gas cost
of certain opcodes, possibly making contracts go over the 2300 gas limit
imposed by `transfer`, making them unable to receive funds via
`transfer`. {sendValue} removes this limitation.

https://diligence.consensys.net/posts/2019/09/stop-using-soliditys-transfer-now/[Learn more].

IMPORTANT: because control is transferred to `recipient`, care must be
taken to not create reentrancy vulnerabilities. Consider using
{ReentrancyGuard} or the
https://solidity.readthedocs.io/en/v0.5.11/security-considerations.html#use-the-checks-effects-interactions-pattern[checks-effects-interactions pattern]._

### functionCall

```solidity
function functionCall(address target, bytes data) internal returns (bytes)
```

_Performs a Solidity function call using a low level `call`. A
plain `call` is an unsafe replacement for a function call: use this
function instead.

If `target` reverts with a revert reason, it is bubbled up by this
function (like regular Solidity function calls).

Returns the raw returned data. To convert to the expected return value,
use https://solidity.readthedocs.io/en/latest/units-and-global-variables.html?highlight=abi.decode#abi-encoding-and-decoding-functions[`abi.decode`].

Requirements:

- `target` must be a contract.
- calling `target` with `data` must not revert.

_Available since v3.1.__

### functionCall

```solidity
function functionCall(address target, bytes data, string errorMessage) internal returns (bytes)
```

_Same as {xref-Address-functionCall-address-bytes-}[`functionCall`], but with
`errorMessage` as a fallback revert reason when `target` reverts.

_Available since v3.1.__

### functionCallWithValue

```solidity
function functionCallWithValue(address target, bytes data, uint256 value) internal returns (bytes)
```

_Same as {xref-Address-functionCall-address-bytes-}[`functionCall`],
but also transferring `value` wei to `target`.

Requirements:

- the calling contract must have an ETH balance of at least `value`.
- the called Solidity function must be `payable`.

_Available since v3.1.__

### functionCallWithValue

```solidity
function functionCallWithValue(address target, bytes data, uint256 value, string errorMessage) internal returns (bytes)
```

_Same as {xref-Address-functionCallWithValue-address-bytes-uint256-}[`functionCallWithValue`], but
with `errorMessage` as a fallback revert reason when `target` reverts.

_Available since v3.1.__

### functionStaticCall

```solidity
function functionStaticCall(address target, bytes data) internal view returns (bytes)
```

_Same as {xref-Address-functionCall-address-bytes-}[`functionCall`],
but performing a static call.

_Available since v3.3.__

### functionStaticCall

```solidity
function functionStaticCall(address target, bytes data, string errorMessage) internal view returns (bytes)
```

_Same as {xref-Address-functionCall-address-bytes-string-}[`functionCall`],
but performing a static call.

_Available since v3.3.__

### functionDelegateCall

```solidity
function functionDelegateCall(address target, bytes data) internal returns (bytes)
```

_Same as {xref-Address-functionCall-address-bytes-}[`functionCall`],
but performing a delegate call.

_Available since v3.4.__

### functionDelegateCall

```solidity
function functionDelegateCall(address target, bytes data, string errorMessage) internal returns (bytes)
```

_Same as {xref-Address-functionCall-address-bytes-string-}[`functionCall`],
but performing a delegate call.

_Available since v3.4.__

### verifyCallResultFromTarget

```solidity
function verifyCallResultFromTarget(address target, bool success, bytes returndata, string errorMessage) internal view returns (bytes)
```

_Tool to verify that a low level call to smart-contract was successful, and revert (either by bubbling
the revert reason or using the provided one) in case of unsuccessful call or if target was not a contract.

_Available since v4.8.__

### verifyCallResult

```solidity
function verifyCallResult(bool success, bytes returndata, string errorMessage) internal pure returns (bytes)
```

_Tool to verify that a low level call was successful, and revert if it wasn't, either by bubbling the
revert reason or using the provided one.

_Available since v4.3.__

## Context

_Provides information about the current execution context, including the
sender of the transaction and its data. While these are generally available
via msg.sender and msg.data, they should not be accessed in such a direct
manner, since when dealing with meta-transactions the account sending and
paying for execution may not be the actual sender (as far as an application
is concerned).

This contract is only required for intermediate, library-like contracts._

### _msgSender

```solidity
function _msgSender() internal view virtual returns (address)
```

### _msgData

```solidity
function _msgData() internal view virtual returns (bytes)
```

## IERC165

_Interface of the ERC165 standard, as defined in the
https://eips.ethereum.org/EIPS/eip-165[EIP].

Implementers can declare support of contract interfaces, which can then be
queried by others ({ERC165Checker}).

For an implementation, see {ERC165}._

### supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) external view returns (bool)
```

_Returns true if this contract implements the interface defined by
`interfaceId`. See the corresponding
https://eips.ethereum.org/EIPS/eip-165#how-interfaces-are-identified[EIP section]
to learn more about how these ids are created.

This function call must use less than 30 000 gas._

## IERC20

_Interface of the ERC20 standard as defined in the EIP._

### Transfer

```solidity
event Transfer(address from, address to, uint256 value)
```

_Emitted when `value` tokens are moved from one account (`from`) to
another (`to`).

Note that `value` may be zero._

### Approval

```solidity
event Approval(address owner, address spender, uint256 value)
```

_Emitted when the allowance of a `spender` for an `owner` is set by
a call to {approve}. `value` is the new allowance._

### totalSupply

```solidity
function totalSupply() external view returns (uint256)
```

_Returns the amount of tokens in existence._

### balanceOf

```solidity
function balanceOf(address account) external view returns (uint256)
```

_Returns the amount of tokens owned by `account`._

### transfer

```solidity
function transfer(address to, uint256 amount) external returns (bool)
```

_Moves `amount` tokens from the caller's account to `to`.

Returns a boolean value indicating whether the operation succeeded.

Emits a {Transfer} event._

### allowance

```solidity
function allowance(address owner, address spender) external view returns (uint256)
```

_Returns the remaining number of tokens that `spender` will be
allowed to spend on behalf of `owner` through {transferFrom}. This is
zero by default.

This value changes when {approve} or {transferFrom} are called._

### approve

```solidity
function approve(address spender, uint256 amount) external returns (bool)
```

_Sets `amount` as the allowance of `spender` over the caller's tokens.

Returns a boolean value indicating whether the operation succeeded.

IMPORTANT: Beware that changing an allowance with this method brings the risk
that someone may use both the old and the new allowance by unfortunate
transaction ordering. One possible solution to mitigate this race
condition is to first reduce the spender's allowance to 0 and set the
desired value afterwards:
https://github.com/ethereum/EIPs/issues/20#issuecomment-263524729

Emits an {Approval} event._

### transferFrom

```solidity
function transferFrom(address from, address to, uint256 amount) external returns (bool)
```

_Moves `amount` tokens from `from` to `to` using the
allowance mechanism. `amount` is then deducted from the caller's
allowance.

Returns a boolean value indicating whether the operation succeeded.

Emits a {Transfer} event._

## IERC721

_Required interface of an ERC721 compliant contract._

### Transfer

```solidity
event Transfer(address from, address to, uint256 tokenId)
```

_Emitted when `tokenId` token is transferred from `from` to `to`._

### Approval

```solidity
event Approval(address owner, address approved, uint256 tokenId)
```

_Emitted when `owner` enables `approved` to manage the `tokenId` token._

### ApprovalForAll

```solidity
event ApprovalForAll(address owner, address operator, bool approved)
```

_Emitted when `owner` enables or disables (`approved`) `operator` to manage all of its assets._

### balanceOf

```solidity
function balanceOf(address owner) external view returns (uint256 balance)
```

_Returns the number of tokens in ``owner``'s account._

### ownerOf

```solidity
function ownerOf(uint256 tokenId) external view returns (address owner)
```

_Returns the owner of the `tokenId` token.

Requirements:

- `tokenId` must exist._

### safeTransferFrom

```solidity
function safeTransferFrom(address from, address to, uint256 tokenId, bytes data) external
```

_Safely transfers `tokenId` token from `from` to `to`.

Requirements:

- `from` cannot be the zero address.
- `to` cannot be the zero address.
- `tokenId` token must exist and be owned by `from`.
- If the caller is not `from`, it must be approved to move this token by either {approve} or {setApprovalForAll}.
- If `to` refers to a smart contract, it must implement {IERC721Receiver-onERC721Received}, which is called upon a safe transfer.

Emits a {Transfer} event._

### safeTransferFrom

```solidity
function safeTransferFrom(address from, address to, uint256 tokenId) external
```

_Safely transfers `tokenId` token from `from` to `to`, checking first that contract recipients
are aware of the ERC721 protocol to prevent tokens from being forever locked.

Requirements:

- `from` cannot be the zero address.
- `to` cannot be the zero address.
- `tokenId` token must exist and be owned by `from`.
- If the caller is not `from`, it must have been allowed to move this token by either {approve} or {setApprovalForAll}.
- If `to` refers to a smart contract, it must implement {IERC721Receiver-onERC721Received}, which is called upon a safe transfer.

Emits a {Transfer} event._

### transferFrom

```solidity
function transferFrom(address from, address to, uint256 tokenId) external
```

_Transfers `tokenId` token from `from` to `to`.

WARNING: Note that the caller is responsible to confirm that the recipient is capable of receiving ERC721
or else they may be permanently lost. Usage of {safeTransferFrom} prevents loss, though the caller must
understand this adds an external call which potentially creates a reentrancy vulnerability.

Requirements:

- `from` cannot be the zero address.
- `to` cannot be the zero address.
- `tokenId` token must be owned by `from`.
- If the caller is not `from`, it must be approved to move this token by either {approve} or {setApprovalForAll}.

Emits a {Transfer} event._

### approve

```solidity
function approve(address to, uint256 tokenId) external
```

_Gives permission to `to` to transfer `tokenId` token to another account.
The approval is cleared when the token is transferred.

Only a single account can be approved at a time, so approving the zero address clears previous approvals.

Requirements:

- The caller must own the token or be an approved operator.
- `tokenId` must exist.

Emits an {Approval} event._

### setApprovalForAll

```solidity
function setApprovalForAll(address operator, bool _approved) external
```

_Approve or remove `operator` as an operator for the caller.
Operators can call {transferFrom} or {safeTransferFrom} for any token owned by the caller.

Requirements:

- The `operator` cannot be the caller.

Emits an {ApprovalForAll} event._

### getApproved

```solidity
function getApproved(uint256 tokenId) external view returns (address operator)
```

_Returns the account approved for `tokenId` token.

Requirements:

- `tokenId` must exist._

### isApprovedForAll

```solidity
function isApprovedForAll(address owner, address operator) external view returns (bool)
```

_Returns if the `operator` is allowed to manage all of the assets of `owner`.

See {setApprovalForAll}_

## Ownable

_Contract module which provides a basic access control mechanism, where
there is an account (an owner) that can be granted exclusive access to
specific functions.

By default, the owner account will be the one that deploys the contract. This
can later be changed with {transferOwnership}.

This module is used through inheritance. It will make available the modifier
`onlyOwner`, which can be applied to your functions to restrict their use to
the owner._

### OwnershipTransferred

```solidity
event OwnershipTransferred(address previousOwner, address newOwner)
```

### constructor

```solidity
constructor() internal
```

_Initializes the contract setting the deployer as the initial owner._

### onlyOwner

```solidity
modifier onlyOwner()
```

_Throws if called by any account other than the owner._

### owner

```solidity
function owner() public view virtual returns (address)
```

_Returns the address of the current owner._

### _checkOwner

```solidity
function _checkOwner() internal view virtual
```

_Throws if the sender is not the owner._

### renounceOwnership

```solidity
function renounceOwnership() public virtual
```

_Leaves the contract without owner. It will not be possible to call
`onlyOwner` functions anymore. Can only be called by the current owner.

NOTE: Renouncing ownership will leave the contract without an owner,
thereby removing any functionality that is only available to the owner._

### transferOwnership

```solidity
function transferOwnership(address newOwner) public virtual
```

_Transfers ownership of the contract to a new account (`newOwner`).
Can only be called by the current owner._

### _transferOwnership

```solidity
function _transferOwnership(address newOwner) internal virtual
```

_Transfers ownership of the contract to a new account (`newOwner`).
Internal function without access restriction._

## ReentrancyGuard

_Contract module that helps prevent reentrant calls to a function.

Inheriting from `ReentrancyGuard` will make the {nonReentrant} modifier
available, which can be applied to functions to make sure there are no nested
(reentrant) calls to them.

Note that because there is a single `nonReentrant` guard, functions marked as
`nonReentrant` may not call one another. This can be worked around by making
those functions `private`, and then adding `external` `nonReentrant` entry
points to them.

TIP: If you would like to learn more about reentrancy and alternative ways
to protect against it, check out our blog post
https://blog.openzeppelin.com/reentrancy-after-istanbul/[Reentrancy After Istanbul]._

### constructor

```solidity
constructor() internal
```

### nonReentrant

```solidity
modifier nonReentrant()
```

_Prevents a contract from calling itself, directly or indirectly.
Calling a `nonReentrant` function from another `nonReentrant`
function is not supported. It is possible to prevent this from happening
by making the `nonReentrant` function external, and making it call a
`private` function that does the actual work._

## SafeERC20

_Wrappers around ERC20 operations that throw on failure (when the token
contract returns false). Tokens that return no value (and instead revert or
throw on failure) are also supported, non-reverting calls are assumed to be
successful.
To use this library you can add a `using SafeERC20 for IERC20;` statement to your contract,
which allows you to call the safe operations as `token.safeTransfer(...)`, etc._

### safeTransfer

```solidity
function safeTransfer(contract IERC20 token, address to, uint256 value) internal
```

### safeTransferFrom

```solidity
function safeTransferFrom(contract IERC20 token, address from, address to, uint256 value) internal
```

### safeApprove

```solidity
function safeApprove(contract IERC20 token, address spender, uint256 value) internal
```

_Deprecated. This function has issues similar to the ones found in
{IERC20-approve}, and its usage is discouraged.

Whenever possible, use {safeIncreaseAllowance} and
{safeDecreaseAllowance} instead._

### safeIncreaseAllowance

```solidity
function safeIncreaseAllowance(contract IERC20 token, address spender, uint256 value) internal
```

### safeDecreaseAllowance

```solidity
function safeDecreaseAllowance(contract IERC20 token, address spender, uint256 value) internal
```

### safePermit

```solidity
function safePermit(contract IERC20Permit token, address owner, address spender, uint256 value, uint256 deadline, uint8 v, bytes32 r, bytes32 s) internal
```

## IERC20Permit

_Interface of the ERC20 Permit extension allowing approvals to be made via signatures, as defined in
https://eips.ethereum.org/EIPS/eip-2612[EIP-2612].

Adds the {permit} method, which can be used to change an account's ERC20 allowance (see {IERC20-allowance}) by
presenting a message signed by the account. By not relying on {IERC20-approve}, the token holder account doesn't
need to send a transaction, and thus is not required to hold Ether at all._

### permit

```solidity
function permit(address owner, address spender, uint256 value, uint256 deadline, uint8 v, bytes32 r, bytes32 s) external
```

_Sets `value` as the allowance of `spender` over ``owner``'s tokens,
given ``owner``'s signed approval.

IMPORTANT: The same issues {IERC20-approve} has related to transaction
ordering also apply here.

Emits an {Approval} event.

Requirements:

- `spender` cannot be the zero address.
- `deadline` must be a timestamp in the future.
- `v`, `r` and `s` must be a valid `secp256k1` signature from `owner`
over the EIP712-formatted function arguments.
- the signature must use ``owner``'s current nonce (see {nonces}).

For more information on the signature format, see the
https://eips.ethereum.org/EIPS/eip-2612#specification[relevant EIP
section]._

### nonces

```solidity
function nonces(address owner) external view returns (uint256)
```

_Returns the current nonce for `owner`. This value must be
included whenever a signature is generated for {permit}.

Every successful call to {permit} increases ``owner``'s nonce by one. This
prevents a signature from being used multiple times._

### DOMAIN_SEPARATOR

```solidity
function DOMAIN_SEPARATOR() external view returns (bytes32)
```

_Returns the domain separator used in the encoding of the signature for {permit}, as defined by {EIP712}._

## Multicall

Enables calling multiple methods in a single call to the contract

### multicall

```solidity
function multicall(bytes[] data) public payable returns (bytes[] results)
```

## IOvaReferral

### referredFrom

```solidity
function referredFrom(address user) external view returns (address)
```

### seeReferred

```solidity
function seeReferred(address user) external view returns (address[])
```

### generatePoints

```solidity
function generatePoints(address user) external view returns (uint256)
```

### track

```solidity
function track(address user, uint256 amount) external
```

### consumeReferral

```solidity
function consumeReferral(address source, address consumer) external
```

## IRewardAsset

### mint

```solidity
function mint(address to, uint256 amount) external
```

## FEE

```solidity
uint24 FEE
```

## UniswapV3StakerFront

It handles user stakings by integrating all the bonus points obtained by referrals

### originalOwners

```solidity
mapping(uint256 => address) originalOwners
```

Cache of original token owners

### referralBonus

```solidity
uint8 referralBonus
```

Referral bonus amount

_5%_

### selfReferralBonus

```solidity
uint16 selfReferralBonus
```

Self referral bonus amount

_1.5%_

### referral

```solidity
contract IOvaReferral referral
```

Ova referral contract

### UniswapV3StakerReferralUpdated

```solidity
event UniswapV3StakerReferralUpdated(contract IOvaReferral referral)
```

### UniswapV3StakerReferralBonusUpdated

```solidity
event UniswapV3StakerReferralBonusUpdated(uint8 bonus)
```

### UniswapV3StakerReferralBonusPayed

```solidity
event UniswapV3StakerReferralBonusPayed(address recipient, uint256 amount)
```

### UniswapV3StakerSelfReferralBonusUpdated

```solidity
event UniswapV3StakerSelfReferralBonusUpdated(uint16 bonus)
```

### UniswapV3StakerSelfReferralBonusPayed

```solidity
event UniswapV3StakerSelfReferralBonusPayed(address recipient, uint256 amount)
```

### constructor

```solidity
constructor(address admin, contract IUniswapV3Factory factory, contract INonfungiblePositionManager nonfungiblePositionManager, uint256 maxIncentiveStartLeadTime, uint256 maxIncentiveDuration) public
```

Constructor

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| admin | address | The contract admin |
| factory | contract IUniswapV3Factory |  |
| nonfungiblePositionManager | contract INonfungiblePositionManager |  |
| maxIncentiveStartLeadTime | uint256 |  |
| maxIncentiveDuration | uint256 |  |

### updateReferral

```solidity
function updateReferral(contract IOvaReferral referral_) external
```

Update the referral contract

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| referral_ | contract IOvaReferral | The new referral contract |

### updateReferralBonus

```solidity
function updateReferralBonus(uint8 referralBonus_) external
```

Update the referral bonus amount.

_It can not be over 1000 (100%)._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| referralBonus_ | uint8 | the bonus amount. |

### updateSelfReferralBonus

```solidity
function updateSelfReferralBonus(uint16 selfReferralBonus_) external
```

Update the referral bonus amount.

_It can not be over 1000 (100%)._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| selfReferralBonus_ | uint16 | the bonus amount. |

### createIncentive

```solidity
function createIncentive(address token0, address token1, address reward, uint256 rewardAmount, uint256 startTime, uint256 endTime, address refundee) external
```

Create a new incentive

_Public uniswap staker allows a max incentive time of 63072000 seconds (https://etherscan.io/address/0xe34139463ba50bd61336e0c446bd8c0867c6fe65#readContract)_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| token0 | address | The first pool token |
| token1 | address | The second pool token |
| reward | address | The reward token |
| rewardAmount | uint256 | The total reward amount |
| startTime | uint256 | The reward start time |
| endTime | uint256 | The reward end time |
| refundee | address | The reward refundee if any left |

### stake

```solidity
function stake(uint256 tokenId, struct IUniswapV3Staker.IncentiveKey key, address referralSource) external
```

Deposit a token into the staker contract

_This transfer will trigger deposit + stake inside the staker contract
The original token owner is cached if any token is blocked inside this contract
Referral is consumed if the source valid_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The position tokenId |
| key | struct IUniswapV3Staker.IncentiveKey | The incentive key created inside the staker contract |
| referralSource | address | Any referral source |

### unstake

```solidity
function unstake(uint256 tokenId, struct IUniswapV3Staker.IncentiveKey key, contract IERC20Minimal reward, address rewardRecipient, address tokenRecipient) external returns (uint256)
```

Unstake, collect and withdraw the token

_The token owner must have called `transferDeposit` before (https://github.com/Uniswap/v3-staker/blob/6d06fe4034e4eec53e1e587fc4770286466f4b35/contracts/UniswapV3Staker.sol#L179C14-L179C29)
If user has being referred, the referral source will gain the referral bonus
and the current user will gain the self referral bonus_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The token id |
| key | struct IUniswapV3Staker.IncentiveKey | The incentive key |
| reward | contract IERC20Minimal | The reward token |
| rewardRecipient | address | The reward destination |
| tokenRecipient | address | The token destination |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | The collected reward amount |

### recoverDeposit

```solidity
function recoverDeposit(uint256 tokenId) external
```

Recover a deposit who changed owner to this contract

_Can only be called from the original owner who did stake the token_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The token to recover |

### getRewardInfo

```solidity
function getRewardInfo(uint256 tokenId, struct IUniswapV3Staker.IncentiveKey key) external view returns (uint256)
```

Visualize the accrued reward so far for a tokenId

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The position tokenId |
| key | struct IUniswapV3Staker.IncentiveKey | The incentive key created inside the staker contract |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | amount The accrued amount for the given tokenid and incentive |

### rewardsOwned

```solidity
function rewardsOwned(contract IERC20Minimal reward, address owner_) external view returns (uint256)
```

Visualize the owned reward to an owner

_The amount will we non zero only after unstaking_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| reward | contract IERC20Minimal | The reward address |
| owner_ | address | The owner to query |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | The amount of owned rewards |

### incentiveId

```solidity
function incentiveId(struct IUniswapV3Staker.IncentiveKey key) public pure returns (bytes32)
```

Retrieve the hash related to an incentive key

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | The incentive key |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | bytes32 | The hash |

### computeUnhashedKey

```solidity
function computeUnhashedKey(struct IUniswapV3Staker.IncentiveKey key) public pure returns (bytes)
```

Compute the packed struct

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | The incentive key to be packed |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | bytes | The packed key |

### stakedLiquidityStableCoins

```solidity
function stakedLiquidityStableCoins(struct IUniswapV3Staker.IncentiveKey key) public view returns (uint256)
```

### _payBonus

```solidity
function _payBonus(address rewardAsset, uint256 amount, address selfBonusRecipient) internal
```

Pay the reward bonus to referral source.

_The reward asset is directly minted from the reward token_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardAsset | address | the reward token. |
| amount | uint256 | the original collected amount. |
| selfBonusRecipient | address | The self bonus recipient |

## UniswapV3Staker

### Incentive

```solidity
struct Incentive {
  uint256 totalRewardUnclaimed;
  uint160 totalSecondsClaimedX128;
  uint96 numberOfStakes;
}
```

### Deposit

```solidity
struct Deposit {
  address owner;
  uint48 numberOfStakes;
  int24 tickLower;
  int24 tickUpper;
  uint256 amount0ValueAtDeposit;
  uint256 amount1ValueAtDeposit;
}
```

### Stake

```solidity
struct Stake {
  uint160 secondsPerLiquidityInsideInitialX128;
  uint96 liquidityNoOverflow;
  uint128 liquidityIfOverflow;
}
```

### factory

```solidity
contract IUniswapV3Factory factory
```

The Uniswap V3 Factory

### nonfungiblePositionManager

```solidity
contract INonfungiblePositionManager nonfungiblePositionManager
```

The nonfungible position manager with which this staking contract is compatible

### maxIncentiveStartLeadTime

```solidity
uint256 maxIncentiveStartLeadTime
```

The max amount of seconds into the future the incentive startTime can be set

### maxIncentiveDuration

```solidity
uint256 maxIncentiveDuration
```

The max duration of an incentive in seconds

### incentives

```solidity
mapping(bytes32 => struct UniswapV3Staker.Incentive) incentives
```

_bytes32 refers to the return value of IncentiveId.compute_

### deposits

```solidity
mapping(uint256 => struct UniswapV3Staker.Deposit) deposits
```

_deposits[tokenId] => Deposit_

### totalStakedStableCoins

```solidity
mapping(bytes32 => uint256) totalStakedStableCoins
```

_Total liquidity staked for incentive as stable coins_

### stakes

```solidity
function stakes(uint256 tokenId, bytes32 incentiveId) public view returns (uint160 secondsPerLiquidityInsideInitialX128, uint128 liquidity)
```

Returns information about a staked liquidity NFT

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The ID of the staked token |
| incentiveId | bytes32 | The ID of the incentive for which the token is staked |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| secondsPerLiquidityInsideInitialX128 | uint160 | secondsPerLiquidity represented as a UQ32.128 |
| liquidity | uint128 | The amount of liquidity in the NFT as of the last time the rewards were computed |

### rewards

```solidity
mapping(contract IERC20Minimal => mapping(address => uint256)) rewards
```

Returns amounts of reward tokens owed to a given address according to the last time all stakes were updated

_rewards[rewardToken][owner] => uint256_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |

### constructor

```solidity
constructor(contract IUniswapV3Factory _factory, contract INonfungiblePositionManager _nonfungiblePositionManager, uint256 _maxIncentiveStartLeadTime, uint256 _maxIncentiveDuration) public
```

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _factory | contract IUniswapV3Factory | the Uniswap V3 factory |
| _nonfungiblePositionManager | contract INonfungiblePositionManager | the NFT position manager contract address |
| _maxIncentiveStartLeadTime | uint256 | the max duration of an incentive in seconds |
| _maxIncentiveDuration | uint256 | the max amount of seconds into the future the incentive startTime can be set |

### createIncentive

```solidity
function createIncentive(struct IUniswapV3Staker.IncentiveKey key, uint256 reward) internal
```

Creates a new liquidity mining incentive program

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | Details of the incentive to create |
| reward | uint256 | The amount of reward tokens to be distributed |

### endIncentive

```solidity
function endIncentive(struct IUniswapV3Staker.IncentiveKey key) internal returns (uint256 refund)
```

Ends an incentive after the incentive end time has passed and all stakes have been withdrawn

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | Details of the incentive to end |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| refund | uint256 | The remaining reward tokens when the incentive is ended |

### getPool

```solidity
function getPool(address token0, address token1, uint24 fee) public view returns (contract IUniswapV3Pool)
```

Retrieve a pool address

_Fee amount is fixed for now_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| token0 | address | The first token |
| token1 | address | The second token |
| fee | uint24 |  |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | contract IUniswapV3Pool | The pool address as interface |

### onERC721Received

```solidity
function onERC721Received(address, address from, uint256 tokenId, bytes data) external returns (bytes4)
```

Upon receiving a Uniswap V3 ERC721, creates the token deposit setting owner to `from`. Also stakes token
in one or more incentives if properly formatted `data` has a length > 0.

_Whenever an {IERC721} `tokenId` token is transferred to this contract via {IERC721-safeTransferFrom}
by `operator` from `from`, this function is called.

It must return its Solidity selector to confirm the token transfer.
If any other value is returned or the interface is not implemented by the recipient, the transfer will be reverted.

The selector can be obtained in Solidity with `IERC721.onERC721Received.selector`._

### computeExponentDiff

```solidity
function computeExponentDiff(uint256 a, uint256 b) internal pure returns (uint256)
```

### computePositionToken0InRange

```solidity
function computePositionToken0InRange(uint256 liq, uint256 sqrtPu, uint256 sqrtP) internal pure returns (uint256 res, uint256 k)
```

### computePositionToken1InRange

```solidity
function computePositionToken1InRange(uint256 liq, uint256 sqrtPl, uint256 sqrtP) internal pure returns (uint256 res, uint256 k)
```

### getPositionAmounts

```solidity
function getPositionAmounts(contract IUniswapV3Pool pool, uint128 liquidity, int24 tickLower, int24 tickUpper) internal view returns (uint256 amount0, uint256 amount1)
```

### transferDeposit

```solidity
function transferDeposit(uint256 tokenId, address to) internal
```

Transfers ownership of a deposit from the sender to the given recipient

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The ID of the token (and the deposit) to transfer |
| to | address | The new owner of the deposit |

### withdrawToken

```solidity
function withdrawToken(uint256 tokenId, address to, bytes data) internal
```

Withdraws a Uniswap V3 LP token `tokenId` from this contract to the recipient `to`

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The unique identifier of an Uniswap V3 LP token |
| to | address | The address where the LP token will be sent |
| data | bytes | An optional data array that will be passed along to the `to` address via the NFT safeTransferFrom |

### stakeToken

```solidity
function stakeToken(struct IUniswapV3Staker.IncentiveKey key, uint256 tokenId) internal
```

Stakes a Uniswap V3 LP token

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | The key of the incentive for which to stake the NFT |
| tokenId | uint256 | The ID of the token to stake |

### unstakeToken

```solidity
function unstakeToken(struct IUniswapV3Staker.IncentiveKey key, uint256 tokenId) internal
```

Unstakes a Uniswap V3 LP token

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | The key of the incentive for which to unstake the NFT |
| tokenId | uint256 | The ID of the token to unstake |

### claimReward

```solidity
function claimReward(contract IERC20Minimal rewardToken, address to, uint256 amountRequested) internal returns (uint256 reward)
```

Transfers `amountRequested` of accrued `rewardToken` rewards from the contract to the recipient `to`

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardToken | contract IERC20Minimal | The token being distributed as a reward |
| to | address | The address where claimed rewards will be sent to |
| amountRequested | uint256 | The amount of reward tokens to claim. Claims entire reward amount if set to 0. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| reward | uint256 | The amount of reward tokens claimed |

### getRewardInfo

```solidity
function getRewardInfo(struct IUniswapV3Staker.IncentiveKey key, uint256 tokenId) public view returns (uint256 reward, uint160 secondsInsideX128)
```

Calculates the reward amount that will be received for the given stake

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | The key of the incentive |
| tokenId | uint256 | The ID of the token |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| reward | uint256 | The reward accrued to the NFT for the given incentive thus far |
| secondsInsideX128 | uint160 |  |

## IUniswapV3Staker

Allows staking nonfungible liquidity tokens in exchange for reward tokens

### IncentiveKey

```solidity
struct IncentiveKey {
  contract IERC20Minimal rewardToken;
  contract IUniswapV3Pool pool;
  uint256 startTime;
  uint256 endTime;
  address refundee;
}
```

### factory

```solidity
function factory() external view returns (contract IUniswapV3Factory)
```

The Uniswap V3 Factory

### nonfungiblePositionManager

```solidity
function nonfungiblePositionManager() external view returns (contract INonfungiblePositionManager)
```

The nonfungible position manager with which this staking contract is compatible

### maxIncentiveDuration

```solidity
function maxIncentiveDuration() external view returns (uint256)
```

The max duration of an incentive in seconds

### maxIncentiveStartLeadTime

```solidity
function maxIncentiveStartLeadTime() external view returns (uint256)
```

The max amount of seconds into the future the incentive startTime can be set

### incentives

```solidity
function incentives(bytes32 incentiveId) external view returns (uint256 totalRewardUnclaimed, uint160 totalSecondsClaimedX128, uint96 numberOfStakes)
```

Represents a staking incentive

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| incentiveId | bytes32 | The ID of the incentive computed from its parameters |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| totalRewardUnclaimed | uint256 | The amount of reward token not yet claimed by users |
| totalSecondsClaimedX128 | uint160 | Total liquidity-seconds claimed, represented as a UQ32.128 |
| numberOfStakes | uint96 | The count of deposits that are currently staked for the incentive |

### deposits

```solidity
function deposits(uint256 tokenId) external view returns (address owner, uint48 numberOfStakes, int24 tickLower, int24 tickUpper, uint256 amount0, uint256 amount1)
```

Returns information about a deposited NFT

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| owner | address | The owner of the deposited NFT |
| numberOfStakes | uint48 | Counter of how many incentives for which the liquidity is staked |
| tickLower | int24 | The lower tick of the range |
| tickUpper | int24 | The upper tick of the range |
| amount0 | uint256 |  |
| amount1 | uint256 |  |

### stakes

```solidity
function stakes(uint256 tokenId, bytes32 incentiveId) external view returns (uint160 secondsPerLiquidityInsideInitialX128, uint128 liquidity)
```

Returns information about a staked liquidity NFT

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The ID of the staked token |
| incentiveId | bytes32 | The ID of the incentive for which the token is staked |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| secondsPerLiquidityInsideInitialX128 | uint160 | secondsPerLiquidity represented as a UQ32.128 |
| liquidity | uint128 | The amount of liquidity in the NFT as of the last time the rewards were computed |

### rewards

```solidity
function rewards(contract IERC20Minimal rewardToken, address owner) external view returns (uint256 rewardsOwed)
```

Returns amounts of reward tokens owed to a given address according to the last time all stakes were updated

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardToken | contract IERC20Minimal | The token for which to check rewards |
| owner | address | The owner for which the rewards owed are checked |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardsOwed | uint256 | The amount of the reward token claimable by the owner |

### getRewardInfo

```solidity
function getRewardInfo(struct IUniswapV3Staker.IncentiveKey key, uint256 tokenId) external returns (uint256 reward, uint160 secondsInsideX128)
```

Calculates the reward amount that will be received for the given stake

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | The key of the incentive |
| tokenId | uint256 | The ID of the token |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| reward | uint256 | The reward accrued to the NFT for the given incentive thus far |
| secondsInsideX128 | uint160 |  |

### IncentiveCreated

```solidity
event IncentiveCreated(contract IERC20Minimal rewardToken, contract IUniswapV3Pool pool, uint256 startTime, uint256 endTime, address refundee, uint256 reward)
```

Event emitted when a liquidity mining incentive has been created

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardToken | contract IERC20Minimal | The token being distributed as a reward |
| pool | contract IUniswapV3Pool | The Uniswap V3 pool |
| startTime | uint256 | The time when the incentive program begins |
| endTime | uint256 | The time when rewards stop accruing |
| refundee | address | The address which receives any remaining reward tokens after the end time |
| reward | uint256 | The amount of reward tokens to be distributed |

### IncentiveEnded

```solidity
event IncentiveEnded(bytes32 incentiveId, uint256 refund)
```

Event that can be emitted when a liquidity mining incentive has ended

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| incentiveId | bytes32 | The incentive which is ending |
| refund | uint256 | The amount of reward tokens refunded |

### DepositTransferred

```solidity
event DepositTransferred(uint256 tokenId, address oldOwner, address newOwner)
```

Emitted when ownership of a deposit changes

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The ID of the deposit (and token) that is being transferred |
| oldOwner | address | The owner before the deposit was transferred |
| newOwner | address | The owner after the deposit was transferred |

### TokenStaked

```solidity
event TokenStaked(uint256 tokenId, bytes32 incentiveId, uint128 liquidity)
```

Event emitted when a Uniswap V3 LP token has been staked

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The unique identifier of an Uniswap V3 LP token |
| incentiveId | bytes32 | The incentive in which the token is staking |
| liquidity | uint128 | The amount of liquidity staked |

### TokenUnstaked

```solidity
event TokenUnstaked(uint256 tokenId, bytes32 incentiveId)
```

Event emitted when a Uniswap V3 LP token has been unstaked

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The unique identifier of an Uniswap V3 LP token |
| incentiveId | bytes32 | The incentive in which the token is staking |

### RewardClaimed

```solidity
event RewardClaimed(address to, uint256 reward)
```

Event emitted when a reward token has been claimed

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| to | address | The address where claimed rewards were sent to |
| reward | uint256 | The amount of reward tokens claimed |

## IncentiveId

### compute

```solidity
function compute(struct IUniswapV3Staker.IncentiveKey key) internal pure returns (bytes32 incentiveId)
```

Calculate the key for a staking incentive

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | The components used to compute the incentive identifier |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| incentiveId | bytes32 | The identifier for the incentive |

## NFTPositionInfo

Encapsulates the logic for getting info about a NFT token ID

### getPositionInfo

```solidity
function getPositionInfo(contract IUniswapV3Factory factory, contract INonfungiblePositionManager nonfungiblePositionManager, uint256 tokenId) internal view returns (contract IUniswapV3Pool pool, int24 tickLower, int24 tickUpper, uint128 liquidity)
```

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| factory | contract IUniswapV3Factory | The address of the Uniswap V3 Factory used in computing the pool address |
| nonfungiblePositionManager | contract INonfungiblePositionManager | The address of the nonfungible position manager to query |
| tokenId | uint256 | The unique identifier of an Uniswap V3 LP token |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| pool | contract IUniswapV3Pool | The address of the Uniswap V3 pool |
| tickLower | int24 | The lower tick of the Uniswap V3 position |
| tickUpper | int24 | The upper tick of the Uniswap V3 position |
| liquidity | uint128 | The amount of liquidity staked |

## RewardMath

Allows computing rewards given some parameters of stakes and incentives

### computeRewardAmount

```solidity
function computeRewardAmount(uint256 totalRewardUnclaimed, uint160 totalSecondsClaimedX128, uint256 startTime, uint256 endTime, uint128 liquidity, uint160 secondsPerLiquidityInsideInitialX128, uint160 secondsPerLiquidityInsideX128, uint256 currentTime) internal pure returns (uint256 reward, uint160 secondsInsideX128)
```

Compute the amount of rewards owed given parameters of the incentive and stake

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| totalRewardUnclaimed | uint256 | The total amount of unclaimed rewards left for an incentive |
| totalSecondsClaimedX128 | uint160 | How many full liquidity-seconds have been already claimed for the incentive |
| startTime | uint256 | When the incentive rewards began in epoch seconds |
| endTime | uint256 | When rewards are no longer being dripped out in epoch seconds |
| liquidity | uint128 | The amount of liquidity, assumed to be constant over the period over which the snapshots are measured |
| secondsPerLiquidityInsideInitialX128 | uint160 | The seconds per liquidity of the liquidity tick range as of the beginning of the period |
| secondsPerLiquidityInsideX128 | uint160 | The seconds per liquidity of the liquidity tick range as of the current block timestamp |
| currentTime | uint256 | The current block timestamp, which must be greater than or equal to the start time |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| reward | uint256 | The amount of rewards owed |
| secondsInsideX128 | uint160 | The total liquidity seconds inside the position's range for the duration of the stake |

## TransferHelperExtended

### safeTransferFrom

```solidity
function safeTransferFrom(address token, address from, address to, uint256 value) internal
```

Transfers tokens from the targeted address to the given destination
Errors with 'STF' if transfer fails

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| token | address | The contract address of the token to be transferred |
| from | address | The originating address from which the tokens will be transferred |
| to | address | The destination address of the transfer |
| value | uint256 | The amount to be transferred |

### safeTransfer

```solidity
function safeTransfer(address token, address to, uint256 value) internal
```

Transfers tokens from msg.sender to a recipient

_Errors with ST if transfer fails_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| token | address | The contract address of the token which will be transferred |
| to | address | The recipient of the transfer |
| value | uint256 | The value of the transfer |

## Address

_Collection of functions related to the address type_

### isContract

```solidity
function isContract(address account) internal view returns (bool)
```

_Returns true if `account` is a contract.

[IMPORTANT]
====
It is unsafe to assume that an address for which this function returns
false is an externally-owned account (EOA) and not a contract.

Among others, `isContract` will return false for the following
types of addresses:

 - an externally-owned account
 - a contract in construction
 - an address where a contract will be created
 - an address where a contract lived, but was destroyed
====_

### sendValue

```solidity
function sendValue(address payable recipient, uint256 amount) internal
```

_Replacement for Solidity's `transfer`: sends `amount` wei to
`recipient`, forwarding all available gas and reverting on errors.

https://eips.ethereum.org/EIPS/eip-1884[EIP1884] increases the gas cost
of certain opcodes, possibly making contracts go over the 2300 gas limit
imposed by `transfer`, making them unable to receive funds via
`transfer`. {sendValue} removes this limitation.

https://diligence.consensys.net/posts/2019/09/stop-using-soliditys-transfer-now/[Learn more].

IMPORTANT: because control is transferred to `recipient`, care must be
taken to not create reentrancy vulnerabilities. Consider using
{ReentrancyGuard} or the
https://solidity.readthedocs.io/en/v0.5.11/security-considerations.html#use-the-checks-effects-interactions-pattern[checks-effects-interactions pattern]._

### functionCall

```solidity
function functionCall(address target, bytes data) internal returns (bytes)
```

_Performs a Solidity function call using a low level `call`. A
plain`call` is an unsafe replacement for a function call: use this
function instead.

If `target` reverts with a revert reason, it is bubbled up by this
function (like regular Solidity function calls).

Returns the raw returned data. To convert to the expected return value,
use https://solidity.readthedocs.io/en/latest/units-and-global-variables.html?highlight=abi.decode#abi-encoding-and-decoding-functions[`abi.decode`].

Requirements:

- `target` must be a contract.
- calling `target` with `data` must not revert.

_Available since v3.1.__

### functionCall

```solidity
function functionCall(address target, bytes data, string errorMessage) internal returns (bytes)
```

_Same as {xref-Address-functionCall-address-bytes-}[`functionCall`], but with
`errorMessage` as a fallback revert reason when `target` reverts.

_Available since v3.1.__

### functionCallWithValue

```solidity
function functionCallWithValue(address target, bytes data, uint256 value) internal returns (bytes)
```

_Same as {xref-Address-functionCall-address-bytes-}[`functionCall`],
but also transferring `value` wei to `target`.

Requirements:

- the calling contract must have an ETH balance of at least `value`.
- the called Solidity function must be `payable`.

_Available since v3.1.__

### functionCallWithValue

```solidity
function functionCallWithValue(address target, bytes data, uint256 value, string errorMessage) internal returns (bytes)
```

_Same as {xref-Address-functionCallWithValue-address-bytes-uint256-}[`functionCallWithValue`], but
with `errorMessage` as a fallback revert reason when `target` reverts.

_Available since v3.1.__

### functionStaticCall

```solidity
function functionStaticCall(address target, bytes data) internal view returns (bytes)
```

_Same as {xref-Address-functionCall-address-bytes-}[`functionCall`],
but performing a static call.

_Available since v3.3.__

### functionStaticCall

```solidity
function functionStaticCall(address target, bytes data, string errorMessage) internal view returns (bytes)
```

_Same as {xref-Address-functionCall-address-bytes-string-}[`functionCall`],
but performing a static call.

_Available since v3.3.__

### functionDelegateCall

```solidity
function functionDelegateCall(address target, bytes data) internal returns (bytes)
```

_Same as {xref-Address-functionCall-address-bytes-}[`functionCall`],
but performing a delegate call.

_Available since v3.4.__

### functionDelegateCall

```solidity
function functionDelegateCall(address target, bytes data, string errorMessage) internal returns (bytes)
```

_Same as {xref-Address-functionCall-address-bytes-string-}[`functionCall`],
but performing a delegate call.

_Available since v3.4.__

## Context

_Provides information about the current execution context, including the
sender of the transaction and its data. While these are generally available
via msg.sender and msg.data, they should not be accessed in such a direct
manner, since when dealing with meta-transactions the account sending and
paying for execution may not be the actual sender (as far as an application
is concerned).

This contract is only required for intermediate, library-like contracts._

### _msgSender

```solidity
function _msgSender() internal view virtual returns (address)
```

### _msgData

```solidity
function _msgData() internal view virtual returns (bytes)
```

### _contextSuffixLength

```solidity
function _contextSuffixLength() internal view virtual returns (uint256)
```

## IERC165

_Interface of the ERC165 standard, as defined in the
https://eips.ethereum.org/EIPS/eip-165[EIP].

Implementers can declare support of contract interfaces, which can then be
queried by others ({ERC165Checker}).

For an implementation, see {ERC165}._

### supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) external view returns (bool)
```

_Returns true if this contract implements the interface defined by
`interfaceId`. See the corresponding
https://eips.ethereum.org/EIPS/eip-165#how-interfaces-are-identified[EIP section]
to learn more about how these ids are created.

This function call must use less than 30 000 gas._

## IERC20

_Interface of the ERC20 standard as defined in the EIP._

### totalSupply

```solidity
function totalSupply() external view returns (uint256)
```

_Returns the amount of tokens in existence._

### balanceOf

```solidity
function balanceOf(address account) external view returns (uint256)
```

_Returns the amount of tokens owned by `account`._

### transfer

```solidity
function transfer(address recipient, uint256 amount) external returns (bool)
```

_Moves `amount` tokens from the caller's account to `recipient`.

Returns a boolean value indicating whether the operation succeeded.

Emits a {Transfer} event._

### allowance

```solidity
function allowance(address owner, address spender) external view returns (uint256)
```

_Returns the remaining number of tokens that `spender` will be
allowed to spend on behalf of `owner` through {transferFrom}. This is
zero by default.

This value changes when {approve} or {transferFrom} are called._

### approve

```solidity
function approve(address spender, uint256 amount) external returns (bool)
```

_Sets `amount` as the allowance of `spender` over the caller's tokens.

Returns a boolean value indicating whether the operation succeeded.

IMPORTANT: Beware that changing an allowance with this method brings the risk
that someone may use both the old and the new allowance by unfortunate
transaction ordering. One possible solution to mitigate this race
condition is to first reduce the spender's allowance to 0 and set the
desired value afterwards:
https://github.com/ethereum/EIPs/issues/20#issuecomment-263524729

Emits an {Approval} event._

### transferFrom

```solidity
function transferFrom(address sender, address recipient, uint256 amount) external returns (bool)
```

_Moves `amount` tokens from `sender` to `recipient` using the
allowance mechanism. `amount` is then deducted from the caller's
allowance.

Returns a boolean value indicating whether the operation succeeded.

Emits a {Transfer} event._

### Transfer

```solidity
event Transfer(address from, address to, uint256 value)
```

_Emitted when `value` tokens are moved from one account (`from`) to
another (`to`).

Note that `value` may be zero._

### Approval

```solidity
event Approval(address owner, address spender, uint256 value)
```

_Emitted when the allowance of a `spender` for an `owner` is set by
a call to {approve}. `value` is the new allowance._

## IERC721

_Required interface of an ERC721 compliant contract._

### Transfer

```solidity
event Transfer(address from, address to, uint256 tokenId)
```

_Emitted when `tokenId` token is transferred from `from` to `to`._

### Approval

```solidity
event Approval(address owner, address approved, uint256 tokenId)
```

_Emitted when `owner` enables `approved` to manage the `tokenId` token._

### ApprovalForAll

```solidity
event ApprovalForAll(address owner, address operator, bool approved)
```

_Emitted when `owner` enables or disables (`approved`) `operator` to manage all of its assets._

### balanceOf

```solidity
function balanceOf(address owner) external view returns (uint256 balance)
```

_Returns the number of tokens in ``owner``'s account._

### ownerOf

```solidity
function ownerOf(uint256 tokenId) external view returns (address owner)
```

_Returns the owner of the `tokenId` token.

Requirements:

- `tokenId` must exist._

### safeTransferFrom

```solidity
function safeTransferFrom(address from, address to, uint256 tokenId) external
```

_Safely transfers `tokenId` token from `from` to `to`, checking first that contract recipients
are aware of the ERC721 protocol to prevent tokens from being forever locked.

Requirements:

- `from` cannot be the zero address.
- `to` cannot be the zero address.
- `tokenId` token must exist and be owned by `from`.
- If the caller is not `from`, it must be have been allowed to move this token by either {approve} or {setApprovalForAll}.
- If `to` refers to a smart contract, it must implement {IERC721Receiver-onERC721Received}, which is called upon a safe transfer.

Emits a {Transfer} event._

### transferFrom

```solidity
function transferFrom(address from, address to, uint256 tokenId) external
```

_Transfers `tokenId` token from `from` to `to`.

WARNING: Usage of this method is discouraged, use {safeTransferFrom} whenever possible.

Requirements:

- `from` cannot be the zero address.
- `to` cannot be the zero address.
- `tokenId` token must be owned by `from`.
- If the caller is not `from`, it must be approved to move this token by either {approve} or {setApprovalForAll}.

Emits a {Transfer} event._

### approve

```solidity
function approve(address to, uint256 tokenId) external
```

_Gives permission to `to` to transfer `tokenId` token to another account.
The approval is cleared when the token is transferred.

Only a single account can be approved at a time, so approving the zero address clears previous approvals.

Requirements:

- The caller must own the token or be an approved operator.
- `tokenId` must exist.

Emits an {Approval} event._

### getApproved

```solidity
function getApproved(uint256 tokenId) external view returns (address operator)
```

_Returns the account approved for `tokenId` token.

Requirements:

- `tokenId` must exist._

### setApprovalForAll

```solidity
function setApprovalForAll(address operator, bool _approved) external
```

_Approve or remove `operator` as an operator for the caller.
Operators can call {transferFrom} or {safeTransferFrom} for any token owned by the caller.

Requirements:

- The `operator` cannot be the caller.

Emits an {ApprovalForAll} event._

### isApprovedForAll

```solidity
function isApprovedForAll(address owner, address operator) external view returns (bool)
```

_Returns if the `operator` is allowed to manage all of the assets of `owner`.

See {setApprovalForAll}_

### safeTransferFrom

```solidity
function safeTransferFrom(address from, address to, uint256 tokenId, bytes data) external
```

_Safely transfers `tokenId` token from `from` to `to`.

Requirements:

- `from` cannot be the zero address.
- `to` cannot be the zero address.
- `tokenId` token must exist and be owned by `from`.
- If the caller is not `from`, it must be approved to move this token by either {approve} or {setApprovalForAll}.
- If `to` refers to a smart contract, it must implement {IERC721Receiver-onERC721Received}, which is called upon a safe transfer.

Emits a {Transfer} event._

## IERC721Enumerable

_See https://eips.ethereum.org/EIPS/eip-721_

### totalSupply

```solidity
function totalSupply() external view returns (uint256)
```

_Returns the total amount of tokens stored by the contract._

### tokenOfOwnerByIndex

```solidity
function tokenOfOwnerByIndex(address owner, uint256 index) external view returns (uint256 tokenId)
```

_Returns a token ID owned by `owner` at a given `index` of its token list.
Use along with {balanceOf} to enumerate all of ``owner``'s tokens._

### tokenByIndex

```solidity
function tokenByIndex(uint256 index) external view returns (uint256)
```

_Returns a token ID at a given `index` of all the tokens stored by the contract.
Use along with {totalSupply} to enumerate all tokens._

## IERC721Metadata

_See https://eips.ethereum.org/EIPS/eip-721_

### name

```solidity
function name() external view returns (string)
```

_Returns the token collection name._

### symbol

```solidity
function symbol() external view returns (string)
```

_Returns the token collection symbol._

### tokenURI

```solidity
function tokenURI(uint256 tokenId) external view returns (string)
```

_Returns the Uniform Resource Identifier (URI) for `tokenId` token._

## IERC721Receiver

_Interface for any contract that wants to support safeTransfers
from ERC721 asset contracts._

### onERC721Received

```solidity
function onERC721Received(address operator, address from, uint256 tokenId, bytes data) external returns (bytes4)
```

_Whenever an {IERC721} `tokenId` token is transferred to this contract via {IERC721-safeTransferFrom}
by `operator` from `from`, this function is called.

It must return its Solidity selector to confirm the token transfer.
If any other value is returned or the interface is not implemented by the recipient, the transfer will be reverted.

The selector can be obtained in Solidity with `IERC721.onERC721Received.selector`._

## Math

_Standard math utilities missing in the Solidity language._

### max

```solidity
function max(uint256 a, uint256 b) internal pure returns (uint256)
```

_Returns the largest of two numbers._

### min

```solidity
function min(uint256 a, uint256 b) internal pure returns (uint256)
```

_Returns the smallest of two numbers._

### average

```solidity
function average(uint256 a, uint256 b) internal pure returns (uint256)
```

_Returns the average of two numbers. The result is rounded towards
zero._

## Ownable

_Contract module which provides a basic access control mechanism, where
there is an account (an owner) that can be granted exclusive access to
specific functions.

The initial owner is set to the address provided by the deployer. This can
later be changed with {transferOwnership}.

This module is used through inheritance. It will make available the modifier
`onlyOwner`, which can be applied to your functions to restrict their use to
the owner._

### OwnershipTransferred

```solidity
event OwnershipTransferred(address previousOwner, address newOwner)
```

### constructor

```solidity
constructor(address initialOwner) internal
```

_Initializes the contract setting the address provided by the deployer as the initial owner._

### onlyOwner

```solidity
modifier onlyOwner()
```

_Throws if called by any account other than the owner._

### owner

```solidity
function owner() public view virtual returns (address)
```

_Returns the address of the current owner._

### _checkOwner

```solidity
function _checkOwner() internal view virtual
```

_Throws if the sender is not the owner._

### renounceOwnership

```solidity
function renounceOwnership() public virtual
```

_Leaves the contract without owner. It will not be possible to call
`onlyOwner` functions. Can only be called by the current owner.

NOTE: Renouncing ownership will leave the contract without an owner,
thereby disabling any functionality that is only available to the owner._

### transferOwnership

```solidity
function transferOwnership(address newOwner) public virtual
```

_Transfers ownership of the contract to a new account (`newOwner`).
Can only be called by the current owner._

### _transferOwnership

```solidity
function _transferOwnership(address newOwner) internal virtual
```

_Transfers ownership of the contract to a new account (`newOwner`).
Internal function without access restriction._

## ReentrancyGuard

_Contract module that helps prevent reentrant calls to a function.

Inheriting from `ReentrancyGuard` will make the {nonReentrant} modifier
available, which can be applied to functions to make sure there are no nested
(reentrant) calls to them.

Note that because there is a single `nonReentrant` guard, functions marked as
`nonReentrant` may not call one another. This can be worked around by making
those functions `private`, and then adding `external` `nonReentrant` entry
points to them.

TIP: If you would like to learn more about reentrancy and alternative ways
to protect against it, check out our blog post
https://blog.openzeppelin.com/reentrancy-after-istanbul/[Reentrancy After Istanbul]._

### constructor

```solidity
constructor() internal
```

### nonReentrant

```solidity
modifier nonReentrant()
```

_Prevents a contract from calling itself, directly or indirectly.
Calling a `nonReentrant` function from another `nonReentrant`
function is not supported. It is possible to prevent this from happening
by making the `nonReentrant` function external, and making it call a
`private` function that does the actual work._

## SafeMath

_Wrappers over Solidity's arithmetic operations with added overflow
checks.

Arithmetic operations in Solidity wrap on overflow. This can easily result
in bugs, because programmers usually assume that an overflow raises an
error, which is the standard behavior in high level programming languages.
`SafeMath` restores this intuition by reverting the transaction when an
operation overflows.

Using this library instead of the unchecked operations eliminates an entire
class of bugs, so it's recommended to use it always._

### tryAdd

```solidity
function tryAdd(uint256 a, uint256 b) internal pure returns (bool, uint256)
```

_Returns the addition of two unsigned integers, with an overflow flag.

_Available since v3.4.__

### trySub

```solidity
function trySub(uint256 a, uint256 b) internal pure returns (bool, uint256)
```

_Returns the substraction of two unsigned integers, with an overflow flag.

_Available since v3.4.__

### tryMul

```solidity
function tryMul(uint256 a, uint256 b) internal pure returns (bool, uint256)
```

_Returns the multiplication of two unsigned integers, with an overflow flag.

_Available since v3.4.__

### tryDiv

```solidity
function tryDiv(uint256 a, uint256 b) internal pure returns (bool, uint256)
```

_Returns the division of two unsigned integers, with a division by zero flag.

_Available since v3.4.__

### tryMod

```solidity
function tryMod(uint256 a, uint256 b) internal pure returns (bool, uint256)
```

_Returns the remainder of dividing two unsigned integers, with a division by zero flag.

_Available since v3.4.__

### add

```solidity
function add(uint256 a, uint256 b) internal pure returns (uint256)
```

_Returns the addition of two unsigned integers, reverting on
overflow.

Counterpart to Solidity's `+` operator.

Requirements:

- Addition cannot overflow._

### sub

```solidity
function sub(uint256 a, uint256 b) internal pure returns (uint256)
```

_Returns the subtraction of two unsigned integers, reverting on
overflow (when the result is negative).

Counterpart to Solidity's `-` operator.

Requirements:

- Subtraction cannot overflow._

### mul

```solidity
function mul(uint256 a, uint256 b) internal pure returns (uint256)
```

_Returns the multiplication of two unsigned integers, reverting on
overflow.

Counterpart to Solidity's `*` operator.

Requirements:

- Multiplication cannot overflow._

### div

```solidity
function div(uint256 a, uint256 b) internal pure returns (uint256)
```

_Returns the integer division of two unsigned integers, reverting on
division by zero. The result is rounded towards zero.

Counterpart to Solidity's `/` operator. Note: this function uses a
`revert` opcode (which leaves remaining gas untouched) while Solidity
uses an invalid opcode to revert (consuming all remaining gas).

Requirements:

- The divisor cannot be zero._

### mod

```solidity
function mod(uint256 a, uint256 b) internal pure returns (uint256)
```

_Returns the remainder of dividing two unsigned integers. (unsigned integer modulo),
reverting when dividing by zero.

Counterpart to Solidity's `%` operator. This function uses a `revert`
opcode (which leaves remaining gas untouched) while Solidity uses an
invalid opcode to revert (consuming all remaining gas).

Requirements:

- The divisor cannot be zero._

### sub

```solidity
function sub(uint256 a, uint256 b, string errorMessage) internal pure returns (uint256)
```

_Returns the subtraction of two unsigned integers, reverting with custom message on
overflow (when the result is negative).

CAUTION: This function is deprecated because it requires allocating memory for the error
message unnecessarily. For custom revert reasons use {trySub}.

Counterpart to Solidity's `-` operator.

Requirements:

- Subtraction cannot overflow._

### div

```solidity
function div(uint256 a, uint256 b, string errorMessage) internal pure returns (uint256)
```

_Returns the integer division of two unsigned integers, reverting with custom message on
division by zero. The result is rounded towards zero.

CAUTION: This function is deprecated because it requires allocating memory for the error
message unnecessarily. For custom revert reasons use {tryDiv}.

Counterpart to Solidity's `/` operator. Note: this function uses a
`revert` opcode (which leaves remaining gas untouched) while Solidity
uses an invalid opcode to revert (consuming all remaining gas).

Requirements:

- The divisor cannot be zero._

### mod

```solidity
function mod(uint256 a, uint256 b, string errorMessage) internal pure returns (uint256)
```

_Returns the remainder of dividing two unsigned integers. (unsigned integer modulo),
reverting with custom message when dividing by zero.

CAUTION: This function is deprecated because it requires allocating memory for the error
message unnecessarily. For custom revert reasons use {tryMod}.

Counterpart to Solidity's `%` operator. This function uses a `revert`
opcode (which leaves remaining gas untouched) while Solidity uses an
invalid opcode to revert (consuming all remaining gas).

Requirements:

- The divisor cannot be zero._

## FullMath

Facilitates multiplication and division that can have overflow of an intermediate value without any loss of precision

_Handles "phantom overflow" i.e., allows multiplication and division where an intermediate value overflows 256 bits_

### mulDiv

```solidity
function mulDiv(uint256 a, uint256 b, uint256 denominator) internal pure returns (uint256 result)
```

Calculates floor(a×b÷denominator) with full precision. Throws if result overflows a uint256 or denominator == 0

_Credit to Remco Bloemen under MIT license https://xn--2-umb.com/21/muldiv_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| a | uint256 | The multiplicand |
| b | uint256 | The multiplier |
| denominator | uint256 | The divisor |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| result | uint256 | The 256-bit result |

### mulDivRoundingUp

```solidity
function mulDivRoundingUp(uint256 a, uint256 b, uint256 denominator) internal pure returns (uint256 result)
```

Calculates ceil(a×b÷denominator) with full precision. Throws if result overflows a uint256 or denominator == 0

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| a | uint256 | The multiplicand |
| b | uint256 | The multiplier |
| denominator | uint256 | The divisor |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| result | uint256 | The 256-bit result |

## IERC20Minimal

Contains a subset of the full ERC20 interface that is used in Uniswap V3

### balanceOf

```solidity
function balanceOf(address account) external view returns (uint256)
```

Returns the balance of a token

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| account | address | The account for which to look up the number of tokens it has, i.e. its balance |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | The number of tokens held by the account |

### transfer

```solidity
function transfer(address recipient, uint256 amount) external returns (bool)
```

Transfers the amount of token from the `msg.sender` to the recipient

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| recipient | address | The account that will receive the amount transferred |
| amount | uint256 | The number of tokens to send from the sender to the recipient |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | bool | Returns true for a successful transfer, false for an unsuccessful transfer |

### allowance

```solidity
function allowance(address owner, address spender) external view returns (uint256)
```

Returns the current allowance given to a spender by an owner

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| owner | address | The account of the token owner |
| spender | address | The account of the token spender |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | The current allowance granted by `owner` to `spender` |

### approve

```solidity
function approve(address spender, uint256 amount) external returns (bool)
```

Sets the allowance of a spender from the `msg.sender` to the value `amount`

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| spender | address | The account which will be allowed to spend a given amount of the owners tokens |
| amount | uint256 | The amount of tokens allowed to be used by `spender` |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | bool | Returns true for a successful approval, false for unsuccessful |

### transferFrom

```solidity
function transferFrom(address sender, address recipient, uint256 amount) external returns (bool)
```

Transfers `amount` tokens from `sender` to `recipient` up to the allowance given to the `msg.sender`

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| sender | address | The account from which the transfer will be initiated |
| recipient | address | The recipient of the transfer |
| amount | uint256 | The amount of the transfer |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | bool | Returns true for a successful transfer, false for unsuccessful |

### Transfer

```solidity
event Transfer(address from, address to, uint256 value)
```

Event emitted when tokens are transferred from one address to another, either via `#transfer` or `#transferFrom`.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| from | address | The account from which the tokens were sent, i.e. the balance decreased |
| to | address | The account to which the tokens were sent, i.e. the balance increased |
| value | uint256 | The amount of tokens that were transferred |

### Approval

```solidity
event Approval(address owner, address spender, uint256 value)
```

Event emitted when the approval amount for the spender of a given owner's tokens changes.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| owner | address | The account that approved spending of its tokens |
| spender | address | The account for which the spending allowance was modified |
| value | uint256 | The new allowance from the owner to the spender |

## IERC721Permit

Extension to ERC721 that includes a permit function for signature based approvals

### PERMIT_TYPEHASH

```solidity
function PERMIT_TYPEHASH() external pure returns (bytes32)
```

The permit typehash used in the permit signature

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | bytes32 | The typehash for the permit |

### DOMAIN_SEPARATOR

```solidity
function DOMAIN_SEPARATOR() external view returns (bytes32)
```

The domain separator used in the permit signature

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | bytes32 | The domain seperator used in encoding of permit signature |

### permit

```solidity
function permit(address spender, uint256 tokenId, uint256 deadline, uint8 v, bytes32 r, bytes32 s) external payable
```

Approve of a specific token ID for spending by spender via signature

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| spender | address | The account that is being approved |
| tokenId | uint256 | The ID of the token that is being approved for spending |
| deadline | uint256 | The deadline timestamp by which the call must be mined for the approve to work |
| v | uint8 | Must produce valid secp256k1 signature from the holder along with `r` and `s` |
| r | bytes32 | Must produce valid secp256k1 signature from the holder along with `v` and `s` |
| s | bytes32 | Must produce valid secp256k1 signature from the holder along with `r` and `v` |

## IMulticall

Enables calling multiple methods in a single call to the contract

### multicall

```solidity
function multicall(bytes[] data) external payable returns (bytes[] results)
```

Call multiple functions in the current contract and return the data from all of them if they all succeed

_The `msg.value` should not be trusted for any method callable from multicall._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| data | bytes[] | The encoded function data for each of the calls to make to this contract |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| results | bytes[] | The results from each of the calls passed in via data |

## INonfungiblePositionManager

Wraps Uniswap V3 positions in a non-fungible token interface which allows for them to be transferred
and authorized.

### IncreaseLiquidity

```solidity
event IncreaseLiquidity(uint256 tokenId, uint128 liquidity, uint256 amount0, uint256 amount1)
```

Emitted when liquidity is increased for a position NFT

_Also emitted when a token is minted_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The ID of the token for which liquidity was increased |
| liquidity | uint128 | The amount by which liquidity for the NFT position was increased |
| amount0 | uint256 | The amount of token0 that was paid for the increase in liquidity |
| amount1 | uint256 | The amount of token1 that was paid for the increase in liquidity |

### DecreaseLiquidity

```solidity
event DecreaseLiquidity(uint256 tokenId, uint128 liquidity, uint256 amount0, uint256 amount1)
```

Emitted when liquidity is decreased for a position NFT

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The ID of the token for which liquidity was decreased |
| liquidity | uint128 | The amount by which liquidity for the NFT position was decreased |
| amount0 | uint256 | The amount of token0 that was accounted for the decrease in liquidity |
| amount1 | uint256 | The amount of token1 that was accounted for the decrease in liquidity |

### Collect

```solidity
event Collect(uint256 tokenId, address recipient, uint256 amount0, uint256 amount1)
```

Emitted when tokens are collected for a position NFT

_The amounts reported may not be exactly equivalent to the amounts transferred, due to rounding behavior_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The ID of the token for which underlying tokens were collected |
| recipient | address | The address of the account that received the collected tokens |
| amount0 | uint256 | The amount of token0 owed to the position that was collected |
| amount1 | uint256 | The amount of token1 owed to the position that was collected |

### positions

```solidity
function positions(uint256 tokenId) external view returns (uint96 nonce, address operator, address token0, address token1, uint24 fee, int24 tickLower, int24 tickUpper, uint128 liquidity, uint256 feeGrowthInside0LastX128, uint256 feeGrowthInside1LastX128, uint128 tokensOwed0, uint128 tokensOwed1)
```

Returns the position information associated with a given token ID.

_Throws if the token ID is not valid._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The ID of the token that represents the position |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| nonce | uint96 | The nonce for permits |
| operator | address | The address that is approved for spending |
| token0 | address | The address of the token0 for a specific pool |
| token1 | address | The address of the token1 for a specific pool |
| fee | uint24 | The fee associated with the pool |
| tickLower | int24 | The lower end of the tick range for the position |
| tickUpper | int24 | The higher end of the tick range for the position |
| liquidity | uint128 | The liquidity of the position |
| feeGrowthInside0LastX128 | uint256 | The fee growth of token0 as of the last action on the individual position |
| feeGrowthInside1LastX128 | uint256 | The fee growth of token1 as of the last action on the individual position |
| tokensOwed0 | uint128 | The uncollected amount of token0 owed to the position as of the last computation |
| tokensOwed1 | uint128 | The uncollected amount of token1 owed to the position as of the last computation |

### MintParams

```solidity
struct MintParams {
  address token0;
  address token1;
  uint24 fee;
  int24 tickLower;
  int24 tickUpper;
  uint256 amount0Desired;
  uint256 amount1Desired;
  uint256 amount0Min;
  uint256 amount1Min;
  address recipient;
  uint256 deadline;
}
```

### mint

```solidity
function mint(struct INonfungiblePositionManager.MintParams params) external payable returns (uint256 tokenId, uint128 liquidity, uint256 amount0, uint256 amount1)
```

Creates a new position wrapped in a NFT

_Call this when the pool does exist and is initialized. Note that if the pool is created but not initialized
a method does not exist, i.e. the pool is assumed to be initialized._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| params | struct INonfungiblePositionManager.MintParams | The params necessary to mint a position, encoded as `MintParams` in calldata |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The ID of the token that represents the minted position |
| liquidity | uint128 | The amount of liquidity for this position |
| amount0 | uint256 | The amount of token0 |
| amount1 | uint256 | The amount of token1 |

### IncreaseLiquidityParams

```solidity
struct IncreaseLiquidityParams {
  uint256 tokenId;
  uint256 amount0Desired;
  uint256 amount1Desired;
  uint256 amount0Min;
  uint256 amount1Min;
  uint256 deadline;
}
```

### increaseLiquidity

```solidity
function increaseLiquidity(struct INonfungiblePositionManager.IncreaseLiquidityParams params) external payable returns (uint128 liquidity, uint256 amount0, uint256 amount1)
```

Increases the amount of liquidity in a position, with tokens paid by the `msg.sender`

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| params | struct INonfungiblePositionManager.IncreaseLiquidityParams | tokenId The ID of the token for which liquidity is being increased, amount0Desired The desired amount of token0 to be spent, amount1Desired The desired amount of token1 to be spent, amount0Min The minimum amount of token0 to spend, which serves as a slippage check, amount1Min The minimum amount of token1 to spend, which serves as a slippage check, deadline The time by which the transaction must be included to effect the change |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| liquidity | uint128 | The new liquidity amount as a result of the increase |
| amount0 | uint256 | The amount of token0 to acheive resulting liquidity |
| amount1 | uint256 | The amount of token1 to acheive resulting liquidity |

### DecreaseLiquidityParams

```solidity
struct DecreaseLiquidityParams {
  uint256 tokenId;
  uint128 liquidity;
  uint256 amount0Min;
  uint256 amount1Min;
  uint256 deadline;
}
```

### decreaseLiquidity

```solidity
function decreaseLiquidity(struct INonfungiblePositionManager.DecreaseLiquidityParams params) external payable returns (uint256 amount0, uint256 amount1)
```

Decreases the amount of liquidity in a position and accounts it to the position

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| params | struct INonfungiblePositionManager.DecreaseLiquidityParams | tokenId The ID of the token for which liquidity is being decreased, amount The amount by which liquidity will be decreased, amount0Min The minimum amount of token0 that should be accounted for the burned liquidity, amount1Min The minimum amount of token1 that should be accounted for the burned liquidity, deadline The time by which the transaction must be included to effect the change |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount0 | uint256 | The amount of token0 accounted to the position's tokens owed |
| amount1 | uint256 | The amount of token1 accounted to the position's tokens owed |

### CollectParams

```solidity
struct CollectParams {
  uint256 tokenId;
  address recipient;
  uint128 amount0Max;
  uint128 amount1Max;
}
```

### collect

```solidity
function collect(struct INonfungiblePositionManager.CollectParams params) external payable returns (uint256 amount0, uint256 amount1)
```

Collects up to a maximum amount of fees owed to a specific position to the recipient

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| params | struct INonfungiblePositionManager.CollectParams | tokenId The ID of the NFT for which tokens are being collected, recipient The account that should receive the tokens, amount0Max The maximum amount of token0 to collect, amount1Max The maximum amount of token1 to collect |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount0 | uint256 | The amount of fees collected in token0 |
| amount1 | uint256 | The amount of fees collected in token1 |

### burn

```solidity
function burn(uint256 tokenId) external payable
```

Burns a token ID, which deletes it from the NFT contract. The token must have 0 liquidity and all tokens
must be collected first.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The ID of the token that is being burned |

## IPeripheryImmutableState

Functions that return immutable state of the router

### factory

```solidity
function factory() external view returns (address)
```

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | address | Returns the address of the Uniswap V3 factory |

### WETH9

```solidity
function WETH9() external view returns (address)
```

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | address | Returns the address of WETH9 |

## IPeripheryPayments

Functions to ease deposits and withdrawals of ETH

### unwrapWETH9

```solidity
function unwrapWETH9(uint256 amountMinimum, address recipient) external payable
```

Unwraps the contract's WETH9 balance and sends it to recipient as ETH.

_The amountMinimum parameter prevents malicious contracts from stealing WETH9 from users._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| amountMinimum | uint256 | The minimum amount of WETH9 to unwrap |
| recipient | address | The address receiving ETH |

### refundETH

```solidity
function refundETH() external payable
```

Refunds any ETH balance held by this contract to the `msg.sender`

_Useful for bundling with mint or increase liquidity that uses ether, or exact output swaps
that use ether for the input amount_

### sweepToken

```solidity
function sweepToken(address token, uint256 amountMinimum, address recipient) external payable
```

Transfers the full amount of a token held by this contract to recipient

_The amountMinimum parameter prevents malicious contracts from stealing the token from users_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| token | address | The contract address of the token which will be transferred to `recipient` |
| amountMinimum | uint256 | The minimum amount of token required for a transfer |
| recipient | address | The destination address of the token |

## IPoolInitializer

Provides a method for creating and initializing a pool, if necessary, for bundling with other methods that
require the pool to exist.

### createAndInitializePoolIfNecessary

```solidity
function createAndInitializePoolIfNecessary(address token0, address token1, uint24 fee, uint160 sqrtPriceX96) external payable returns (address pool)
```

Creates a new pool if it does not exist, then initializes if not initialized

_This method can be bundled with others via IMulticall for the first action (e.g. mint) performed against a pool_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| token0 | address | The contract address of token0 of the pool |
| token1 | address | The contract address of token1 of the pool |
| fee | uint24 | The fee amount of the v3 pool for the specified token pair |
| sqrtPriceX96 | uint160 | The initial square root price of the pool as a Q64.96 value |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| pool | address | Returns the pool address based on the pair of tokens and fee, will return the newly created pool address if necessary |

## IUniswapV3Factory

The Uniswap V3 Factory facilitates creation of Uniswap V3 pools and control over the protocol fees

### OwnerChanged

```solidity
event OwnerChanged(address oldOwner, address newOwner)
```

Emitted when the owner of the factory is changed

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| oldOwner | address | The owner before the owner was changed |
| newOwner | address | The owner after the owner was changed |

### PoolCreated

```solidity
event PoolCreated(address token0, address token1, uint24 fee, int24 tickSpacing, address pool)
```

Emitted when a pool is created

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| token0 | address | The first token of the pool by address sort order |
| token1 | address | The second token of the pool by address sort order |
| fee | uint24 | The fee collected upon every swap in the pool, denominated in hundredths of a bip |
| tickSpacing | int24 | The minimum number of ticks between initialized ticks |
| pool | address | The address of the created pool |

### FeeAmountEnabled

```solidity
event FeeAmountEnabled(uint24 fee, int24 tickSpacing)
```

Emitted when a new fee amount is enabled for pool creation via the factory

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| fee | uint24 | The enabled fee, denominated in hundredths of a bip |
| tickSpacing | int24 | The minimum number of ticks between initialized ticks for pools created with the given fee |

### owner

```solidity
function owner() external view returns (address)
```

Returns the current owner of the factory

_Can be changed by the current owner via setOwner_

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | address | The address of the factory owner |

### feeAmountTickSpacing

```solidity
function feeAmountTickSpacing(uint24 fee) external view returns (int24)
```

Returns the tick spacing for a given fee amount, if enabled, or 0 if not enabled

_A fee amount can never be removed, so this value should be hard coded or cached in the calling context_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| fee | uint24 | The enabled fee, denominated in hundredths of a bip. Returns 0 in case of unenabled fee |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | int24 | The tick spacing |

### getPool

```solidity
function getPool(address tokenA, address tokenB, uint24 fee) external view returns (address pool)
```

Returns the pool address for a given pair of tokens and a fee, or address 0 if it does not exist

_tokenA and tokenB may be passed in either token0/token1 or token1/token0 order_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenA | address | The contract address of either token0 or token1 |
| tokenB | address | The contract address of the other token |
| fee | uint24 | The fee collected upon every swap in the pool, denominated in hundredths of a bip |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| pool | address | The pool address |

### createPool

```solidity
function createPool(address tokenA, address tokenB, uint24 fee) external returns (address pool)
```

Creates a pool for the given two tokens and fee

_tokenA and tokenB may be passed in either order: token0/token1 or token1/token0. tickSpacing is retrieved
from the fee. The call will revert if the pool already exists, the fee is invalid, or the token arguments
are invalid._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenA | address | One of the two tokens in the desired pool |
| tokenB | address | The other of the two tokens in the desired pool |
| fee | uint24 | The desired fee for the pool |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| pool | address | The address of the newly created pool |

### setOwner

```solidity
function setOwner(address _owner) external
```

Updates the owner of the factory

_Must be called by the current owner_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| _owner | address | The new owner of the factory |

### enableFeeAmount

```solidity
function enableFeeAmount(uint24 fee, int24 tickSpacing) external
```

Enables a fee amount with the given tickSpacing

_Fee amounts may never be removed once enabled_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| fee | uint24 | The fee amount to enable, denominated in hundredths of a bip (i.e. 1e-6) |
| tickSpacing | int24 | The spacing between ticks to be enforced for all pools created with the given fee amount |

## IUniswapV3Pool

A Uniswap pool facilitates swapping and automated market making between any two assets that strictly conform
to the ERC20 specification

_The pool interface is broken up into many smaller pieces_

## IUniswapV3PoolActions

Contains pool methods that can be called by anyone

### initialize

```solidity
function initialize(uint160 sqrtPriceX96) external
```

Sets the initial price for the pool

_Price is represented as a sqrt(amountToken1/amountToken0) Q64.96 value_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| sqrtPriceX96 | uint160 | the initial sqrt price of the pool as a Q64.96 |

### mint

```solidity
function mint(address recipient, int24 tickLower, int24 tickUpper, uint128 amount, bytes data) external returns (uint256 amount0, uint256 amount1)
```

Adds liquidity for the given recipient/tickLower/tickUpper position

_The caller of this method receives a callback in the form of IUniswapV3MintCallback#uniswapV3MintCallback
in which they must pay any token0 or token1 owed for the liquidity. The amount of token0/token1 due depends
on tickLower, tickUpper, the amount of liquidity, and the current price._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| recipient | address | The address for which the liquidity will be created |
| tickLower | int24 | The lower tick of the position in which to add liquidity |
| tickUpper | int24 | The upper tick of the position in which to add liquidity |
| amount | uint128 | The amount of liquidity to mint |
| data | bytes | Any data that should be passed through to the callback |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount0 | uint256 | The amount of token0 that was paid to mint the given amount of liquidity. Matches the value in the callback |
| amount1 | uint256 | The amount of token1 that was paid to mint the given amount of liquidity. Matches the value in the callback |

### collect

```solidity
function collect(address recipient, int24 tickLower, int24 tickUpper, uint128 amount0Requested, uint128 amount1Requested) external returns (uint128 amount0, uint128 amount1)
```

Collects tokens owed to a position

_Does not recompute fees earned, which must be done either via mint or burn of any amount of liquidity.
Collect must be called by the position owner. To withdraw only token0 or only token1, amount0Requested or
amount1Requested may be set to zero. To withdraw all tokens owed, caller may pass any value greater than the
actual tokens owed, e.g. type(uint128).max. Tokens owed may be from accumulated swap fees or burned liquidity._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| recipient | address | The address which should receive the fees collected |
| tickLower | int24 | The lower tick of the position for which to collect fees |
| tickUpper | int24 | The upper tick of the position for which to collect fees |
| amount0Requested | uint128 | How much token0 should be withdrawn from the fees owed |
| amount1Requested | uint128 | How much token1 should be withdrawn from the fees owed |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount0 | uint128 | The amount of fees collected in token0 |
| amount1 | uint128 | The amount of fees collected in token1 |

### burn

```solidity
function burn(int24 tickLower, int24 tickUpper, uint128 amount) external returns (uint256 amount0, uint256 amount1)
```

Burn liquidity from the sender and account tokens owed for the liquidity to the position

_Can be used to trigger a recalculation of fees owed to a position by calling with an amount of 0
Fees must be collected separately via a call to #collect_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tickLower | int24 | The lower tick of the position for which to burn liquidity |
| tickUpper | int24 | The upper tick of the position for which to burn liquidity |
| amount | uint128 | How much liquidity to burn |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount0 | uint256 | The amount of token0 sent to the recipient |
| amount1 | uint256 | The amount of token1 sent to the recipient |

### swap

```solidity
function swap(address recipient, bool zeroForOne, int256 amountSpecified, uint160 sqrtPriceLimitX96, bytes data) external returns (int256 amount0, int256 amount1)
```

Swap token0 for token1, or token1 for token0

_The caller of this method receives a callback in the form of IUniswapV3SwapCallback#uniswapV3SwapCallback_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| recipient | address | The address to receive the output of the swap |
| zeroForOne | bool | The direction of the swap, true for token0 to token1, false for token1 to token0 |
| amountSpecified | int256 | The amount of the swap, which implicitly configures the swap as exact input (positive), or exact output (negative) |
| sqrtPriceLimitX96 | uint160 | The Q64.96 sqrt price limit. If zero for one, the price cannot be less than this value after the swap. If one for zero, the price cannot be greater than this value after the swap |
| data | bytes | Any data to be passed through to the callback |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount0 | int256 | The delta of the balance of token0 of the pool, exact when negative, minimum when positive |
| amount1 | int256 | The delta of the balance of token1 of the pool, exact when negative, minimum when positive |

### flash

```solidity
function flash(address recipient, uint256 amount0, uint256 amount1, bytes data) external
```

Receive token0 and/or token1 and pay it back, plus a fee, in the callback

_The caller of this method receives a callback in the form of IUniswapV3FlashCallback#uniswapV3FlashCallback
Can be used to donate underlying tokens pro-rata to currently in-range liquidity providers by calling
with 0 amount{0,1} and sending the donation amount(s) from the callback_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| recipient | address | The address which will receive the token0 and token1 amounts |
| amount0 | uint256 | The amount of token0 to send |
| amount1 | uint256 | The amount of token1 to send |
| data | bytes | Any data to be passed through to the callback |

### increaseObservationCardinalityNext

```solidity
function increaseObservationCardinalityNext(uint16 observationCardinalityNext) external
```

Increase the maximum number of price and liquidity observations that this pool will store

_This method is no-op if the pool already has an observationCardinalityNext greater than or equal to
the input observationCardinalityNext._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| observationCardinalityNext | uint16 | The desired minimum number of observations for the pool to store |

## IUniswapV3PoolDerivedState

Contains view functions to provide information about the pool that is computed rather than stored on the
blockchain. The functions here may have variable gas costs.

### observe

```solidity
function observe(uint32[] secondsAgos) external view returns (int56[] tickCumulatives, uint160[] secondsPerLiquidityCumulativeX128s)
```

Returns the cumulative tick and liquidity as of each timestamp `secondsAgo` from the current block timestamp

_To get a time weighted average tick or liquidity-in-range, you must call this with two values, one representing
the beginning of the period and another for the end of the period. E.g., to get the last hour time-weighted average tick,
you must call it with secondsAgos = [3600, 0].
The time weighted average tick represents the geometric time weighted average price of the pool, in
log base sqrt(1.0001) of token1 / token0. The TickMath library can be used to go from a tick value to a ratio._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| secondsAgos | uint32[] | From how long ago each cumulative tick and liquidity value should be returned |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| tickCumulatives | int56[] | Cumulative tick values as of each `secondsAgos` from the current block timestamp |
| secondsPerLiquidityCumulativeX128s | uint160[] | Cumulative seconds per liquidity-in-range value as of each `secondsAgos` from the current block timestamp |

### snapshotCumulativesInside

```solidity
function snapshotCumulativesInside(int24 tickLower, int24 tickUpper) external view returns (int56 tickCumulativeInside, uint160 secondsPerLiquidityInsideX128, uint32 secondsInside)
```

Returns a snapshot of the tick cumulative, seconds per liquidity and seconds inside a tick range

_Snapshots must only be compared to other snapshots, taken over a period for which a position existed.
I.e., snapshots cannot be compared if a position is not held for the entire period between when the first
snapshot is taken and the second snapshot is taken._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tickLower | int24 | The lower tick of the range |
| tickUpper | int24 | The upper tick of the range |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| tickCumulativeInside | int56 | The snapshot of the tick accumulator for the range |
| secondsPerLiquidityInsideX128 | uint160 | The snapshot of seconds per liquidity for the range |
| secondsInside | uint32 | The snapshot of seconds per liquidity for the range |

## IUniswapV3PoolEvents

Contains all events emitted by the pool

### Initialize

```solidity
event Initialize(uint160 sqrtPriceX96, int24 tick)
```

Emitted exactly once by a pool when #initialize is first called on the pool

_Mint/Burn/Swap cannot be emitted by the pool before Initialize_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| sqrtPriceX96 | uint160 | The initial sqrt price of the pool, as a Q64.96 |
| tick | int24 | The initial tick of the pool, i.e. log base 1.0001 of the starting price of the pool |

### Mint

```solidity
event Mint(address sender, address owner, int24 tickLower, int24 tickUpper, uint128 amount, uint256 amount0, uint256 amount1)
```

Emitted when liquidity is minted for a given position

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| sender | address | The address that minted the liquidity |
| owner | address | The owner of the position and recipient of any minted liquidity |
| tickLower | int24 | The lower tick of the position |
| tickUpper | int24 | The upper tick of the position |
| amount | uint128 | The amount of liquidity minted to the position range |
| amount0 | uint256 | How much token0 was required for the minted liquidity |
| amount1 | uint256 | How much token1 was required for the minted liquidity |

### Collect

```solidity
event Collect(address owner, address recipient, int24 tickLower, int24 tickUpper, uint128 amount0, uint128 amount1)
```

Emitted when fees are collected by the owner of a position

_Collect events may be emitted with zero amount0 and amount1 when the caller chooses not to collect fees_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| owner | address | The owner of the position for which fees are collected |
| recipient | address |  |
| tickLower | int24 | The lower tick of the position |
| tickUpper | int24 | The upper tick of the position |
| amount0 | uint128 | The amount of token0 fees collected |
| amount1 | uint128 | The amount of token1 fees collected |

### Burn

```solidity
event Burn(address owner, int24 tickLower, int24 tickUpper, uint128 amount, uint256 amount0, uint256 amount1)
```

Emitted when a position's liquidity is removed

_Does not withdraw any fees earned by the liquidity position, which must be withdrawn via #collect_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| owner | address | The owner of the position for which liquidity is removed |
| tickLower | int24 | The lower tick of the position |
| tickUpper | int24 | The upper tick of the position |
| amount | uint128 | The amount of liquidity to remove |
| amount0 | uint256 | The amount of token0 withdrawn |
| amount1 | uint256 | The amount of token1 withdrawn |

### Swap

```solidity
event Swap(address sender, address recipient, int256 amount0, int256 amount1, uint160 sqrtPriceX96, uint128 liquidity, int24 tick)
```

Emitted by the pool for any swaps between token0 and token1

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| sender | address | The address that initiated the swap call, and that received the callback |
| recipient | address | The address that received the output of the swap |
| amount0 | int256 | The delta of the token0 balance of the pool |
| amount1 | int256 | The delta of the token1 balance of the pool |
| sqrtPriceX96 | uint160 | The sqrt(price) of the pool after the swap, as a Q64.96 |
| liquidity | uint128 | The liquidity of the pool after the swap |
| tick | int24 | The log base 1.0001 of price of the pool after the swap |

### Flash

```solidity
event Flash(address sender, address recipient, uint256 amount0, uint256 amount1, uint256 paid0, uint256 paid1)
```

Emitted by the pool for any flashes of token0/token1

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| sender | address | The address that initiated the swap call, and that received the callback |
| recipient | address | The address that received the tokens from flash |
| amount0 | uint256 | The amount of token0 that was flashed |
| amount1 | uint256 | The amount of token1 that was flashed |
| paid0 | uint256 | The amount of token0 paid for the flash, which can exceed the amount0 plus the fee |
| paid1 | uint256 | The amount of token1 paid for the flash, which can exceed the amount1 plus the fee |

### IncreaseObservationCardinalityNext

```solidity
event IncreaseObservationCardinalityNext(uint16 observationCardinalityNextOld, uint16 observationCardinalityNextNew)
```

Emitted by the pool for increases to the number of observations that can be stored

_observationCardinalityNext is not the observation cardinality until an observation is written at the index
just before a mint/swap/burn._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| observationCardinalityNextOld | uint16 | The previous value of the next observation cardinality |
| observationCardinalityNextNew | uint16 | The updated value of the next observation cardinality |

### SetFeeProtocol

```solidity
event SetFeeProtocol(uint8 feeProtocol0Old, uint8 feeProtocol1Old, uint8 feeProtocol0New, uint8 feeProtocol1New)
```

Emitted when the protocol fee is changed by the pool

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| feeProtocol0Old | uint8 | The previous value of the token0 protocol fee |
| feeProtocol1Old | uint8 | The previous value of the token1 protocol fee |
| feeProtocol0New | uint8 | The updated value of the token0 protocol fee |
| feeProtocol1New | uint8 | The updated value of the token1 protocol fee |

### CollectProtocol

```solidity
event CollectProtocol(address sender, address recipient, uint128 amount0, uint128 amount1)
```

Emitted when the collected protocol fees are withdrawn by the factory owner

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| sender | address | The address that collects the protocol fees |
| recipient | address | The address that receives the collected protocol fees |
| amount0 | uint128 | The amount of token0 protocol fees that is withdrawn |
| amount1 | uint128 |  |

## IUniswapV3PoolImmutables

These parameters are fixed for a pool forever, i.e., the methods will always return the same values

### factory

```solidity
function factory() external view returns (address)
```

The contract that deployed the pool, which must adhere to the IUniswapV3Factory interface

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | address | The contract address |

### token0

```solidity
function token0() external view returns (address)
```

The first of the two tokens of the pool, sorted by address

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | address | The token contract address |

### token1

```solidity
function token1() external view returns (address)
```

The second of the two tokens of the pool, sorted by address

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | address | The token contract address |

### fee

```solidity
function fee() external view returns (uint24)
```

The pool's fee in hundredths of a bip, i.e. 1e-6

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint24 | The fee |

### tickSpacing

```solidity
function tickSpacing() external view returns (int24)
```

The pool tick spacing

_Ticks can only be used at multiples of this value, minimum of 1 and always positive
e.g.: a tickSpacing of 3 means ticks can be initialized every 3rd tick, i.e., ..., -6, -3, 0, 3, 6, ...
This value is an int24 to avoid casting even though it is always positive._

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | int24 | The tick spacing |

### maxLiquidityPerTick

```solidity
function maxLiquidityPerTick() external view returns (uint128)
```

The maximum amount of position liquidity that can use any tick in the range

_This parameter is enforced per tick to prevent liquidity from overflowing a uint128 at any point, and
also prevents out-of-range liquidity from being used to prevent adding in-range liquidity to a pool_

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint128 | The max amount of liquidity per tick |

## IUniswapV3PoolOwnerActions

Contains pool methods that may only be called by the factory owner

### setFeeProtocol

```solidity
function setFeeProtocol(uint8 feeProtocol0, uint8 feeProtocol1) external
```

Set the denominator of the protocol's % share of the fees

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| feeProtocol0 | uint8 | new protocol fee for token0 of the pool |
| feeProtocol1 | uint8 | new protocol fee for token1 of the pool |

### collectProtocol

```solidity
function collectProtocol(address recipient, uint128 amount0Requested, uint128 amount1Requested) external returns (uint128 amount0, uint128 amount1)
```

Collect the protocol fee accrued to the pool

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| recipient | address | The address to which collected protocol fees should be sent |
| amount0Requested | uint128 | The maximum amount of token0 to send, can be 0 to collect fees in only token1 |
| amount1Requested | uint128 | The maximum amount of token1 to send, can be 0 to collect fees in only token0 |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount0 | uint128 | The protocol fee collected in token0 |
| amount1 | uint128 | The protocol fee collected in token1 |

## IUniswapV3PoolState

These methods compose the pool's state, and can change with any frequency including multiple times
per transaction

### slot0

```solidity
function slot0() external view returns (uint160 sqrtPriceX96, int24 tick, uint16 observationIndex, uint16 observationCardinality, uint16 observationCardinalityNext, uint8 feeProtocol, bool unlocked)
```

The 0th storage slot in the pool stores many values, and is exposed as a single method to save gas
when accessed externally.

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| sqrtPriceX96 | uint160 | The current price of the pool as a sqrt(token1/token0) Q64.96 value tick The current tick of the pool, i.e. according to the last tick transition that was run. This value may not always be equal to SqrtTickMath.getTickAtSqrtRatio(sqrtPriceX96) if the price is on a tick boundary. observationIndex The index of the last oracle observation that was written, observationCardinality The current maximum number of observations stored in the pool, observationCardinalityNext The next maximum number of observations, to be updated when the observation. feeProtocol The protocol fee for both tokens of the pool. Encoded as two 4 bit values, where the protocol fee of token1 is shifted 4 bits and the protocol fee of token0 is the lower 4 bits. Used as the denominator of a fraction of the swap fee, e.g. 4 means 1/4th of the swap fee. unlocked Whether the pool is currently locked to reentrancy |
| tick | int24 |  |
| observationIndex | uint16 |  |
| observationCardinality | uint16 |  |
| observationCardinalityNext | uint16 |  |
| feeProtocol | uint8 |  |
| unlocked | bool |  |

### feeGrowthGlobal0X128

```solidity
function feeGrowthGlobal0X128() external view returns (uint256)
```

The fee growth as a Q128.128 fees of token0 collected per unit of liquidity for the entire life of the pool

_This value can overflow the uint256_

### feeGrowthGlobal1X128

```solidity
function feeGrowthGlobal1X128() external view returns (uint256)
```

The fee growth as a Q128.128 fees of token1 collected per unit of liquidity for the entire life of the pool

_This value can overflow the uint256_

### protocolFees

```solidity
function protocolFees() external view returns (uint128 token0, uint128 token1)
```

The amounts of token0 and token1 that are owed to the protocol

_Protocol fees will never exceed uint128 max in either token_

### liquidity

```solidity
function liquidity() external view returns (uint128)
```

The currently in range liquidity available to the pool

_This value has no relationship to the total liquidity across all ticks_

### ticks

```solidity
function ticks(int24 tick) external view returns (uint128 liquidityGross, int128 liquidityNet, uint256 feeGrowthOutside0X128, uint256 feeGrowthOutside1X128, int56 tickCumulativeOutside, uint160 secondsPerLiquidityOutsideX128, uint32 secondsOutside, bool initialized)
```

Look up information about a specific tick in the pool

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tick | int24 | The tick to look up |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| liquidityGross | uint128 | the total amount of position liquidity that uses the pool either as tick lower or tick upper, liquidityNet how much liquidity changes when the pool price crosses the tick, feeGrowthOutside0X128 the fee growth on the other side of the tick from the current tick in token0, feeGrowthOutside1X128 the fee growth on the other side of the tick from the current tick in token1, tickCumulativeOutside the cumulative tick value on the other side of the tick from the current tick secondsPerLiquidityOutsideX128 the seconds spent per liquidity on the other side of the tick from the current tick, secondsOutside the seconds spent on the other side of the tick from the current tick, initialized Set to true if the tick is initialized, i.e. liquidityGross is greater than 0, otherwise equal to false. Outside values can only be used if the tick is initialized, i.e. if liquidityGross is greater than 0. In addition, these values are only relative and must be used only in comparison to previous snapshots for a specific position. |
| liquidityNet | int128 |  |
| feeGrowthOutside0X128 | uint256 |  |
| feeGrowthOutside1X128 | uint256 |  |
| tickCumulativeOutside | int56 |  |
| secondsPerLiquidityOutsideX128 | uint160 |  |
| secondsOutside | uint32 |  |
| initialized | bool |  |

### tickBitmap

```solidity
function tickBitmap(int16 wordPosition) external view returns (uint256)
```

Returns 256 packed tick initialized boolean values. See TickBitmap for more information

### positions

```solidity
function positions(bytes32 key) external view returns (uint128 _liquidity, uint256 feeGrowthInside0LastX128, uint256 feeGrowthInside1LastX128, uint128 tokensOwed0, uint128 tokensOwed1)
```

Returns the information about a position by the position's key

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | bytes32 | The position's key is a hash of a preimage composed by the owner, tickLower and tickUpper |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| _liquidity | uint128 | The amount of liquidity in the position, Returns feeGrowthInside0LastX128 fee growth of token0 inside the tick range as of the last mint/burn/poke, Returns feeGrowthInside1LastX128 fee growth of token1 inside the tick range as of the last mint/burn/poke, Returns tokensOwed0 the computed amount of token0 owed to the position as of the last mint/burn/poke, Returns tokensOwed1 the computed amount of token1 owed to the position as of the last mint/burn/poke |
| feeGrowthInside0LastX128 | uint256 |  |
| feeGrowthInside1LastX128 | uint256 |  |
| tokensOwed0 | uint128 |  |
| tokensOwed1 | uint128 |  |

### observations

```solidity
function observations(uint256 index) external view returns (uint32 blockTimestamp, int56 tickCumulative, uint160 secondsPerLiquidityCumulativeX128, bool initialized)
```

Returns data about a specific observation index

_You most likely want to use #observe() instead of this method to get an observation as of some amount of time
ago, rather than at a specific index in the array._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| index | uint256 | The element of the observations array to fetch |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| blockTimestamp | uint32 | The timestamp of the observation, Returns tickCumulative the tick multiplied by seconds elapsed for the life of the pool as of the observation timestamp, Returns secondsPerLiquidityCumulativeX128 the seconds per in range liquidity for the life of the pool as of the observation timestamp, Returns initialized whether the observation has been initialized and the values are safe to use |
| tickCumulative | int56 |  |
| secondsPerLiquidityCumulativeX128 | uint160 |  |
| initialized | bool |  |

## IUniswapV3Staker

Allows staking nonfungible liquidity tokens in exchange for reward tokens

### IncentiveKey

```solidity
struct IncentiveKey {
  contract IERC20Minimal rewardToken;
  contract IUniswapV3Pool pool;
  uint256 startTime;
  uint256 endTime;
  address refundee;
}
```

### factory

```solidity
function factory() external view returns (contract IUniswapV3Factory)
```

The Uniswap V3 Factory

### nonfungiblePositionManager

```solidity
function nonfungiblePositionManager() external view returns (contract INonfungiblePositionManager)
```

The nonfungible position manager with which this staking contract is compatible

### maxIncentiveDuration

```solidity
function maxIncentiveDuration() external view returns (uint256)
```

The max duration of an incentive in seconds

### maxIncentiveStartLeadTime

```solidity
function maxIncentiveStartLeadTime() external view returns (uint256)
```

The max amount of seconds into the future the incentive startTime can be set

### incentives

```solidity
function incentives(bytes32 incentiveId) external view returns (uint256 totalRewardUnclaimed, uint160 totalSecondsClaimedX128, uint96 numberOfStakes)
```

Represents a staking incentive

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| incentiveId | bytes32 | The ID of the incentive computed from its parameters |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| totalRewardUnclaimed | uint256 | The amount of reward token not yet claimed by users |
| totalSecondsClaimedX128 | uint160 | Total liquidity-seconds claimed, represented as a UQ32.128 |
| numberOfStakes | uint96 | The count of deposits that are currently staked for the incentive |

### deposits

```solidity
function deposits(uint256 tokenId) external view returns (address owner, uint48 numberOfStakes, int24 tickLower, int24 tickUpper)
```

Returns information about a deposited NFT

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| owner | address | The owner of the deposited NFT |
| numberOfStakes | uint48 | Counter of how many incentives for which the liquidity is staked |
| tickLower | int24 | The lower tick of the range |
| tickUpper | int24 | The upper tick of the range |

### stakes

```solidity
function stakes(uint256 tokenId, bytes32 incentiveId) external view returns (uint160 secondsPerLiquidityInsideInitialX128, uint128 liquidity)
```

Returns information about a staked liquidity NFT

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The ID of the staked token |
| incentiveId | bytes32 | The ID of the incentive for which the token is staked |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| secondsPerLiquidityInsideInitialX128 | uint160 | secondsPerLiquidity represented as a UQ32.128 |
| liquidity | uint128 | The amount of liquidity in the NFT as of the last time the rewards were computed |

### rewards

```solidity
function rewards(contract IERC20Minimal rewardToken, address owner) external view returns (uint256 rewardsOwed)
```

Returns amounts of reward tokens owed to a given address according to the last time all stakes were updated

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardToken | contract IERC20Minimal | The token for which to check rewards |
| owner | address | The owner for which the rewards owed are checked |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardsOwed | uint256 | The amount of the reward token claimable by the owner |

### createIncentive

```solidity
function createIncentive(struct IUniswapV3Staker.IncentiveKey key, uint256 reward) external
```

Creates a new liquidity mining incentive program

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | Details of the incentive to create |
| reward | uint256 | The amount of reward tokens to be distributed |

### endIncentive

```solidity
function endIncentive(struct IUniswapV3Staker.IncentiveKey key) external returns (uint256 refund)
```

Ends an incentive after the incentive end time has passed and all stakes have been withdrawn

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | Details of the incentive to end |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| refund | uint256 | The remaining reward tokens when the incentive is ended |

### transferDeposit

```solidity
function transferDeposit(uint256 tokenId, address to) external
```

Transfers ownership of a deposit from the sender to the given recipient

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The ID of the token (and the deposit) to transfer |
| to | address | The new owner of the deposit |

### withdrawToken

```solidity
function withdrawToken(uint256 tokenId, address to, bytes data) external
```

Withdraws a Uniswap V3 LP token `tokenId` from this contract to the recipient `to`

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The unique identifier of an Uniswap V3 LP token |
| to | address | The address where the LP token will be sent |
| data | bytes | An optional data array that will be passed along to the `to` address via the NFT safeTransferFrom |

### stakeToken

```solidity
function stakeToken(struct IUniswapV3Staker.IncentiveKey key, uint256 tokenId) external
```

Stakes a Uniswap V3 LP token

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | The key of the incentive for which to stake the NFT |
| tokenId | uint256 | The ID of the token to stake |

### unstakeToken

```solidity
function unstakeToken(struct IUniswapV3Staker.IncentiveKey key, uint256 tokenId) external
```

Unstakes a Uniswap V3 LP token

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | The key of the incentive for which to unstake the NFT |
| tokenId | uint256 | The ID of the token to unstake |

### claimReward

```solidity
function claimReward(contract IERC20Minimal rewardToken, address to, uint256 amountRequested) external returns (uint256 reward)
```

Transfers `amountRequested` of accrued `rewardToken` rewards from the contract to the recipient `to`

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardToken | contract IERC20Minimal | The token being distributed as a reward |
| to | address | The address where claimed rewards will be sent to |
| amountRequested | uint256 | The amount of reward tokens to claim. Claims entire reward amount if set to 0. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| reward | uint256 | The amount of reward tokens claimed |

### getRewardInfo

```solidity
function getRewardInfo(struct IUniswapV3Staker.IncentiveKey key, uint256 tokenId) external returns (uint256 reward, uint160 secondsInsideX128)
```

Calculates the reward amount that will be received for the given stake

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| key | struct IUniswapV3Staker.IncentiveKey | The key of the incentive |
| tokenId | uint256 | The ID of the token |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| reward | uint256 | The reward accrued to the NFT for the given incentive thus far |
| secondsInsideX128 | uint160 |  |

### IncentiveCreated

```solidity
event IncentiveCreated(contract IERC20Minimal rewardToken, contract IUniswapV3Pool pool, uint256 startTime, uint256 endTime, address refundee, uint256 reward)
```

Event emitted when a liquidity mining incentive has been created

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| rewardToken | contract IERC20Minimal | The token being distributed as a reward |
| pool | contract IUniswapV3Pool | The Uniswap V3 pool |
| startTime | uint256 | The time when the incentive program begins |
| endTime | uint256 | The time when rewards stop accruing |
| refundee | address | The address which receives any remaining reward tokens after the end time |
| reward | uint256 | The amount of reward tokens to be distributed |

### IncentiveEnded

```solidity
event IncentiveEnded(bytes32 incentiveId, uint256 refund)
```

Event that can be emitted when a liquidity mining incentive has ended

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| incentiveId | bytes32 | The incentive which is ending |
| refund | uint256 | The amount of reward tokens refunded |

### DepositTransferred

```solidity
event DepositTransferred(uint256 tokenId, address oldOwner, address newOwner)
```

Emitted when ownership of a deposit changes

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The ID of the deposit (and token) that is being transferred |
| oldOwner | address | The owner before the deposit was transferred |
| newOwner | address | The owner after the deposit was transferred |

### TokenStaked

```solidity
event TokenStaked(uint256 tokenId, bytes32 incentiveId, uint128 liquidity)
```

Event emitted when a Uniswap V3 LP token has been staked

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The unique identifier of an Uniswap V3 LP token |
| incentiveId | bytes32 | The incentive in which the token is staking |
| liquidity | uint128 | The amount of liquidity staked |

### TokenUnstaked

```solidity
event TokenUnstaked(uint256 tokenId, bytes32 incentiveId)
```

Event emitted when a Uniswap V3 LP token has been unstaked

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenId | uint256 | The unique identifier of an Uniswap V3 LP token |
| incentiveId | bytes32 | The incentive in which the token is staking |

### RewardClaimed

```solidity
event RewardClaimed(address to, uint256 reward)
```

Event emitted when a reward token has been claimed

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| to | address | The address where claimed rewards were sent to |
| reward | uint256 | The amount of reward tokens claimed |

## Multicall

Enables calling multiple methods in a single call to the contract

### multicall

```solidity
function multicall(bytes[] data) external payable returns (bytes[] results)
```

Call multiple functions in the current contract and return the data from all of them if they all succeed

_The `msg.value` should not be trusted for any method callable from multicall._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| data | bytes[] | The encoded function data for each of the calls to make to this contract |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| results | bytes[] | The results from each of the calls passed in via data |

## PoolAddress

### POOL_INIT_CODE_HASH

```solidity
bytes32 POOL_INIT_CODE_HASH
```

### PoolKey

```solidity
struct PoolKey {
  address token0;
  address token1;
  uint24 fee;
}
```

### getPoolKey

```solidity
function getPoolKey(address tokenA, address tokenB, uint24 fee) internal pure returns (struct PoolAddress.PoolKey)
```

Returns PoolKey: the ordered tokens with the matched fee levels

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tokenA | address | The first token of a pool, unsorted |
| tokenB | address | The second token of a pool, unsorted |
| fee | uint24 | The fee level of the pool |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | struct PoolAddress.PoolKey | Poolkey The pool details with ordered token0 and token1 assignments |

### computeAddress

```solidity
function computeAddress(address factory, struct PoolAddress.PoolKey key) internal pure returns (address pool)
```

Deterministically computes the pool address given the factory and PoolKey

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| factory | address | The Uniswap V3 factory contract address |
| key | struct PoolAddress.PoolKey | The PoolKey |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| pool | address | The contract address of the V3 pool |

## TickMath

Computes sqrt price for ticks of size 1.0001, i.e. sqrt(1.0001^tick) as fixed point Q64.96 numbers. Supports
prices between 2**-128 and 2**128

### MIN_TICK

```solidity
int24 MIN_TICK
```

_The minimum tick that may be passed to #getSqrtRatioAtTick computed from log base 1.0001 of 2**-128_

### MAX_TICK

```solidity
int24 MAX_TICK
```

_The maximum tick that may be passed to #getSqrtRatioAtTick computed from log base 1.0001 of 2**128_

### MIN_SQRT_RATIO

```solidity
uint160 MIN_SQRT_RATIO
```

_The minimum value that can be returned from #getSqrtRatioAtTick. Equivalent to getSqrtRatioAtTick(MIN_TICK)_

### MAX_SQRT_RATIO

```solidity
uint160 MAX_SQRT_RATIO
```

_The maximum value that can be returned from #getSqrtRatioAtTick. Equivalent to getSqrtRatioAtTick(MAX_TICK)_

### getSqrtRatioAtTick

```solidity
function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160 sqrtPriceX96)
```

Calculates sqrt(1.0001^tick) * 2^96

_Throws if |tick| > max tick_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| tick | int24 | The input tick for the above formula |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| sqrtPriceX96 | uint160 | A Fixed point Q64.96 number representing the sqrt of the ratio of the two assets (token1/token0) at the given tick |

### getTickAtSqrtRatio

```solidity
function getTickAtSqrtRatio(uint160 sqrtPriceX96) internal pure returns (int24 tick)
```

Calculates the greatest tick value such that getRatioAtTick(tick) <= ratio

_Throws in case sqrtPriceX96 < MIN_SQRT_RATIO, as MIN_SQRT_RATIO is the lowest value getRatioAtTick may
ever return._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| sqrtPriceX96 | uint160 | The sqrt ratio for which to compute the tick as a Q64.96 |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| tick | int24 | The greatest tick for which the ratio is less than or equal to the input ratio |

## TransferHelper

### safeTransferFrom

```solidity
function safeTransferFrom(address token, address from, address to, uint256 value) internal
```

Transfers tokens from the targeted address to the given destination
Errors with 'STF' if transfer fails

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| token | address | The contract address of the token to be transferred |
| from | address | The originating address from which the tokens will be transferred |
| to | address | The destination address of the transfer |
| value | uint256 | The amount to be transferred |

### safeTransfer

```solidity
function safeTransfer(address token, address to, uint256 value) internal
```

Transfers tokens from msg.sender to a recipient

_Errors with ST if transfer fails_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| token | address | The contract address of the token which will be transferred |
| to | address | The recipient of the transfer |
| value | uint256 | The value of the transfer |

### safeApprove

```solidity
function safeApprove(address token, address to, uint256 value) internal
```

Approves the stipulated contract to spend the given allowance in the given token

_Errors with 'SA' if transfer fails_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| token | address | The contract address of the token to be approved |
| to | address | The target of the approval |
| value | uint256 | The amount of the given token the target will be allowed to spend |

### safeTransferETH

```solidity
function safeTransferETH(address to, uint256 value) internal
```

Transfers ETH to the recipient address

_Fails with `STE`_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| to | address | The destination of the transfer |
| value | uint256 | The value to be transferred |

