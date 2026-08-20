---
name: patsnap-triz-case-library
description: Patsnap TRIZ Case Library MCP for AI agents. Finds cross-domain patent cases by technical contradiction, SVOP function, technical efficacy, scientific effect, keyword, and patent filters. Use for evidence-backed analogies, inventive principles, effects, and prior cases that can inspire engineering solutions.
homepage: https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-triz-case-library
metadata:
  author: Patsnap
  category: "RD Innovation"
  version: 1.0.0
  requires:
    mcp_endpoint: "https://connect.zhihuiya.com/37b2d2/mcp?apikey=YOUR_API_KEY"
---

## Setup
Get your API key at https://open.zhihuiya.com

# TRIZ Case Library

This skill connects your AI agent to **Patsnap's TRIZ Case Library MCP server**, covering more than 45 million structured patent cases.

## Prerequisites

```json
{
  "mcpServers": {
    "patsnap_triz_case_library": {
      "url": "https://connect.zhihuiya.com/37b2d2/mcp?apikey=YOUR_API_KEY",
      "type": "streamableHttp"
    }
  }
}
```

For the full tool schema, refer to:
https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-triz-case-library

---

## Instructions for AI Agents

### Build searchable signals

Frame the engineering problem as a technical contradiction, SVOP function, desired efficacy, scientific effect, keywords, or a combination. Patent filters refine a search but cannot be the only search condition.

### Resolve standard terms first

Before using `efficacy` or `oxford_effects`, call `list_triz_search_terms` for that field unless the exact standard spelling is already known. Do not invent or loosely translate enumeration values.

### Search cases

Use `search_triz_case` with these semantics:

- `technical_contradiction`: improving parameter IDs 1–39, worsening parameter IDs 1–39, and invention principle IDs 1–40. Conditions in one object are ANDed against the same record; multiple objects are ORed.
- `svop`: `subject`, `verb_standard`, `object`, and `param_standard` are ANDed within an object; multiple objects are ORed.
- `efficacy` and `oxford_effects`: standard terms; when both are supplied they are ANDed within a record.
- `keyword`: at most five keywords.
- `filters`: optional `authority`, `legal_status`, `applicant`, `ipc_cpc`, and `ipc_cpc_exclude`.
- `sort`: `sdesc` relevance, `pdesc` publication date, or `vdesc` value.
- `limit`: 1–200, default 50.

For cross-domain inspiration, use `ipc_cpc_exclude` to remove the current field. Authority examples include `CN`, `US`, and `EP`. Legal-status codes are `0` invalid, `1` valid, `2` pending, `220` PCT designated invalid, `221` PCT designated valid, and `999` unknown.

### Synthesize responsibly

Explain why each returned case is analogous and cite its patent or source identifier. Distinguish the disclosed mechanism from your proposed transfer to the user's problem. Similarity is not proof of feasibility or freedom to operate.

## Example Workflows

- Find cross-domain cases that improve heat dissipation without increasing volume.
- Search SVOP cases where a coating prevents a substrate from absorbing moisture.
- Identify effects for passive particle separation and find supporting cases.
- Exclude the current IPC/CPC classes to discover analogous mechanisms.

## Resources

- **MCP Server**: [TRIZ Case Library](https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-triz-case-library)
- **Patsnap Open Platform**: [open.zhihuiya.com](https://open.zhihuiya.com)
- Patsnap: [https://www.patsnap.com](https://www.patsnap.com)
