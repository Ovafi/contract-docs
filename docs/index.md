# Ova V1 Smart Contracts
Welcome to the documentation for Ova V1 smart contracts.

This resource provides guides and technical references for the Ova V1 Smart Contracts. Below, you will find the Solidity API documentation to help you understand the smart contracts and facilitate integrations.

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

### rewardsPerYearMultiplierNum

```solidity
mapping(address => uint256) rewardsPerYearMultiplierNum
```

The emitted amount of reward for each year multiplier numerator.

### rewardsPerYearMultiplierDen

```solidity
mapping(address => uint256) rewardsPerYearMultiplierDen
```

The emitted amount of reward for each year multiplier denominator.

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

_This is allowed both before and after the end of pool endTimeStamp_

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

_This is allowed both before and after the end of pool endTimeStamp_

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
| stakedAsset | contract IERC20 | the wanted token. |
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
function _getMultiplier(uint256 pid) internal view returns (uint256)
```

Get the multiplier value calculated between two times.

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pid | uint256 | the pool id. |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| [0] | uint256 | The difference between the two sides multiplied for the bonus. |

## SingleStableStake

Single stable coin staking contract implementation.
This contract supports multiple staking pools to be deployed in the same contract sharing the reward token.

### rewardsPerYearMultiplierNum

```solidity
mapping(address => uint256) rewardsPerYearMultiplierNum
```

The emitted amount of reward for each year multiplier numerator.

### rewardsPerYearMultiplierDen

```solidity
mapping(address => uint256) rewardsPerYearMultiplierDen
```

The emitted amount of reward for each year multiplier denominator.

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

### AlreadyUsedStakedAsset

```solidity
error AlreadyUsedStakedAsset()
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

## SingleAdminAccessControl

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

New admin role acceptance

### grantRole

```solidity
function grantRole(bytes32 role, address account) public
```

Grant a role
Can only be executed by the current single admin
Admin role cannot be granted externally

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| role | bytes32 | bytes32 |
| account | address | address |

### revokeRole

```solidity
function revokeRole(bytes32 role, address account) public
```

Revoke a role
Can only be executed by the current admin
Admin role cannot be revoked

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

No way to change admin without removing old admin first

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

## CollateralSpenderManager

This contract handles the collateral spender for USDO

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

@notice The time interval needed to changed a spender address

### approvedCollateralSpender

```solidity
address approvedCollateralSpender
```

@notice The unique approved collateral spender

### proposedSpender

```solidity
address proposedSpender
```

@notice The proposed new spender

### proposalTime

```solidity
uint256 proposalTime
```

@notice The last proposal time

### constructor

```solidity
constructor(address admin, struct MintRedeemManagerTypes.StableCoin usdc_, struct MintRedeemManagerTypes.StableCoin usdt_, struct MintRedeemManagerTypes.StableCoin aUsdc_, struct MintRedeemManagerTypes.StableCoin aUsdt_) internal
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

Max minted USDO allowed per block

### maxRedeemPerBlock

```solidity
uint256 maxRedeemPerBlock
```

@notice Max redeemed USDO allowed per block

### emergencyMode

```solidity
bool emergencyMode
```

@notice If protocol is in emergency mode

### belowMaxMintPerBlock

```solidity
modifier belowMaxMintPerBlock(uint256 mintAmount)
```

Ensure that the already minted USDO in the actual block plus the amount to be minted is below the maxMintPerBlock

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| mintAmount | uint256 | The USDO amount to be minted |

### belowMaxRedeemPerBlock

```solidity
modifier belowMaxRedeemPerBlock(uint256 redeemAmount)
```

Ensure that the already redeemed USDO in the actual block plus the amount to be redeemed is below the maxRedeemPerBlock

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| redeemAmount | uint256 | The USDO amount to be redeemed |

### constructor

```solidity
constructor(struct MintRedeemManagerTypes.StableCoin usdc_, struct MintRedeemManagerTypes.StableCoin usdt_, struct MintRedeemManagerTypes.StableCoin aUsdc_, struct MintRedeemManagerTypes.StableCoin aUsdt_, address admin, uint256 decimals, uint256 maxMintPerBlock_, uint256 maxRedeemPerBlock_) internal
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

_The spender is handled by the CollateralSpenderManager contract
Normally this function is not used as the approval is managed by the acceptance flow_

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
| collateralManager | address | The address to remove the COLLATERAL_MANAGER_ROLE role from |

### setEmergencyStatus

```solidity
function setEmergencyStatus(bool emergencyMode_) external
```

Change the protocol emergency mode

_Only default admin can call this function
If any additional stable coin is found (USDC or USDT) is present here, consider calling `supplyToBacking` first as that call may fail if called from here under some unusual circumstances_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| emergencyMode_ | bool | The mode to be set |

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

### supplyToBacking

```solidity
function supplyToBacking() external
```

Supply funds to the active backing contract (aka approvedCollateralSpender)

_The approveCollateralSpender will colect the funds, as the only entity allowed to do so_

### _validateInvariant

```solidity
function _validateInvariant(struct MintRedeemManagerTypes.Order order) internal view
```

Check mint and redeem invariant

_This invariant holds only if _decimals >= usdc.decimals >= usdt.decimals_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| order | struct MintRedeemManagerTypes.Order | A struct containing the order |

### _validateInputTokens

```solidity
function _validateInputTokens(struct MintRedeemManagerTypes.Order order) internal view
```

Check order parameters based on protocol emergency status

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| order | struct MintRedeemManagerTypes.Order | A struct containing the order |

### _managerMint

```solidity
function _managerMint(struct MintRedeemManagerTypes.Order order) internal
```

Mint stablecoins from assets

