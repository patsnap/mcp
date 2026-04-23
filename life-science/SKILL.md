---
name: patsnap-pharma-intelligence
description: PatSnap Pharma Intelligence MCP. Search clinical trials, drugs, patents, papers, deals, FDA labels and more via 28 specialized tools.
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
      "url": "https://connect.patsnap.com/mcp/pharma_intelligence",
      "type": "streamableHttp"
    }
  }
}
```

Get your API key at [open.patsnap.com](https://open.patsnap.com).

---

## Instructions for AI Agents

### Step 1: Always Normalize Entities First

Before executing any search or fetch operation, **always call `ls_ner_nor_normalize`** on the user's input text. This tool:
- Identifies targets, drugs, diseases, companies, mechanisms of action (MoA), action types, patent numbers, and clinical trial IDs
- Runs NER-NOR and LLM keyword extraction in parallel for maximum coverage
- Returns normalized entity IDs required by downstream tools

> **Do not skip this step.** Raw user text (e.g., "EGFR", "Keytruda", "lung cancer") must be resolved to PatSnap internal IDs for accurate retrieval.

---

### Step 2: Choose the Right Tool for the Task

#### Drug & Pipeline Research
- Use `ls_drug_search` to find drug assets by name, target, disease, phase, or company
- Use `ls_drug_fetch` to retrieve full drug profiles including MoA, indications, and development status
- Use `ls_drug_deal_search` for BD intelligence: licensing, collaboration, acquisition, or option deals

#### Clinical Trial Intelligence
- Use `ls_clinical_trial_search` for structured queries (by drug, sponsor, phase, geography)
- Use `ls_clinical_trial_vector_search` for natural-language queries about trial content
- Use `ls_clinical_trial_result_search` to find published efficacy and safety outcomes

#### Scientific Literature
- Use `ls_paper_search` for structured queries (by drug, target, journal, author, year)
- Use `ls_paper_vector_search` for complex semantic queries about research topics
- Use `ls_translational_medicine_search` to bridge basic research and clinical application

#### Patent & IP Analysis
- Use `ls_patent_fetch` to retrieve full patent records by patent ID or number
- Combine with `ls_drug_search` to map IP landscapes around specific drug assets

#### Regulatory Intelligence
- Use `ls_fda_label_vector_search` for semantic search across FDA-approved drug labels
- Ideal for label comparison, contraindication analysis, and regulatory strategy

#### Market & Epidemiology
- Use `ls_epidemiology_vector_search` for disease burden and patient population data
- Use `ls_financial_report_vector_search` for corporate pipeline and revenue analysis
- Use `ls_heor_vector_search` for health economics and outcomes research

#### Real-Time News
- Use `ls_news_vector_search` for the latest industry developments, approvals, and trial readouts
- Use `ls_news_fetch` to retrieve full articles by news ID

---

### Step 3: Fetch Full Records When Needed

Search tools return summary results with IDs. When the user needs complete details, always follow up with the corresponding `_fetch` tool:

| Search Tool | Fetch Tool |
| :--- | :--- |
| `ls_drug_search` | `ls_drug_fetch` |
| `ls_clinical_trial_search` | `ls_clinical_trial_fetch` |
| `ls_paper_search` | `ls_paper_fetch` |
| `ls_drug_deal_search` | `ls_drug_deal_fetch` |
| `ls_translational_medicine_search` | `ls_translational_medicine_fetch` |
| `ls_clinical_trial_result_search` | `ls_clinical_trial_result_fetch` |

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
- **API Docs**: [open.patsnap.com/developers](https://open.patsnap.com/developers)
- **PatSnap Life Sciences**: [patsnap.com/solutions/life-sciences](https://www.patsnap.com/solutions/life-sciences/)
