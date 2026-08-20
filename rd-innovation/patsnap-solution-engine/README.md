# TRIZ Concept Solution Engine

> by [Patsnap](https://www.patsnap.com)

## Product Definition

Patsnap TRIZ Concept Solution Engine MCP is a Model Context Protocol server for engineering innovation and product cost reduction. It routes a task into either a TRIZ innovation workflow or a TRIZ/DFMA cost-reduction workflow, runs the analysis asynchronously, returns candidate concepts, and provides detailed content for a selected solution.

A complete concept-generation task normally takes about 5–10 minutes. Actual time varies with task complexity, input completeness, and service load.

## Quick Links

- [Patsnap](https://www.patsnap.com)
- [Patsnap Open Platform](https://open.zhihuiya.com)
- [TRIZ Concept Solution Engine MCP](https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-solution-engine)

## Data Sources and Coverage

Powered by Patsnap's TRIZ analysis, cross-domain innovation-case matching, product function analysis, cost analysis, trimming, and DFMA capabilities.

## Supported Tools

- `run_triz_innovation_task`: create an asynchronous TRIZ innovation task.
- `fetch_triz_innovation_task_stream`: retrieve progress and candidate innovation concepts.
- `fetch_triz_innovation_solution_detail`: retrieve the detailed content of a selected innovation concept.
- `run_triz_reduction_task`: create an asynchronous TRIZ/DFMA cost-reduction task.
- `fetch_triz_reduction_task_stream`: retrieve progress, cost analysis, trimming analysis, DFMA output, and candidate cost-reduction concepts.
- `fetch_triz_reduction_solution_detail`: retrieve the detailed content of a selected cost-reduction concept.

## Installation

```json
{
  "mcpServers": {
    "patsnap_solution_engine": {
      "url": "https://connect.zhihuiya.com/c18800/mcp?apikey=YOUR_API_KEY",
      "type": "streamableHttp"
    }
  }
}
```

Get your API key at [Patsnap Open Platform](https://open.zhihuiya.com).

## Usage Examples

- Generate TRIZ concepts to prevent a battery enclosure seal from leaking during thermal cycling.
- Reduce the manufacturing cost of a pump assembly without lowering flow rate, lifetime, or safety margin.
- Track an existing TRIZ task and compare the candidate concepts.
- Expand a selected candidate into a detailed concept and validation plan.

## Related Links

- Official MCP page: [https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-solution-engine](https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-solution-engine)
- Patsnap: [https://www.patsnap.com](https://www.patsnap.com)
- Source repository: [https://github.com/patsnap/mcp](https://github.com/patsnap/mcp)

## License

Apache License 2.0 (see [../../LICENSE](../../LICENSE))

---

Powered by [Patsnap](https://www.patsnap.com). Innovate with Confidence.