_Order benefactor is not used as we constraint it to be the msg.sender at higher level
The received funds are supplied to the backing contract_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| order | struct MintRedeemManagerTypes.Order | Struct containing order details |

### _managerRedeem

```solidity
function _managerRedeem(struct MintRedeemManagerTypes.Order order) internal returns (uint256 amountToBurn, uint256 usdcBack, uint256 usdtBack)
```

Redeem stablecoins for assets

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| order | struct MintRedeemManagerTypes.Order | Struct containing order details |

### _withdrawFromProtocol

```solidity
function _withdrawFromProtocol(uint256 amount) internal returns (uint256 checkedBurnAmount, uint256 usdcBack, uint256 usdtBack)
```

Redeem collateral from the protocol

_It will trigger the backing contract (aka approvedCollateralSpender) withdraw method if the collateral is not sufficient
When calling `IUSDOBacking(approvedCollateralSpender).withdraw(...)`,
it is possible that some standard collateral has not yet been converted into aTokens during emergency mode.
Additionally, if a large amount was minted before entering emergency mode, USDC and USDT collateral might become
locked in this contract until they are eventually transferable under unusual circumstances.
We are aware of this issue, and the necessary funds will be manually provided to the `approvedCollateralSpender` to facilitate withdrawals._

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| amount | uint256 | The amount of USDO to burn |

#### Return Values

| Name | Type | Description |
| ---- | ---- | ----------- |
| checkedBurnAmount | uint256 | The checked amount to burn |
| usdcBack | uint256 | The amount of USDC or their aToken version returned to user |
| usdtBack | uint256 | The amount of USDT or their aToken version returned to user |

### _transferToBeneficiary

```solidity
function _transferToBeneficiary(address beneficiary, address asset, uint256 amount) internal
```

Transfer supported asset to beneficiary address

_This contract needs to have available funds
Asset validation has to be performed by the caller_

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

Transfer supported asset to target addresses

_User must have approved this contract for allowance
Asset validation has to be performed by the caller_

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

## MintableTokenBase

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

### StakingPoolSet

```solidity
event StakingPoolSet(address[] pools)
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
function consumeReferral(string code) external
```

Consume a referral code. This action will harvest all the user positions in the staking pools

_Code holders can not use any code
Staking pools must be set_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| code | string | The referral code |

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

_This contract is intended to be inherited in order to define custom vesting (cooldowns) policies_

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

Ensure input amount nonzero

### notOwner

```solidity
modifier notOwner(address target)
```

Ensures blacklist target is not owner

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

Ensures a small non-zero amount of shares does not remain, exposing to donation attack

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

Updata the vesting amount

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| newVestingAmount | uint256 | The new vesting amount |

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

Ensure cooldownDuration is zero

### ensureCooldownOn

```solidity
modifier ensureCooldownOn()
```

Ensure cooldownDuration is gt 0

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

_Unstake can be called after cooldown have been set to 0, to let accounts to be able to claim remaining assets locked at Silo_

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| receiver | address | Address to send the assets by the staker |

### cooldownAssets

```solidity
function cooldownAssets(uint256 assets) external returns (uint256 shares)
```

Redeem assets and starts a cooldown to claim the converted underlying asset

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| assets | uint256 | Assets to redeem |

### cooldownShares

```solidity
function cooldownShares(uint256 shares) external returns (uint256 assets)
```

Redeem shares into assets and starts a cooldown to claim the converted underlying asset

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| shares | uint256 | Shares to redeem |

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

The Second Layer stable coin

### blacklist

```solidity
mapping(address => bool) blacklist
```

Blacklisted accounts

### notDisabled

```solidity
modifier notDisabled(address account)
```

### constructor

```solidity
constructor(address admin, struct MintRedeemManagerTypes.StableCoin usdc_, struct MintRedeemManagerTypes.StableCoin usdt_, struct MintRedeemManagerTypes.StableCoin aUsdc_, struct MintRedeemManagerTypes.StableCoin aUsdt_, uint256 maxMintPerBlock_, uint256 maxRedeemPerBlock_) public
```

Constructor

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| admin | address | The contract admin |
| usdc_ | struct MintRedeemManagerTypes.StableCoin | The usdc stablecoin struct |
| usdt_ | struct MintRedeemManagerTypes.StableCoin | The ausdt stablecoin struct |
| aUsdc_ | struct MintRedeemManagerTypes.StableCoin |  |
| aUsdt_ | struct MintRedeemManagerTypes.StableCoin |  |
| maxMintPerBlock_ | uint256 | Max mint amount for each block |
| maxRedeemPerBlock_ | uint256 | Max redeem amount for each block |

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

## USDOCollateral

This contract handles the collateral definitions for USDO

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

### aUsdt

```solidity
struct MintRedeemManagerTypes.StableCoin aUsdt
```

### aUsdc

```solidity
struct MintRedeemManagerTypes.StableCoin aUsdc
```

### constructor

```solidity
constructor(address admin, struct MintRedeemManagerTypes.StableCoin usdc_, struct MintRedeemManagerTypes.StableCoin usdt_, struct MintRedeemManagerTypes.StableCoin aUsdc_, struct MintRedeemManagerTypes.StableCoin aUsdt_) internal
```

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

### MintRedeemManagerCollateralNotValid

```solidity
error MintRedeemManagerCollateralNotValid()
```

## IMintRedeemManagerEvents

### Received

```solidity
event Received(address, uint256)
```

Event emitted when contract receives ETH

### MintRedeemManagerEmergencyStatus

```solidity
event MintRedeemManagerEmergencyStatus(bool status)
```

Event for signaling emergency mode status

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
function consumeReferral(string code) external
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

