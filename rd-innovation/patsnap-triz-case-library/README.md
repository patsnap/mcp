# TRIZ Case Library

> by [Patsnap](https://www.patsnap.com)

## Product Definition

Patsnap TRIZ Case Library MCP is a cross-domain innovation-case search service. It searches more than 45 million structured patent cases by technical contradiction, SVOP function, technical efficacy, scientific effect, keyword, and patent filters, returning case summaries, innovation points, and TRIZ annotations.

## Quick Links

- [Patsnap](https://www.patsnap.com)
- [Patsnap Open Platform](https://open.zhihuiya.com)
- [TRIZ Case Library MCP](https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-triz-case-library)

## Data Sources and Coverage

Powered by Patsnap's structured patent and TRIZ annotation data, covering technical contradictions, invention principles, SVOP relations, technical efficacies, scientific effects, IPC/CPC classifications, applicants, jurisdictions, and legal status.

## Supported Tools

- `search_triz_case`: search TRIZ cases and return summaries and annotation data.
- `list_triz_search_terms`: list standard values accepted by the `efficacy` and `oxford_effects` search fields.

`search_triz_case` supports up to five keywords, a result limit from 1 to 200, relevance/publication-date/value sorting, and optional authority, legal-status, applicant, IPC/CPC inclusion, and IPC/CPC exclusion filters.

## Installation

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

Get your API key at [Patsnap Open Platform](https://open.zhihuiya.com).

## Usage Examples

- Find cross-domain cases that improve heat dissipation without increasing enclosure volume.
- Search for SVOP cases where a coating prevents a substrate from absorbing moisture.
- Find scientific effects and patent cases for passive particle separation.
- Exclude the current IPC/CPC field to discover analogous mechanisms in other industries.

## Related Links

- Official MCP page: [https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-triz-case-library](https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-triz-case-library)
- Patsnap: [https://www.patsnap.com](https://www.patsnap.com)
- Source repository: [https://github.com/patsnap/mcp](https://github.com/patsnap/mcp)

## License

Apache License 2.0 (see [../../LICENSE](../../LICENSE))

---

Powered by [Patsnap](https://www.patsnap.com). Innovate with Confidence.
