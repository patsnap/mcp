# 🧬 PatSnap Biology Modality MCP

> **The definitive biology sequence and modality intelligence layer for AI agents.**
> Connect your agent to 1B+ biological sequences, including proteins, nucleotides, antibodies, and multi-omics data.

---

## What is This?

This is the official **Model Context Protocol (MCP) server** for PatSnap's **Biology Modality**. It provides AI agents with the specialized tools needed to analyze biological modalities, search for sequence similarities, and investigate the biological IP landscape (sequences in patents).

Designed for biologists, antibody engineers, and bioinformatics researchers who need an AI agent that can handle the complexity of large molecules and sequences.

---

## 🚀 Quick Connect

Connect URL:

```
https://connect.patsnap.com/06e741/logic-mcp?apikey=YOUR_API_KEY
```

Add the following snippet to your MCP configuration file (e.g., Claude Desktop, Cursor, or any MCP-compatible agent):

```json
{
  "mcpServers": {
    "biology_modality": {
      "url": "https://connect.patsnap.com/06e741/logic-mcp?apikey=YOUR_API_KEY",
      "type": "streamableHttp"
    }
  }
}
```

> **Need an API Key?** Get your free credits at [open.patsnap.com](https://open.patsnap.com)

---

## 🛠️ Tools & API Reference

This MCP server provides tools for biological sequence search (BLAST-like), antibody-antigen interaction discovery, post-translational modification profiling, and multi-omics data retrieval.

For the full list of tools, input parameters, and API specifications, please refer to the official documentation:

- **MCP Server Details**: [open.patsnap.com/marketplace/mcp-servers/96b4a650-d563-4fc5-860d-c99ee8cb5b1e](https://open.patsnap.com/marketplace/mcp-servers/96b4a650-d563-4fc5-860d-c99ee8cb5b1e)
- **API Documentation**: [open.patsnap.com/developers](https://open.patsnap.com/developers)

---

## 💡 Example Use Cases

**Sequence Similarity Search**
> "Find all patents that disclose a protein sequence with at least 90% identity to this FASTA sequence."

**Antibody Engineering**
> "Retrieve known antibody-antigen interactions for the HER2 target and identify the CDR regions mentioned in patents."

**Multi-omics Data Retrieval**
> "Search for gene expression profiles associated with this specific nucleotide sequence in recent clinical papers."

---

## 🔗 Resources

- **Developer Portal**: [open.patsnap.com](https://open.patsnap.com)
- **PatSnap Life Sciences**: [patsnap.com/solutions/life-sciences](https://www.patsnap.com/solutions/life-sciences/)
- **GitHub (Skills)**: [github.com/patsnap/skills](https://github.com/patsnap/skills)

---

[![mcp MCP server](https://glama.ai/mcp/servers/patsnap/mcp/badges/card.svg)](https://glama.ai/mcp/servers/patsnap/mcp)

[![mcp MCP server](https://glama.ai/mcp/servers/patsnap/mcp/badges/score.svg)](https://glama.ai/mcp/servers/patsnap/mcp)

---
*Powered by [PatSnap](https://www.patsnap.com) — Innovate with Confidence.*
