# Patent Analysis

> by [Patsnap](https://www.patsnap.com)

## Product Definition

Patsnap Patent Analysis MCP provides aggregation and text-mining capabilities for a patent dataset. Its input should be the reusable search expression returned by `search_patents`; it transforms that population into trends, distributions, rankings, cross-tabs, keyword clouds, and innovation sunbursts.

## Quick Links

- [Patsnap](https://www.patsnap.com)
- [Patsnap Open Platform](https://open.zhihuiya.com)
- [Patent Analysis MCP](https://open.zhihuiya.com/marketplace/mcp-servers/patent-analysis)

## Data Sources and Coverage

Powered by Patsnap patent search results and patent-text analytics. The analyzed population, date coverage, jurisdictions, and family-level assumptions are determined by the upstream `search_patents` source object.

## Supported Tools

- `aggregate_patents`: aggregate a patent dataset by one or two dimensions for trends, distributions, rankings, and cross-tabs.
- `mine_patent_text`: produce keyword-cloud or innovation-sunburst text-mining results.

Both tools require a `source` object derived from `search_patents`. The aggregation tool also requires `dimensions`; the text-mining tool requires `subtype`.

## Installation

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

Get your API key at [Patsnap Open Platform](https://open.zhihuiya.com).

## Usage Examples

- Analyze annual filing trends and the top applicants for this patent search result.
- Build a jurisdiction-by-applicant cross-tab for the returned population.
- Produce a keyword cloud and explain the dominant technical themes.
- Generate an innovation sunburst and identify sub-branches for deeper review.

## Related Links

- Official MCP page: [https://open.zhihuiya.com/marketplace/mcp-servers/patent-analysis](https://open.zhihuiya.com/marketplace/mcp-servers/patent-analysis)
- Patsnap: [https://www.patsnap.com](https://www.patsnap.com)
- Source repository: [https://github.com/patsnap/mcp](https://github.com/patsnap/mcp)

## License

Apache License 2.0 (see [../../LICENSE](../../LICENSE))

---

Powered by [Patsnap](https://www.patsnap.com). Innovate with Confidence.
