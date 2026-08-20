---
name: patsnap-ip-searching
description: Patsnap Patent Research MCP for AI agents. Performs novelty searches, invention freedom-to-operate reviews, and design-patent FTO reviews from technical text, claims, disclosures, or product images. Use for defined novelty and infringement-risk research workflows, including asynchronous task retrieval; do not use it as a substitute for legal advice.
homepage: https://open.patsnap.com/marketplace/mcp-servers/patsnap-ip-searching
metadata:
  author: Patsnap
  category: "IP Intelligence"
  version: 0.1.0
  requires:
    mcp_endpoint: "https://connect.patsnap.com/f176d7/mcp?apikey=YOUR_API_KEY"
---

## Setup
Get your API key at https://open.patsnap.com

# Patsnap Patent Research

This skill connects your AI agent to **Patsnap's Patent Research MCP server**.

## Prerequisites

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

For the full tool schema, refer to:
https://open.patsnap.com/marketplace/mcp-servers/patsnap-ip-searching

---

## Instructions for AI Agents

### Choose the correct workflow

- Use `novelty_search` for a technical solution, invention disclosure, or claim-text novelty review. Text is the primary input; images are optional supplements. Optional search channels include semantic, Boolean, paper, and web search.
- Use `fto_review` for invention-patent infringement-risk research based on a product or technical implementation. The required `input` object uses text as its primary content and can include translated text and images.
- Use `design_fto` for design-patent risk research. Its required `input` object must contain at least one image; only the first item in `input.images` is used, and a title is optional.
- Use a general patent-search MCP instead when the user needs open-ended discovery, query construction, or retrieval without a novelty or FTO analysis workflow.

### Configure search and filters carefully

For `fto_review`, `search.mode` supports `lite` for rapid screening and `pro` for full analysis. Its search settings can also control candidate-patent count and iterative search rounds. Optional filters support `country`, `apd`, `legal_status`, and `assignee`; application-date ranges use `YYYYMMDD`, and assignee filters support `not_in`.

For `design_fto`, optional filters support `country`, `apd`, `legal_status`, and `loc`; `loc` uses Locarno classifications and application-date ranges use `YYYYMMDD`.

The analysis tools also accept optional execution settings for asynchronous execution or real-time progress, optional output controls such as normalized result-row limits, and an optional caller-supplied `task_id`.

### Retrieve asynchronous results

When a tool runs asynchronously, preserve its returned `task_id` and call `get_task`. The `task_id` is required. Use `view: overview` for the status summary; this is the default. Use `view: detail` when step and result details are needed. Do not start duplicate analyses merely because a task is still running.

### Interpret results responsibly

Preserve the user's technical scope, countries, date window, legal-status assumptions, and other filters in the report. Distinguish retrieved patents and service-generated comparisons from your own interpretation. Novelty and FTO outputs support research and triage; they do not establish patent validity, non-infringement, or a legal opinion. Recommend qualified patent counsel for decisions carrying legal or commercial risk.

## Example Workflows

- Search the novelty of an invention disclosure and compare its extracted features with candidate patents.
- Run a `lite` FTO screening, then use `pro` analysis for the highest-risk implementation.
- Restrict an invention FTO review by country, application date, legal status, and excluded assignees.
- Review a single product image for design-patent risk in specified Locarno classes.

## Resources

- **MCP Server**: [Patsnap Patent Research](https://open.patsnap.com/marketplace/mcp-servers/patsnap-ip-searching)
- **Patsnap Open Platform**: [open.patsnap.com](https://open.patsnap.com)
- Patsnap: [https://www.patsnap.com](https://www.patsnap.com)
