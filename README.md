# AgoraSwap

A suite of persistent, non-upgradable smart contracts that together create an automated market maker, a protocol that facilitates peer-to-peer market making and swapping of ERC-20 tokens on EVM compatible blockchains.

The Uniswap V2 protocol was forked from commit [4dd59067c76dea4a0e8e4bfdda41877a6b16dedc](https://github.com/Uniswap/v2-core/tree/4dd59067c76dea4a0e8e4bfdda41877a6b16dedc).

AgoraSwap is an exact fork of [Uniswap V2](https://uniswap.org) with the addition of a new `pull` function that allows retrieval of tokens from the LP contract excluding those corresponding to the pair itself.

For instance if there is a ABC-DEF LP and there are GHI tokens also in that contract for some reason, anyone may trigger the `pull` function that would retrieve the GHI tokens and send them to the `feeTo` address.

Note that this would not work if someone tried to pull either ABC or DEF from the LP contract.
The objective behind addition of this function is to support harvesting of rewards associated with LP contracts of yield generating assets.

For instance ktoken holders on Agora earn Agora rewards. A ktoken LP such as kUSDC-kMETIS would earn Agora rewards. However they would accrue to the LP contract address and would effectively be lost if there was no means to retrieve these reward tokens.
The addition of a `pull` function that only works for non LP tokens solves the problem.

### Deployed Contracts

- Factory - [0xE3E78432168eac2c7132395539849690258741F3](https://andromeda-explorer.metis.io/address/0xE3E78432168eac2c7132395539849690258741F3/contracts)
- Router - [0x7578870127E7F4ec27f90A0D6df1BB42D460aAAB](https://andromeda-explorer.metis.io/address/0x7578870127E7F4ec27f90A0D6df1BB42D460aAAB/contracts)

### Contract Diff Reports

- [UniswapV2Factory](https://diffchecker.com/3VqiShON)
- [UniswapV2Router02](https://diffchecker.com/7Ate1tYf)

## Local Development

The following assumes the use of `node@>=10`.

### Install Dependencies

`yarn`

### Compile Contracts

`yarn compile`

### Run Tests

`yarn test`
