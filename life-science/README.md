# 🧬 PatSnap Pharma Intelligence MCP

> **The most comprehensive pharmaceutical intelligence layer for AI agents.**
> Connect your agent to 200M+ patents, clinical trials, drug pipelines, biomedical literature, and real-world evidence — all through a single MCP endpoint.

---

## What is This?

This is the official **Model Context Protocol (MCP) server** for PatSnap's **Pharma Intelligence** platform. It gives AI agents direct, structured access to PatSnap's proprietary life sciences database — enabling agents to reason over real pharmaceutical data rather than relying on static training knowledge.

Built for researchers, drug developers, competitive intelligence teams, and anyone who needs a **professionally-trained AI agent** that can navigate the complexity of modern biomedical R&D.

---

## 🚀 Quick Connect

Add the following snippet to your MCP configuration file (e.g., Claude Desktop, Cursor, or any MCP-compatible agent):

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

> **Need an API Key?** Get your free credits at [open.patsnap.com](https://open.patsnap.com)

---

## 🛠️ Tools Reference (28 Tools, v1.0.0)

All 28 tools are organized into 6 functional categories:

### 🔬 Entity Intelligence
> Normalize and resolve biomedical entities before any downstream query.

| Tool | Description | Endpoint |
| :--- | :--- | :--- |
| `ls_ner_nor_normalize` | Identify and normalize targets, drugs, diseases, companies, MoA, action types, patent numbers, and clinical trial IDs from free text. Runs NER-NOR and LLM extraction in parallel. | `/api/ls/ner-nor/normalize` |

---

### 💊 Drug & Deal Intelligence
> Track drug assets, pipelines, and business development activity.

| Tool | Description | Endpoint |
| :--- | :--- | :--- |
| `ls_drug_search` | Search drug assets by name, target, disease, MoA, phase, or company. | `/api/ls/drug/search` |
| `ls_drug_fetch` | Batch fetch full drug records by drug IDs or names. | `/api/ls/drug/fetch` |
| `ls_drug_deal_search` | Search licensing, collaboration, acquisition, and option deals. Ideal for BD queries like "Phase 2 KRAS deals involving Novartis". | `/api/ls/drug_deal/search` |
| `ls_drug_deal_fetch` | Batch fetch full drug deal records by deal IDs. | `/api/ls/drug_deal/fetch` |

---

### 🏥 Clinical Trials
> Access registered trial data and published results.

| Tool | Description | Endpoint |
| :--- | :--- | :--- |
| `ls_clinical_trial_search` | Search registered clinical trials by drug, target, disease, sponsor, phase, or geography. | `/api/ls/clinical_trial/search` |
| `ls_clinical_trial_fetch` | Batch fetch full trial records by trial IDs or registration numbers. | `/api/ls/clinical_trial/fetch` |
| `ls_clinical_trial_vector_search` | Semantic vector search across clinical trial content. | `/api/ls/clinical_trial/vector_search` |
| `ls_clinical_trial_result_search` | Search published clinical trial results and outcomes. | `/api/ls/clinical_trial_result/search` |
| `ls_clinical_trial_result_fetch` | Batch fetch full clinical trial result records by IDs. | `/api/ls/clinical_trial_result/fetch` |

---

### 📄 Scientific Literature & Translational Medicine
> Retrieve academic evidence and bridge bench-to-bedside insights.

| Tool | Description | Endpoint |
| :--- | :--- | :--- |
| `ls_paper_search` | Search academic papers by drug, target, disease, organization, journal, author, or year. Effective for queries like "recent Nature Medicine papers on KRAS inhibitors". | `/api/ls/paper/search` |
| `ls_paper_fetch` | Batch fetch full paper records by paper IDs. | `/api/ls/paper/fetch` |
| `ls_paper_vector_search` | Semantic vector search across academic paper content. | `/api/ls/paper/vector_search` |
| `ls_translational_medicine_search` | Search translational medicine records by drug, target, disease, sponsor, journal, or translation stage. | `/api/ls/translational_medicine/search` |
| `ls_translational_medicine_fetch` | Batch fetch full translational medicine records by IDs. | `/api/ls/translational_medicine/fetch` |

---

### ⚖️ Patents & Regulatory
> Investigate IP landscapes and FDA-approved drug labels.

| Tool | Description | Endpoint |
| :--- | :--- | :--- |
| `ls_patent_fetch` | Batch fetch full patent records by patent IDs or patent numbers. | `/api/ls/patent/fetch` |
| `ls_fda_label_vector_search` | Semantic vector search across FDA drug labels. Ideal for regulatory intelligence and label comparison. | `/api/ls/fda_label/vector_search` |

---

### 🌍 Market, Epidemiology & Financial Intelligence
> Understand disease burden, market dynamics, and corporate financials.

| Tool | Description | Endpoint |
| :--- | :--- | :--- |
| `ls_disease_fetch` | Batch fetch full disease records by disease IDs or names. | `/api/ls/disease/fetch` |
| `ls_epidemiology_vector_search` | Semantic vector search across epidemiology data. | `/api/ls/epidemiology/vector_search` |
| `ls_financial_report_vector_search` | Semantic vector search across corporate financial reports. Useful for revenue, pipeline, and investment analysis. | `/api/ls/financial_report/vector_search` |
| `ls_heor_vector_search` | Semantic vector search across Health Economics and Outcomes Research (HEOR) data. | `/api/ls/heor/vector_search` |
| `ls_organization_fetch` | Batch fetch full organization records by IDs or names. | `/api/ls/organization/fetch` |

---

### 📰 News & Real-Time Intelligence
> Stay current with the latest pharma industry developments.

| Tool | Description | Endpoint |
| :--- | :--- | :--- |
| `ls_news_fetch` | Batch fetch full news records by news IDs. | `/api/ls/news/fetch` |
| `ls_news_vector_search` | Semantic vector search across global pharma news. Returns the most relevant content chunks for natural-language queries. | `/api/ls/news/vector_search` |

---

## 💡 Example Use Cases

**Drug Discovery Research**
> "What are the latest EGFR inhibitors in Phase 2 trials for non-small cell lung cancer?"
→ Agent uses `ls_ner_nor_normalize` → `ls_clinical_trial_search` → `ls_drug_fetch`

**Competitive Intelligence**
> "What licensing deals has AstraZeneca signed for oncology assets in the past 2 years?"
→ Agent uses `ls_drug_deal_search` → `ls_organization_fetch`

**Scientific Evidence Review**
> "Find recent Nature Medicine papers on KRAS G12C inhibitors and their resistance mechanisms."
→ Agent uses `ls_paper_search` → `ls_paper_fetch`

**IP Landscape Analysis**
> "Retrieve patent records for semaglutide and identify key assignees."
→ Agent uses `ls_patent_fetch`

---

## 🔗 Resources

- **Developer Portal**: [open.patsnap.com](https://open.patsnap.com)
- **MCP Server Listing**: [open.patsnap.com/marketplace/mcp-servers](https://open.patsnap.com/marketplace/mcp-servers)
- **API Documentation**: [open.patsnap.com/developers](https://open.patsnap.com/devportal)
- **PatSnap Life Sciences**: [patsnap.com/solutions/life-sciences](https://www.patsnap.com/solutions/life-sciences/)
- **GitHub (Skills)**: [github.com/patsnap/skills](https://github.com/patsnap/skills)
- **Contact**: [open.patsnap.com/contact](https://open.patsnap.com/contact)

---

*Powered by [PatSnap](https://www.patsnap.com) — Innovate with Confidence.*
