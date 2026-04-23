# PatSnap MCP Servers

### **Connected Innovation Intelligence for AI Agents**
*Empowering agents with 200M+ patents, pharma records, and R&D intelligence.*

---

## 🧬 Featured: Pharma Intelligence MCP

The **Pharma Intelligence** MCP server provides structured search, semantic vector search, and entity retrieval across clinical trials, drugs, targets, diseases, patents, papers, and more.

### 🛠️ Key Tools (28 Tools Total)
- **ls_ner_nor_normalize**: Normalize entities (targets, drugs, diseases) from user queries.
- **ls_patent_fetch**: Batch fetch full detail records by patent IDs or numbers.
- **ls_paper_search**: Search academic papers (Nature, Science, etc.) by drug or target.
- **ls_news_vector_search**: Semantic search across global pharma news.
- **ls_translational_medicine_search**: Investigate translational medicine records.

## 🚀 Quick Start

To connect your AI agent (e.g., Claude Desktop, Cursor) to PatSnap Pharma Intelligence, add the following to your MCP configuration file:

    {
      "mcpServers": {
        "patsnap_pharma": {
          "url": "https://connect.patsnap.com/mcp/pharma_intelligence",
          "type": "streamableHttp"
        }
      }
    }

## 📖 Documentation & Support

- **Developer Portal**: [open.patsnap.com](https://open.patsnap.com )
- **API Keys**: [Get your API Key here](https://open.patsnap.com/marketplace/mcp-servers/245f3ce8-79e4-4c2a-927c-e155c293f097 )
- **Official Website**: [patsnap.com](https://www.patsnap.com )

---
© 2026 PatSnap. All rights reserved.
