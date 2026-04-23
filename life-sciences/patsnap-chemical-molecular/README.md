# 🧪 PatSnap Chemical Molecular MCP

> **The ultimate chemical and small molecule intelligence layer for AI agents.**
> Connect your agent to 160M+ chemical structures, synthetic routes, bioactivity data, and global chemical patents.

---

## What is This?

This is the official **Model Context Protocol (MCP) server** for PatSnap's **Chemical Molecular**.

It empowers AI agents with deep chemistry knowledge, allowing them to search for **structures**, **analyze synthetic pathways**, and investigate the **chemical IP landscape** with professional-grade accuracy.

Perfect for medicinal chemists, process engineers, and IP professionals who need an AI agent that truly "understands" chemistry.

---

## 🚀 Quick Connect

Connect URL:
```
https://connect.patsnap.com/713886/logic-mcp?apikey=YOUR_API_KEY
```

Or add the following snippet to your MCP configuration file (e.g., Claude Desktop, Cursor, or any MCP-compatible agent):

```json
{
  "mcpServers": {
    "chemical_molecular": {
      "url": "https://connect.patsnap.com/713886/logic-mcp?apikey=YOUR_API_KEY",
      "type": "streamableHttp"
    }
  }
}
```

> **Need an API Key?** Get your free credits at [open.patsnap.com](https://open.patsnap.com)

---

## 🛠️ Tools & API Reference

This MCP server provides specialized tools for chemical entity recognition, structure search (substructure/similarity), property prediction, and chemical patent analysis.

For the full list of tools, input parameters, and API specifications, please refer to the official documentation:

- **MCP Server Details**: [open.patsnap.com/marketplace/mcp-servers/a96c9b0b-2831-4d18-a37d-286896979b8d](https://open.patsnap.com/marketplace/mcp-servers/a96c9b0b-2831-4d18-a37d-286896979b8d)
- **API Documentation**: [open.patsnap.com/devportal](https://open.patsnap.com/devportal)

---

## 💡 Example Use Cases

**Structure Search**
> "Find all patents mentioning substructures similar to Imatinib published in the last 5 years."

**Synthetic Route Analysis**
> "Retrieve known synthetic routes for this SMILES string and identify potential starting materials."

**Bioactivity Investigation**
> "What is the reported IC50 of this compound against the JAK2 kinase in recent literature?"

---

## 🔗 Resources

- **Developer Portal**: [open.patsnap.com](https://open.patsnap.com)
- **PatSnap Life Sciences**: [patsnap.com/solutions/life-sciences](https://www.patsnap.com/solutions/life-sciences/)
- **GitHub (Skills)**: [github.com/patsnap/skills](https://github.com/patsnap/skills)

---

*Powered by [PatSnap](https://www.patsnap.com) — Innovate with Confidence.*
