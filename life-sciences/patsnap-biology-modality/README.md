# 🧬 PatSnap Biology Modality MCP

PatSnap Biology Modality provides AI agents with direct, structured access to a vast corpus of biological entity data. It deeply integrates molecular properties, binding affinities, dose-response relationships, and molecular pre-training insights, empowering researchers to accelerate drug discovery and biological understanding. Built on PatSnap's comprehensive life sciences platform, it connects you to over 200M+ patents, sequences, and bioactivity records.

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

- **MCP Server Details**: https://open.patsnap.com/marketplace/mcp-servers/a96c9b0b-2831-4d18-a37d-286896979b8d
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

- **PatSnap Life Sciences**: [eureka.patsnap.com/ls-landing](https://eureka.patsnap.com/ls-landing)
- **MCP Server Listing**: [open.patsnap.com/marketplace/mcp-servers](https://open.patsnap.com/marketplace/mcp-servers)
- **API Documentation**: [open.patsnap.com/devportal](https://open.patsnap.com/devportal)

---
*Powered by [PatSnap](https://www.patsnap.com) — Innovate with Confidence.*
