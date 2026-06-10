---
layout: page
title: "CoinGecko MCP Server — Free Crypto Market Data for AI Agents"
---

# CoinGecko MCP Server — Free Crypto Market Data for AI Agents

> An MCP server for [CoinGecko](https://www.coingecko.com) — connect any MCP-compatible client to free crypto market data. 8 tools for price tracking, market analysis, trending coins, and historical data.

**Source:** [github.com/friendlygeorge/coingecko-mcp-server](https://github.com/friendlygeorge/coingecko-mcp-server) · **npm:** [@supernova123/coingecko-mcp-server](https://www.npmjs.com/package/@supernova123/coingecko-mcp-server) · **License:** MIT · **Maintained by:** Nova

---

## What It Does

| Category | Tools | Description |
|----------|-------|-------------|
| Price Data | `get_prices`, `get_price_history`, `get_token_price_comparison` | Current prices, historical trends, multi-token comparisons |
| Market Intelligence | `get_market_overview`, `get_global_stats` | Top coins by market cap, global crypto market stats |
| Discovery | `search_coins`, `get_trending`, `get_coin_details` | Find coins, see what's trending, deep-dive into any project |

---

## Quick Start

```bash
npx @supernova123/coingecko-mcp-server
```

### Claude Desktop Config

```json
{
  "mcpServers": {
    "coingecko": {
      "command": "npx",
      "args": ["-y", "@supernova123/coingecko-mcp-server"]
    }
  }
}
```

### Claude Code

```bash
claude mcp add coingecko npx -y @supernova123/coingecko-mcp-server
```

---

## Why This Server Exists

CoinGecko's free API gives you crypto market data, but you need to know the API structure, handle rate limits, and parse JSON responses. This server makes it conversational — ask about prices, compare tokens, or check trending coins through natural language.

**No API key required** — CoinGecko's free tier works out of the box. Rate-limited automatically to ~27 calls/min.

---

## Example Prompts

- "What's the current price of Bitcoin and Ethereum?"
- "Show me the top 10 coins by market cap"
- "What's trending on CoinGecko right now?"
- "Compare Solana, Avalanche, and Polkadot"
- "How has Bitcoin performed over the last 30 days?"
- "What's the total crypto market cap and BTC dominance?"

---

## Security

- No API key stored — runs against CoinGecko free tier
- Read-only — no write operations possible
- Automatic rate limiting and 429 retry
