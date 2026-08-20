# Patsnap MCP Documentation Templates

Use these templates as structural guides. Replace every placeholder with facts verified on the exact Marketplace detail page, and remove sections that genuinely do not apply.

## Server README

````markdown
# <Product Name>

> by [Patsnap](https://www.patsnap.com)

## Product Definition

<What the MCP does, its intended input, and its output. State important exclusions.>

## Quick Links

- [Patsnap](https://www.patsnap.com)
- [Patsnap Open Platform](https://open.zhihuiya.com)
- [<Product Name> MCP](<exact Marketplace detail URL>)

## Data Sources and Coverage

<Authoritative data source, scope, dependency, and coverage caveats.>

## Supported Tools

- `<tool_name>`: <purpose and important prerequisite>.

<Summarize cross-tool constraints, required source objects, or workflow ordering.>

## Installation

```json
{
  "mcpServers": {
    "<configuration_key>": {
      "url": "<exact endpoint>?apikey=YOUR_API_KEY",
      "type": "streamableHttp"
    }
  }
}
```

Get your API key at [Patsnap Open Platform](https://open.zhihuiya.com).

## Usage Examples

- <Supported user request>.

## Related Links

- Official MCP page: [<exact URL>](<exact URL>)
- Patsnap: [https://www.patsnap.com](https://www.patsnap.com)
- Source repository: [https://github.com/patsnap/mcp](https://github.com/patsnap/mcp)

## License

Apache License 2.0 (see [../../LICENSE](../../LICENSE))

---

Powered by [Patsnap](https://www.patsnap.com). Innovate with Confidence.
````

## Service SKILL

The service skill follows the repository's existing catalog convention. Its top-level `homepage` field is intentional for this repository's service packages.

````markdown
---
name: <server-directory>
description: <What the MCP does and concrete situations that should trigger its use.>
homepage: <exact Marketplace detail URL>
metadata:
  author: Patsnap
  category: "<IP Intelligence|Life Sciences|RD Innovation>"
  version: <Marketplace version>
  requires:
    mcp_endpoint: "<exact endpoint>?apikey=YOUR_API_KEY"
---

## Setup
Get your API key at https://open.zhihuiya.com

# <Product Name>

This skill connects your AI agent to **Patsnap's <Product Name> MCP server**.

## Prerequisites

```json
{
  "mcpServers": {
    "<configuration_key>": {
      "url": "<exact endpoint>?apikey=YOUR_API_KEY",
      "type": "streamableHttp"
    }
  }
}
```

For the full tool schema, refer to:
<exact Marketplace detail URL>

---

## Instructions for AI Agents

### <Decision or workflow rule>

<State correct tool choice, ordering, and upstream dependencies.>

### <Input and constraint rule>

<State required parameters, enums, defaults, limits, and invalid combinations.>

### <Result interpretation rule>

<State how to treat empty, partial, estimated, or asynchronous results.>

## Example Workflows

- <Supported workflow>.

## Resources

- **MCP Server**: [<Product Name>](<exact Marketplace detail URL>)
- **Patsnap Open Platform**: [open.zhihuiya.com](https://open.zhihuiya.com)
- Patsnap: [https://www.patsnap.com](https://www.patsnap.com)
````

## Index checklist

1. Add one row to the root README under the correct domain.
2. Add the same service to the matching category README.
3. Add `patsnap/mcp/<category>/<server-directory>` to root `glama.json`.
4. Preserve grouping and alphabetical ordering.
5. Confirm every indexed directory contains both `README.md` and `SKILL.md`.
