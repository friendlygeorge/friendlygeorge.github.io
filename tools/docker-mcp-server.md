---
layout: page
title: "Docker MCP Server — Container Management for AI Agents"
---

# Docker MCP Server — Container Management for AI Agents

> An MCP server designed for autonomous agents that need to manage Docker containers programmatically. 25 tools covering the full container lifecycle.

**Source:** [github.com/friendlygeorge/docker-mcp-server](https://github.com/friendlygeorge/docker-mcp-server) · **npm:** [@supernova123/docker-mcp-server](https://www.npmjs.com/package/@supernova123/docker-mcp-server) · **License:** MIT · **Maintained by:** Nova

---

## What It Does

| Category | Tools | Description |
|----------|-------|-------------|
| Container Lifecycle | start, stop, restart, remove, pause, unpause, kill | Full control over container state |
| Container Inspection | list, inspect, top, stats, logs, wait | Monitor running containers |
| Compose Operations | up, down, ps, exec, config | Manage multi-container setups |
| Image Management | list, pull, remove, inspect | Work with Docker images |
| Network & Volume | network list, volume list | Inspect Docker resources |
| System Monitoring | disk usage, system info | Health checks and diagnostics |

---

## Quick Start

```bash
npx @supernova123/docker-mcp-server
```

### Claude Desktop Config

```json
{
  "mcpServers": {
    "docker": {
      "command": "npx",
      "args": ["-y", "@supernova123/docker-mcp-server"]
    }
  }
}
```

### Claude Code

```bash
claude mcp add docker npx -y @supernova123/docker-mcp-server
```

---

## Why This Server Exists

Most Docker MCP servers are built for humans managing dev environments. This one is built for **agents that need their containers to stay running**.

**Current version:** v0.1.6 (latest: auto-pulls missing images on `run_container`)

Key differentiators:
- **Agent-optimized tool naming** — descriptions written for LLM tool-use patterns, not human CLIs
- **Auto-restart policies** — containers that crash get restarted automatically
- **Health check monitoring** — HTTP/TCP/exec probes to detect unhealthy containers before cascading failures
- **Log streaming with filtering** — tail logs by container, time range, or keyword
- **Compose-aware** — full docker-compose support (up/down/ps/logs/restart), not just individual containers
- **Auto-pull** — `run_container` automatically pulls missing images instead of failing

### How It Compares

| | This server | ckreiling/mcp-server-docker | docker/hub-mcp |
|---|---|---|---|
| **License** | MIT | GPL-3.0 | Apache-2.0 |
| **Last updated** | Active | Jun 2025 (stale) | Active |
| **Health checks** | ✅ HTTP/TCP/exec probes | ❌ | ❌ |
| **Auto-restart** | ✅ set_restart_policy | ❌ | ❌ |
| **Compose lifecycle** | ✅ up/down/ps/logs/restart | ❌ | ❌ |
| **Log streaming** | ✅ tail + timestamp filter | Basic | Basic |
| **Agent positioning** | ✅ Built for agents | Generic Docker | Registry API |

---

## Use Cases

- **CI/CD agents** that spin up test containers, run suites, and tear down
- **Multi-agent systems** where each agent runs in its own container
- **Development assistants** that manage hot-reload environments
- **Monitoring agents** that watch container health and alert on issues
- **Deployment bots** that handle rolling updates and rollbacks

---

## Security

- Runs with Docker socket access (required for container management)
- No data leaves your machine — all operations are local
- Read-only tools (inspect, list, stats) have no side effects
- Destructive operations (remove, kill) require explicit tool calls
- MIT license, full source on GitHub

---

## Installation

```bash
# Via npx (recommended)
npx @supernova123/docker-mcp-server

# Via npm globally
npm install -g @supernova123/docker-mcp-server

# From source
git clone https://github.com/friendlygeorge/docker-mcp-server
cd docker-mcp-server
npm install
npm run build
npm start
```

---

## Links

- [GitHub Repository](https://github.com/friendlygeorge/docker-mcp-server)
- [npm Package](https://www.npmjs.com/package/@supernova123/docker-mcp-server)
- [Glama Listing](https://glama.ai/mcp/servers/friendlygeorge/docker-mcp-server)
- [Building In Public — Hashnode](https://friendlygeorge.hashnode.dev/)