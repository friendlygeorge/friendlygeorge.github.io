---
layout: page
title: "Jobber MCP Server — Field Service Data for AI Agents"
---

# Jobber MCP Server — Field Service Data for AI Agents

> An MCP server for [Jobber](https://www.getjobber.com) — connect any MCP-compatible client to your Jobber field-service data. 6 tools for clients, jobs, invoices, and quotes.

**Source:** [github.com/friendlygeorge/jobber-mcp-server](https://github.com/friendlygeorge/jobber-mcp-server) · **npm:** [@supernova123/jobber-mcp-server](https://www.npmjs.com/package/@supernova123/jobber-mcp-server) · **License:** MIT · **Maintained by:** Nova

---

## What It Does

| Category | Tools | Description |
|----------|-------|-------------|
| Client Management | `list_clients`, `get_client` | Find clients, view contact info and job history |
| Job Operations | `get_job` | Full job detail: status, assignees, schedule, line items |
| Invoicing | `list_invoices`, `get_invoice` | Track invoices by status, view payment details |
| Quote Creation | `create_quote` | Create and send quotes with line items |

---

## Quick Start

```bash
npx @supernova123/jobber-mcp-server
```

### Claude Desktop Config

```json
{
  "mcpServers": {
    "jobber": {
      "command": "npx",
      "args": ["-y", "@supernova123/jobber-mcp-server"],
      "env": {
        "JOBBER_ACCESS_TOKEN": "your_token",
        "JOBBER_CLIENT_ID": "your_client_id",
        "JOBBER_CLIENT_SECRET": "your_client_secret"
      }
    }
  }
}
```

Get API credentials at [Jobber Developer Portal](https://developer.getjobber.com/).

### Try It Without an Account

```bash
JOBBER_MOCK_MODE=true npx @supernova123/jobber-mcp-server
```

### Claude Code

```bash
claude mcp add jobber npx -y @supernova123/jobber-mcp-server
```

---

## Why This Server Exists

Jobber is great field-service management software, but checking on jobs, clients, and invoices means logging into their dashboard. This server makes it conversational — ask about overdue invoices, check today's jobs, or create a quote without opening another tab.

**Mock mode** lets you try it instantly with fake data, no Jobber account needed.

---

## Example Prompts

- "List all my clients"
- "Show me the details for client-101"
- "What jobs are assigned to Alex Reyes?"
- "Create a quote for Northwind Roofing: 2 hours of emergency repair at $150/hr"
- "Which invoices are overdue?"

---

## Security

- API credentials stored in environment variables (never logged)
- Read-only for most operations (quote creation is the only write)
- Mock mode available for testing without credentials
