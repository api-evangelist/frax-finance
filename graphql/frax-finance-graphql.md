# Frax Finance GraphQL API

## Description

Frax Finance is a fractional-algorithmic stablecoin protocol. Its primary products include FRAX (a partially collateralized stablecoin), FXS (Frax Shares, the governance and utility token), and Fraxswap — a TWAMM (Time-Weighted Average Market Maker) AMM DEX built on top of Uniswap v2-style pairs.

The GraphQL API is delivered via a subgraph on The Graph protocol and exposes on-chain state for Fraxswap on Ethereum: token and pair analytics, swap and liquidity events, TWAMM long-term order tracking, and time-series data bucketed by hour and day.

## Endpoint

- **Network**: Ethereum Mainnet
- **Subgraph**: Fraxswap Ethereum
- **Source repo**: https://github.com/FraxFinance/fraxswap-subgraph
- **The Graph hosted service (legacy)**: `https://api.thegraph.com/subgraphs/name/frax-finance/fraxswap-ethereum`
- **The Graph decentralized network**: `https://gateway.thegraph.com/api/{api-key}/subgraphs/id/<subgraph-id>`

## Documentation

- Frax Finance docs: https://docs.frax.finance
- Fraxswap overview: https://docs.frax.finance/fraxswap
- The Graph docs: https://thegraph.com/docs/en/querying/querying-the-graph/

## Key Types

| Type | Description |
|------|-------------|
| `Factory` | Global protocol-level stats (volume, liquidity, pair/token/user counts) |
| `Pair` | Fraxswap liquidity pair with TWAMM reserves and lifetime stats |
| `Token` | ERC-20 token with volume, liquidity, and price derived in ETH |
| `Swap` | Individual swap event within a pair |
| `Mint` | Liquidity add event |
| `Burn` | Liquidity remove event |
| `Transaction` | On-chain transaction grouping mints, burns, and swaps |
| `LiquidityPosition` | A user's LP position in a specific pair |
| `LiquidityPositionSnapshot` | Point-in-time snapshot of an LP position for return calculations |
| `HourData` | Protocol-level hourly volume and liquidity aggregates |
| `DayData` | Protocol-level daily volume and liquidity aggregates |
| `TokenHourData` | Per-token hourly stats |
| `TokenDayData` | Per-token daily stats |
| `PairHourData` | Per-pair hourly stats including TWAMM reserves |
| `PairDayData` | Per-pair daily stats including TWAMM reserves |
| `User` | Wallet address with derived liquidity positions |
| `Bundle` | ETH/USD price feed used for USD value derivation |
| `LongTermSwap0To1` | TWAMM long-term order selling token0 for token1 |
| `LongTermSwap1To0` | TWAMM long-term order selling token1 for token0 |
| `CancelLongTermOrder` | Cancellation event for a TWAMM long-term order |
| `WithdrawProceedsFromLongTermOrder` | Proceeds withdrawal from a TWAMM order |
| `VirtualOrderExecution` | TWAMM virtual order execution checkpoint |
| `Approval` | ERC-20 approval event |
| `Transfer` | ERC-20 transfer event |
| `Sync` | Reserve sync event including TWAMM reserves |

## Notes

- The schema is sourced from the official [fraxswap-subgraph](https://github.com/FraxFinance/fraxswap-subgraph) repository.
- Fraxswap pairs include `twammReserve0` and `twammReserve1` fields in addition to standard AMM reserves, reflecting long-term TWAMM order inventory.
- The Graph hosted service (api.thegraph.com) is being deprecated; use the decentralized network or a gateway for production queries.
- Schema retrieved: 2026-06-14
