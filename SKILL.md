---
name: PatSnap MCP Connector
description: Connect your AI agent to PatSnap's 200M+ patent and R&D intelligence database via Model Context Protocol.
---

# PatSnap MCP Connector

This skill enables AI agents to use PatSnap's official MCP servers for deep innovation intelligence.

## Capabilities
- **Patent Search**: Access 200M+ global patents.
- **Pharma Intelligence**: Retrieve drug R&D and clinical trial records.
- **R&D Insights**: Analyze technical literature and competitive landscapes.

## Setup Instructions
To use this MCP server, add the following to your MCP configuration (e.g., Claude Desktop or Cursor):

```json
{
  "mcpServers": {
    "patsnap": {
      "command": "npx",
      "args": ["-y", "@patsnap/mcp-server"],
      "env": {
        "PATSNAP_API_KEY": "YOUR_API_KEY_HERE"
      }
    }
  }
}
