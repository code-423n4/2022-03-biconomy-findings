

C4 finding submitted: (risk = G (Gas Optimization))
require error messages longer than 32 bytes

## Lines of code
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/ExecutorManager.sol#L17
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/LiquidityPool.sol#L77

## Vulnerability details
Error strings longer than 32 bytes are more expensive

## Impact
https://blog.polymath.network/solidity-tips-and-tricks-to-save-gas-and-reduce-bytecode-size-c44580b218e6#c17b

## Proof of Concept
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/ExecutorManager.sol#L17
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/LiquidityPool.sol#L77

## Tools Used
Manual analysis

## Recommended Mitigation Steps
Limit the error strings to 32 bytes max




C4 finding submitted: (risk = G (Gas Optimization))
For loop index increment can be made unchecked

## Lines of code
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/ExecutorManager.sol#L31
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/ExecutorManager.sol#L47
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/token/TokenManager.sol#L78
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/LiquidityFarming.sol#L233
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/WhitelistPeriodManager.sol#L180
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/WhitelistPeriodManager.sol#L228
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/WhitelistPeriodManager.sol#L248
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/token/LPToken.sol#L77

## Vulnerability details
There is no risk of overflowing the index of the for loops. Therefore, they can be changed to unchecked to save gas.
This would save more gas as iterations in the loop increases. 

## Impact


## Proof of Concept
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/ExecutorManager.sol#L31
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/ExecutorManager.sol#L47
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/token/TokenManager.sol#L78
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/LiquidityFarming.sol#L233
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/WhitelistPeriodManager.sol#L180
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/WhitelistPeriodManager.sol#L228
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/WhitelistPeriodManager.sol#L248
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/token/LPToken.sol#L77

## Tools Used
Manual analysis

## Recommended Mitigation Steps
Change the index increments to unchecked such as:
    function addExecutors(address[] calldata executorArray) external {
        for (uint256 i = 0; i < executorArray.length; ) {
            addExecutor(executorArray[i]);
            unchecked { ++i; }
        }
    }



C4 finding submitted: (risk = G (Gas Optimization))
Redundant index initialisation

## Lines of code
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/ExecutorManager.sol#L31
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/ExecutorManager.sol#L47
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/token/TokenManager.sol#L78
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/LiquidityFarming.sol#L233
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/WhitelistPeriodManager.sol#L180
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/WhitelistPeriodManager.sol#L228
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/token/LPToken.sol#L77

## Vulnerability details
No need to set the uint256 index to zero since uint256 defaults to zero.

## Impact


## Proof of Concept
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/ExecutorManager.sol#L31
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/ExecutorManager.sol#L47
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/token/TokenManager.sol#L78
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/LiquidityFarming.sol#L233
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/WhitelistPeriodManager.sol#L180
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/WhitelistPeriodManager.sol#L228
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/WhitelistPeriodManager.sol#L248
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/token/LPToken.sol#L77

## Tools Used
Manual analysis

## Recommended Mitigation Steps
Remove the index settings to zero.




C4 finding submitted: (risk = G (Gas Optimization))
Subtraction can be made unchecked

## Lines of code
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/LiquidityPool.sol#L179

## Vulnerability details
Since currentLiquidity can not be greater than providedLiquidity here, subtraction can be made unchecked.

## Impact
Saves 2352 gas

## Proof of Concept
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/LiquidityPool.sol#L179


## Tools Used
Remix

## Recommended Mitigation Steps
Change LiquidityPool.sol#L179 as:
            unchecked { liquidityDifference = providedLiquidity - currentLiquidity; }





C4 finding submitted: (risk = G (Gas Optimization))
tokenManager.getTokensInfo(tokenAddress).equilibriumFee can be cached in getAmountToTransfer()

## Lines of code
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/LiquidityPool.sol#L316
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/LiquidityPool.sol#L318
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/LiquidityPool.sol#L321

## Vulnerability details
tokenManager.getTokensInfo(tokenAddress).equilibriumFee is used 3 times in this function. It can be cached 
rather than reading from state everytime.

## Impact
Saves 56369 gas

## Proof of Concept
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/LiquidityPool.sol#L316
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/LiquidityPool.sol#L318
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/LiquidityPool.sol#L321

## Tools Used
Remix

## Recommended Mitigation Steps
Cache the value as:
	uint256 _equilibriumFee = tokenManager.getTokensInfo(tokenAddress).equilibriumFee;
And use the equilibriumFee instead.



C4 finding submitted: (risk = G (Gas Optimization))
Use local variable

## Lines of code
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/LiquidityProviders.sol#L183

## Vulnerability details
totalSharesMinted[_baseToken] is already cached in supply. Use supply rather than reading from the state.

## Impact

## Proof of Concept
https://github.com/code-423n4/2022-03-biconomy/blob/main/contracts/hyphen/LiquidityProviders.sol#L183

## Tools Used
Manual analysis

## Recommended Mitigation Steps
Change LiquidityProviders.sol#L183 as:
	return supply / totalReserve[_baseToken];
