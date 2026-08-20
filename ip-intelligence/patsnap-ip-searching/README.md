# Patsnap Patent Research

> by [Patsnap](https://www.patsnap.com)

## Product Definition

Patsnap Patent Research MCP provides unified novelty searching, invention freedom-to-operate (FTO) review, and design-patent FTO review. It accepts technical descriptions, invention disclosures, claim text, or product/design images and returns staged search and analysis results such as summaries, extracted features, candidate patents, comparisons, and reports.

This MCP is intended for defined novelty and FTO workflows. Use a general patent-search MCP when the task is open-ended patent discovery or query construction rather than a novelty or infringement-risk review.

## Quick Links

- [Patsnap](https://www.patsnap.com)
- [Patsnap Open Platform](https://open.patsnap.com)
- [Patsnap Patent Research MCP](https://open.patsnap.com/marketplace/mcp-servers/patsnap-ip-searching)

## Data Sources and Coverage

Powered by Patsnap patent data and IP analysis workflows. Invention FTO supports country, application-date, legal-status, and assignee filters. Design FTO supports country, application-date, legal-status, and Locarno-classification filters. Search and analysis results are research inputs and are not legal opinions.

## Supported Tools

- `novelty_search`: search the novelty of a technical solution, invention disclosure, or claim text using text and optional images.
- `fto_review`: review invention-patent infringement risk for a product or technical implementation, using `lite` screening or `pro` analysis.
- `design_fto`: review design-patent risk from a product or design image; only the first supplied image is used.
- `get_task`: retrieve the status or detailed results of an asynchronous task.

The three analysis tools require an `input` object and support asynchronous execution. Preserve the returned `task_id` and pass it to `get_task`; use its `view` setting to choose an overview or detailed step results.

## Installation

```json
{
  "mcpServers": {
    "patsnap_patent_research": {
      "url": "https://connect.patsnap.com/f176d7/mcp?apikey=YOUR_API_KEY",
      "type": "streamableHttp"
    }
  }
}
```

Get your API key at [Patsnap Open Platform](https://open.patsnap.com).

## Usage Examples

- Run a novelty search for this invention disclosure and compare the closest candidate patents.
- Perform a lightweight US FTO screening for this product description.
- Run a full invention FTO analysis limited by application date, legal status, and assignee.
- Review design-patent risk for this product image in selected countries and Locarno classes.

## Related Links

- Official MCP page: [https://open.patsnap.com/marketplace/mcp-servers/patsnap-ip-searching](https://open.patsnap.com/marketplace/mcp-servers/patsnap-ip-searching)
- Patsnap: [https://www.patsnap.com](https://www.patsnap.com)
- Source repository: [https://github.com/patsnap/mcp](https://github.com/patsnap/mcp)

## License

Apache License 2.0 (see [../../LICENSE](../../LICENSE))

---

Powered by [Patsnap](https://www.patsnap.com). Innovate with Confidence.
