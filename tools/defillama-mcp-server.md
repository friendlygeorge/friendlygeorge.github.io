---
layout: page
title: "DeFi Llama MCP Server — Free DeFi Protocol Data for AI Agents"
---

# DeFi Llama MCP Server — Free DeFi Protocol Data for AI Agents

> An MCP server for [DeFi Llama](https://defillama.com) — connect any MCP-compatible client to free DeFi protocol data. 8 tools for TVL tracking, yield comparison, stablecoin analysis, and cross-chain bridge monitoring.

**Source:** [github.com/friendlygeorge/defillama-mcp-server](https://github.com/friendlygeorge/defillama-mcp-server) · **npm:** [@supernova123/defillama-mcp-server](https://www.npmjs.com/package/@supernova123/defillama-mcp-server) · **License:** MIT · **Maintained by:** Nova

---

## What It Does

| Category | Tools | Description |
|----------|-------|-------------|
| Protocol Data | `search_protocols`, `get_protocol_tvl` | Find protocols and get detailed TVL breakdowns by chain |
| Chain Analytics | `get_tvl_by_chain` | Total TVL for any chain (Ethereum, Arbitrum, Base, Solana, etc.) |
| Yield Discovery | `get_yields` | Filter lending pools and staking by chain, project, min TVL |
| Market Intelligence | `get_stablecoins`, `get_bridges`, `get_dex_volumes`, `get_protocol_fees` | Stablecoin rankings, bridge TVL, DEX volumes, protocol fees |

---

## Quick Start

```bash
npx @supernova123/defillama-mcp-server
```

### Claude Desktop Config

```json
{
  "mcpServers": {
    "defillama": {
      "command": "npx",
      "args": ["-y", "@supernova123/defillama-mcp-server"]
    }
  }
}
```

### Claude Code

```bash
claude mcp add defillama npx -y @supernova123/defillama-mcp-server
```

---

## Why This Server Exists

DeFi Llama is the gold standard for free DeFi data, but accessing it requires API calls, JSON parsing, and knowing which endpoints exist. This server makes it conversational — ask your AI assistant about TVL movements, yield opportunities, or protocol fees without writing code.

**No API key required** — DeFi Llama is a free public API. Just add it and ask.

---

## Example Prompts

- "What are the top DeFi protocols by TVL on Ethereum?"
- "Search for Aave and show me the chain breakdown"
- "What's the total TVL on Arbitrum?"
- "Show me the highest yield stablecoin pools on Base with at least $10M TVL"
- "Which bridges have the most TVL?"
- "Show me DEX trading volumes for the last 24h"

---

## Security

- No API key stored — runs against public DeFi Llama API
- Read-only — no write operations possible
- Rate-limited automatically (500ms throttle)
