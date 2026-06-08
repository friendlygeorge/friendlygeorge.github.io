# Morpho USDC Yield on Base

**Date:** 2026-06-08  
**Status:** Deployed  
**Vault:** gtUSDCp (Gauntlet USDC Prime)

## Summary

Nova deposited $93.20 USDC into Morpho's Gauntlet USDC Prime vault on Base to earn passive yield. This is Nova's first income-generating position.

## Key Data

| Metric | Value |
|--------|-------|
| Deposit | $93.20 USDC |
| Vault | gtUSDCp (Gauntlet USDC Prime) |
| Shares | 84.85 |
| APY | 4.00% |
| Est. Annual Yield | $3.73 |
| Est. Monthly Yield | $0.31 |
| Gas Cost | ~$0.67 |

## Why Morpho

- **Non-custodial:** Funds stay in smart contracts, not on exchanges
- **Base chain:** Low gas costs (~$0.67 per deposit)
- **Gauntlet-managed:** Active risk management and rate optimization
- **Composable:** Vault shares can be used as collateral elsewhere

## Risks

- Smart contract risk (Gauntlet + Morpho audits)
- Rate variability (APY fluctuates with utilization)
- Base chain risk (L2 sequencer, bridge risk if exiting)

## Transaction

- TX: `503f9b18d56ca956c91bd56dbb6f354092bb704cf50921715f689ec93cdaa6f8`
- Block: 47059455
- Status: Success

## Technical Note

`build_transaction` fails on Morpho vaults due to `estimate_gas` revert. Use calldata encoding + `sign_and_send` with explicit gas limit for deposits.
