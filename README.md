# SimpleSwap Smart Contract Documentation

## Overview

The `SimpleSwap` contract implements a basic liquidity pool for ERC-20 tokens, enabling users to add and remove liquidity, swap tokens, and retrieve token prices. It provides a straightforward interface for token exchanges and liquidity management.

## License

- **SPDX-License-Identifier**: MIT

## Pragma Directive

- Specifies the Solidity compiler version: `pragma solidity ^0.8.0;`

## Contract Description

### SimpleSwap Contract

The `SimpleSwap` contract allows users to manage liquidity and perform token swaps within a pool of ERC-20 tokens.

### Inheritance

- Inherits from the OpenZeppelin ERC20 contract.

### Events

- **LiquidityAdded**: Emitted when liquidity is added to the pool.
- **LiquidityRemoved**: Emitted when liquidity is removed from the pool.
- **TokensSwapped**: Emitted when tokens are swapped.

## Functions

### Constructor

- **constructor()**: 
  - Initializes the ERC-20 token with name "Liquidity" and symbol "LT".

### Liquidity Management

- **addLiquidity**: 
  - Allows users to add liquidity to the token pair in the pool.
  - Parameters:
    - `tokenA`: Address of the first token.
    - `tokenB`: Address of the second token.
    - `amountADesired`: Desired amount of token A to add.
    - `amountBDesired`: Desired amount of token B to add.
    - `amountAMin`: Minimum acceptable amount of token A.
    - `amountBMin`: Minimum acceptable amount of token B.
    - `to`: Address of the recipient of liquidity tokens.
    - `deadline`: Timestamp by which the transaction must be completed.
  - Returns:
    - `amountA`: Effective amount of token A added.
    - `amountB`: Effective amount of token B added.
    - `liquidity`: Amount of liquidity tokens issued.

- **removeLiquidity**: 
  - Allows users to withdraw liquidity from the token pair in the pool.
  - Parameters:
    - `tokenA`: Address of the first token.
    - `tokenB`: Address of the second token.
    - `liquidity`: Amount of liquidity tokens to withdraw.
    - `amountAMin`: Minimum acceptable amount of token A.
    - `amountBMin`: Minimum acceptable amount of token B.
    - `to`: Address of the recipient of the tokens.
    - `deadline`: Timestamp by which the transaction must be completed.
  - Returns:
    - `amountA`: Amount of token A received after removing liquidity.
    - `amountB`: Amount of token B received after removing liquidity.

### Token Swapping

- **swapExactTokensForTokens**: 
  - Swaps an exact amount of one token for another.
  - Parameters:
    - `amountIn`: Amount of input tokens.
    - `amountOutMin`: Minimum acceptable amount of output tokens.
    - `path`: Array of token addresses (input token, output token).
    - `to`: Address of the recipient of the output tokens.
    - `deadline`: Timestamp by which the transaction must be completed.
  - Returns:
    - `amounts`: Array containing the amounts of input and output tokens.

### Price Retrieval

- **getPrice**: 
  - Retrieves the price of one token in terms of another.
  - Parameters:
    - `tokenA`: Address of the first token.
    - `tokenB`: Address of the second token.
  - Returns:
    - `price`: Price of token A in terms of token B.

- **getAmountOut**: 
  - Calculates the amount of tokens received from a swap.
  - Parameters:
    - `amountIn`: Amount of input tokens.
    - `reserveIn`: Current reserves of the input token.
    - `reserveOut`: Current reserves of the output token.
  - Returns:
    - `amountOut`: Amount of tokens to be received.

## Notes

- This contract is a simplified implementation and does not include features such as fee management, slippage control, or advanced price calculations.
- It assumes the existence of an ERC-20 interface for token interactions.

## Final note

The `SimpleSwap` contract provides a fundamental framework for managing liquidity and performing token swaps in an ERC-20 environment. It is suitable for educational and testing purposes, requiring further enhancements for production deployment.
