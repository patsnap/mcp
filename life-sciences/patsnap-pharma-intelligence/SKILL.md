---
name: patsnap-pharma-intelligence
description: PatSnap Pharma Intelligence MCP for AI agents. Search clinical trials, drugs, patents, papers, deals, FDA labels and more via 28 specialized tools.
---

# PatSnap Pharma Intelligence

This skill connects your AI agent to **PatSnap's Pharma Intelligence MCP server** — the most comprehensive pharmaceutical data layer available for AI agents.

With this skill, your agent gains the ability to perform professional-grade pharmaceutical research: from identifying drug targets and searching clinical trials, to analyzing licensing deals and reviewing FDA labels.

## Prerequisites

This skill requires the **PatSnap Pharma Intelligence MCP server** to be configured in your environment:

```json
{
  "mcpServers": {
    "pharma_intelligence": {
      "url": "https://connect.patsnap.com/096456/logic-mcp?apikey=YOUR_API_KEY",
      "type": "streamableHttp"
    }
  }
}
```

Get your API key at [open.patsnap.com](https://open.patsnap.com).

For the full list of available tools and input parameters, refer to the official MCP server documentation:
[open.patsnap.com/marketplace/mcp-servers/245f3ce8-79e4-4c2a-927c-e155c293f097](https://open.patsnap.com/marketplace/mcp-servers/245f3ce8-79e4-4c2a-927c-e155c293f097)

---

## Instructions for AI Agents

### Step 1: Always Normalize Entities First

Before executing any search or fetch operation, **always call `ls_ner_nor_normalize`** on the user's input text. This tool identifies and normalizes targets, drugs, diseases, companies, mechanisms of action (MoA), patent numbers, and clinical trial IDs — returning the internal IDs required by all downstream tools.

> **Do not skip this step.** Raw user text must be resolved to PatSnap internal IDs for accurate retrieval.

---

### Step 2: Choose the Right Tool for the Task

This MCP provides 28 tools organized across these domains:

- **Drug & Pipeline**: search and fetch drug assets, licensing and collaboration deals
- **Clinical Trials**: structured search, semantic search, and published results
- **Scientific Literature**: paper search, vector search, and translational medicine
- **Patents & Regulatory**: patent fetch, FDA label semantic search
- **Market & Epidemiology**: disease data, HEOR, financial reports, epidemiology
- **Real-Time News**: semantic news search and full article fetch

For the complete tool list and input parameters, see:
[open.patsnap.com/marketplace/mcp-servers/245f3ce8-79e4-4c2a-927c-e155c293f097](https://open.patsnap.com/marketplace/mcp-servers/245f3ce8-79e4-4c2a-927c-e155c293f097)

---

### Step 3: Fetch Full Records When Needed

Search tools return summary results with IDs. When the user needs complete details, always follow up with the corresponding `_fetch` tool (e.g., after `ls_drug_search`, call `ls_drug_fetch` with the returned IDs).

---

### Step 4: Synthesize and Structure Your Output

After retrieving data, present findings in a structured, professional format:
- **Lead with key findings**: Summarize the most relevant results first
- **Cite sources**: Always include drug names, trial IDs, paper titles, or patent numbers
- **Highlight gaps**: If data is limited, acknowledge it and suggest alternative search strategies
- **Use tables** for comparing multiple drugs, trials, or deals side by side

---

## Example Workflows

### Biomarker Investigation
1. `ls_ner_nor_normalize` → extract target/disease entities
2. `ls_paper_search` → find supporting academic evidence
3. `ls_clinical_trial_search` → identify trials using this biomarker
4. `ls_patent_fetch` → check IP landscape

### Competitive Drug Landscape
1. `ls_ner_nor_normalize` → normalize disease/target
2. `ls_drug_search` → enumerate competing assets
3. `ls_drug_deal_search` → identify recent BD activity
4. `ls_news_vector_search` → surface latest developments

### Target Intelligence
1. `ls_ner_nor_normalize` → resolve target ID
2. `ls_drug_search` → find all drugs modulating this target
3. `ls_paper_vector_search` → retrieve mechanistic literature
4. `ls_clinical_trial_search` → map clinical development activity

---

## Resources

- **MCP Server**: [open.patsnap.com/marketplace/mcp-servers](https://open.patsnap.com/marketplace/mcp-servers/245f3ce8-79e4-4c2a-927c-e155c293f097)
- **API Docs**: [open.patsnap.com/devportal](https://open.patsnap.com/devportal)
- **PatSnap Life Sciences**: [patsnap.com/solutions/life-sciences](https://www.patsnap.com/solutions/life-sciences/)
