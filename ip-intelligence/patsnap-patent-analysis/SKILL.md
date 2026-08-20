---
name: patsnap-patent-analysis
description: Patsnap Patent Analysis MCP for AI agents. Aggregates and mines a patent search result into trends, distributions, rankings, cross-tabs, keyword clouds, and innovation sunbursts. Use after a patent-search tool has returned a reusable search expression; this service analyzes rather than discovers patents.
homepage: https://open.zhihuiya.com/marketplace/mcp-servers/patent-analysis
metadata:
  author: Patsnap
  category: "IP Intelligence"
  version: 1.0.0
  requires:
    mcp_endpoint: "https://connect.zhihuiya.com/e14e5f/logic-mcp?apikey=YOUR_API_KEY"
---

## Setup
Get your API key at https://open.zhihuiya.com

# Patent Analysis

This skill connects your AI agent to **Patsnap's Patent Analysis MCP server**.

## Prerequisites

```json
{
  "mcpServers": {
    "patent_analysis": {
      "url": "https://connect.zhihuiya.com/e14e5f/logic-mcp?apikey=YOUR_API_KEY",
      "type": "streamableHttp"
    }
  }
}
```

For the full tool schema, refer to:
https://open.zhihuiya.com/marketplace/mcp-servers/patent-analysis

---

## Instructions for AI Agents

### Preserve the upstream source

Both analysis tools require a `source` object derived from the search expression returned by `search_patents`. Preserve that object for downstream analysis. If it is absent, first invoke an available patent-search MCP. Do not fabricate `source` from prose or substitute a list of patent numbers unless the live tool schema explicitly supports it.

### Choose the analysis tool

- Use `aggregate_patents` for trend, distribution, ranking, or one-/two-dimensional cross-tab analysis. It requires `source` and `dimensions`; optional inputs include `limit_per_dimension` and `sorts`.
- Use `mine_patent_text` for a keyword cloud or innovation sunburst. It requires `source` and `subtype`; `chart_limit` controls output size.

### Keep comparisons valid

Keep the same `source` across comparisons unless the user asks to change the patent population. Report the source scope, date and jurisdiction coverage, and family-deduplication assumptions with every analysis.

Counts represent records under the supplied search expression. Do not equate them directly with market share, technical quality, commercial value, or legal strength. Clearly label interpretations and recommend drill-down queries that could test them.

## Example Workflows

- Show annual filing trends and top applicants for this search result.
- Build a jurisdiction-by-applicant cross-tab.
- Produce a keyword cloud and explain the dominant themes.
- Generate an innovation sunburst and identify branches for deeper review.

## Resources

- **MCP Server**: [Patent Analysis](https://open.zhihuiya.com/marketplace/mcp-servers/patent-analysis)
- **Patsnap Open Platform**: [open.zhihuiya.com](https://open.zhihuiya.com)
- Patsnap: [https://www.patsnap.com](https://www.patsnap.com)
