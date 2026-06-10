---
layout: page
title: "Etherscan MCP Server — Ethereum Blockchain Explorer for AI Agents"
---

# Etherscan MCP Server — Ethereum Blockchain Explorer for AI Agents

> An MCP server that connects AI assistants to Etherscan's Ethereum blockchain explorer. 8 tools for wallet inspection, transaction analysis, and contract ABI retrieval. No API key required.

**Source:** [github.com/friendlygeorge/etherscan-mcp-server](https://github.com/friendlygeorge/etherscan-mcp-server) · **npm:** [@supernova123/etherscan-mcp-server](https://www.npmjs.com/package/@supernova123/etherscan-mcp-server) · **License:** MIT · **Maintained by:** Nova

---

## What It Does

| Category | Tools | Description |
|----------|-------|-------------|
| Wallet Inspection | `get_eth_balance`, `get_token_balances` | Check ETH and ERC-20 holdings for any address |
| Transaction Analysis | `get_transaction`, `get_transactions_by_address`, `get_erc20_transfers`, `get_internal_transactions` | Full transaction history with normal, ERC-20, and internal events |
| Contract Interaction | `get_contract_abi` | Retrieve verified contract ABIs for analysis |
| Gas Monitoring | `get_gas_price` | Current gas oracle (slow/standard/fast in Gwei) |

---

## Quick Start

```bash
npx @supernova123/etherscan-mcp-server
```

### Claude Desktop Config

```json
{
  "mcpServers": {
    "etherscan": {
      "command": "npx",
      "args": ["-y", "@supernova123/etherscan-mcp-server"]
    }
  }
}
```

### Claude Code

```bash
claude mcp add etherscan npx -y @supernova123/etherscan-mcp-server
```

### With API Key (Optional)

Set `ETHERSCAN_API_KEY` for 5 calls/sec instead of 1 call/5s free tier:

```json
{
  "mcpServers": {
    "etherscan": {
      "command": "npx",
      "args": ["-y", "@supernova123/etherscan-mcp-server"],
      "env": {
        "ETHERSCAN_API_KEY": "your_key_here"
      }
    }
  }
}
```

---

## Why This Server Exists

Most blockchain data tools require API keys, complex setup, or only work with specific chains. This server:

- **Works out of the box** — no API key required for basic usage
- **Auto-retries on rate limits** — respects Etherscan's free tier, retries on 429
- **Clean markdown output** — results read naturally in chat
- **Agent-optimized** — tool descriptions written for LLM tool-use patterns
- **8 focused tools** — covers the most common on-chain queries without bloat

---

## Use Cases

- **Wallet auditing** — Check balances, transaction history, and token holdings for any Ethereum address
- **Contract analysis** — Retrieve and analyze verified smart contract ABIs
- **Transaction investigation** — Trace normal, ERC-20, and internal transactions
- **Gas monitoring** — Track current gas prices across slow/standard/fast tiers
- **DeFi research** — Analyze on-chain activity for protocol due diligence

---

## Security

- No private keys or signing capabilities — read-only blockchain queries
- API keys are optional and passed via environment variables only
- Rate limiting is built-in — no risk of exceeding Etherscan's free tier
- Results are markdown-formatted, not executable code

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Rate limited (429) | Server auto-retries. For faster access, set `ETHERSCAN_API_KEY` |
| Empty results | Verify the address is a valid Ethereum address (0x + 40 hex chars) |
| npx not found | Ensure Node.js 18+ is installed: `node --version` |
| Connection errors | Check internet connectivity; Etherscan API requires HTTPS access |
