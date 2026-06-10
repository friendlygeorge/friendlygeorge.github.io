---
layout: page
title: "Resend MCP Server — Transactional Email for AI Agents"
---

# Resend MCP Server — Transactional Email for AI Agents

> An MCP server for [Resend](https://resend.com) — connect any MCP-compatible client to the Resend transactional email API. 18 tools for sending emails, managing domains, API keys, audiences, and contacts.

**Source:** [github.com/friendlygeorge/resend-mcp-server](https://github.com/friendlygeorge/resend-mcp-server) · **npm:** [@supernova123/resend-mcp-server](https://www.npmjs.com/package/@supernova123/resend-mcp-server) · **License:** MIT · **Maintained by:** Nova

---

## What It Does

| Category | Tools | Description |
|----------|-------|-------------|
| Email Sending | `send_email`, `send_batch_email`, `list_emails`, `get_email` | Send single or batch emails, track delivery status |
| Domain Management | `create_domain`, `list_domains`, `verify_domain`, `delete_domain` | Manage sending domains and DNS verification |
| API Key Management | `create_api_key`, `list_api_keys`, `delete_api_key` | Mint and revoke API keys with scoped permissions |
| Audience & Contacts | `list_audiences`, `create_audience`, `list_contacts`, `get_contact`, `create_contact`, `update_contact`, `delete_contact` | Full contact CRUD across audiences |

---

## Quick Start

```bash
npx @supernova123/resend-mcp-server
```

### Claude Desktop Config

```json
{
  "mcpServers": {
    "resend": {
      "command": "npx",
      "args": ["-y", "@supernova123/resend-mcp-server"],
      "env": {
        "RESEND_API_KEY": "re_xxxxxxxxxxxx"
      }
    }
  }
}
```

Get a free API key at [resend.com/api-keys](https://resend.com/api-keys).

### Claude Code

```bash
claude mcp add resend npx -y @supernova123/resend-mcp-server
```

---

## Why This Server Exists

Resend is the modern email API for developers, but managing domains, contacts, and sending emails requires API calls and JSON. This server makes it conversational — send an email by talking, manage your infrastructure through natural language, and automate email workflows without leaving your AI assistant.

---

## Example Prompts

- "Send an email to jane@example.com thanking her for signing up"
- "List the last 5 emails I sent"
- "What happened to email ID abc-123?"
- "Create a new sending domain for mail.acme.com"
- "Add jane@example.com to audience audience-1"

---

## Security

- API key stored in environment variable (never logged)
- Rate-limited automatically (10 req/s)
- Works with Resend free tier (100 emails/day)
