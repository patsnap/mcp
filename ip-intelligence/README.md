# Patsnap IP Intelligence MCP Servers

MCP servers for patent search, analysis, workspace collections, legal status, valuation, FTO, internal patent data integration, landscape analytics, mining, and briefing workflows, powered by Patsnap's proprietary IP intelligence databases.

## About Patsnap

Patsnap is a global innovation intelligence platform covering 200M+ patents across 170+ jurisdictions (USPTO, EPO, WIPO and more), 216M+ scientific papers, pharma records, clinical trials, and RD data.

To explore Patsnap patent data interactively, try [Eureka](https://eureka.patsnap.com), Patsnap's AI-native RD assistant. To access patent data programmatically, use the MCP servers or REST API via [Patsnap Open Platform](https://open.patsnap.com).

## Available MCP Servers

| Server | Description | Open Platform |
| :--- | :--- | :--- |
| **Advanced Patent Search** | Semantic, similarity, image, nested-query, and keyword-assist patent search | [Advanced Patent Search](https://open.patsnap.com/marketplace/mcp-servers/1f837249-fce5-4ae3-96b5-1d9038ec41d5) |
| **Deep Patent Mining** | Technical topic, problem-solution-effect, classification, and patent text mining | [Deep Patent Mining](https://open.patsnap.com/marketplace/mcp-servers/d1f84e46-f494-4927-aba8-94eeaef94c55) |
| **Global Core Patent Database** | Global core patent records, full text, drawings, legal status, licensing, and bibliographic data | [Global Core Patent Database](https://open.patsnap.com/marketplace/mcp-servers/8dc7ef1d-d900-4c6d-bec6-2a9c03e7456b) |
| **IP & Innovation Courses** | IP and innovation courses, course details, and training resources | [IP & Innovation Courses](https://open.patsnap.com/marketplace/mcp-servers/172edf47-eae9-4f01-b8c0-e6018aab79bf) |
| **Patsnap Patent Research** | Novelty search, invention FTO analysis, and image-based design FTO analysis | [Patsnap Patent Research](https://open.patsnap.com/marketplace/mcp-servers/patsnap-ip-searching) |
| **Maintain Payment** | Patent maintenance payment and FTO-related workflows | [Maintain Payment](https://open.patsnap.com/marketplace/mcp-servers/aae364b6-a111-4e17-a99f-d7b74539cfa3) |
| **Patent Analysis** | Patent trends, distributions, rankings, cross-tabs, keyword clouds, and innovation sunbursts | [Patent Analysis](https://open.zhihuiya.com/marketplace/mcp-servers/patent-analysis) |
| **Patent Briefing** | Patent and patent family quick-read briefings | [Patent Briefing](https://open.patsnap.com/marketplace/mcp-servers/e54e3afc-df5c-47e9-878f-1e7bb38a7275) |
| **Patent Landscape Analytics** | Patent landscape analysis across filing trends, technologies, applicants, regions, and value signals | [Patent Landscape Analytics](https://open.patsnap.com/marketplace/mcp-servers/6dd83771-70f2-46ce-b4aa-6fdf60ace3f8) |
| **Patent Legal Status & Annuity** | Legal status, annuity status, and core legal document workflows | [Patent Legal Status & Annuity](https://open.patsnap.com/marketplace/mcp-servers/cba8ca99-fcc3-4cb6-8afd-baf393151692) |
| **Patent Monetization & Valuation** | Patent transaction, licensing, monetization, and valuation workflows | [Patent Monetization & Valuation](https://open.patsnap.com/marketplace/mcp-servers/1c20be56-30a5-4917-b5dd-f88986fbe9f8) |
| **Patent Valuation Scorecard** | Patent value scoring across technology, legal, market, strategy, and commercialization dimensions | [Patent Valuation Scorecard](https://open.patsnap.com/marketplace/mcp-servers/ff5b188b-48c5-49ce-aaa7-0b1294a89d55) |
| **Patent Visual Analytics** | Patent charting, trends, value, litigation, citation, and technical-effect analytics | [Patent Visual Analytics](https://open.patsnap.com/marketplace/mcp-servers/29ec8427-6e8a-4125-a246-10af19b24001) |
| **Internal Patent Data Connector** | Enterprise patent data connector for internal systems, applications, and automated workflows | [Internal Patent Data Connector](https://open.patsnap.com/marketplace/mcp-servers/91e1eddf-d691-4eb7-bd36-7d76e4d1d3f9) |
| **Workspace Patent Collection Reader** | Accessible workspace, folder, patent, field, annotation, and comment retrieval | [Workspace](https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-workspace) |

## Quick Start

### 1. Get your API key

Register at [Patsnap Open Platform](https://open.patsnap.com) to get your free API key.

### 2. Add to your MCP client

Add the following to your MCP configuration (Claude Desktop, Cursor, Windsurf, etc.):

```json
{
  "mcpServers": {
    "patsnap_advanced_patent_search": {
      "url": "https://connect.patsnap.com/33072f/mcp?apikey=YOUR_API_KEY",
      "type": "streamableHttp"
    }
  }
}
```

Replace `YOUR_API_KEY` with your key from Patsnap Open Platform.

Each MCP server has its own URL. See the individual README or Open Platform page for the exact endpoint.

## Resources

- [Patsnap](https://www.patsnap.com)
- [Patsnap Open Platform](https://open.patsnap.com)
- [Eureka](https://eureka.patsnap.com)
- [Patsnap MCP Server Source](https://github.com/patsnap/mcp)

## License

Apache License 2.0 (see [../LICENSE](../LICENSE))

---

Powered by [Patsnap](https://www.patsnap.com). Innovate with Confidence.
