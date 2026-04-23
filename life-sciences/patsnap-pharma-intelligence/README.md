# 🧬 PatSnap Pharma Intelligence MCP

> **The most comprehensive pharmaceutical intelligence layer for AI agents.**
> Connect your agent to 200M+ patents, clinical trials, drug pipelines, biomedical literature, and real-world evidence — all through a single MCP endpoint.

---

## What is This?

This is the official **Model Context Protocol (MCP) server** for PatSnap's **Pharma Intelligence** platform. It gives AI agents direct, structured access to PatSnap's proprietary life sciences database — enabling agents to reason over real pharmaceutical data rather than relying on static training knowledge.

Built for researchers, drug developers, competitive intelligence teams, and anyone who needs a **professionally-trained AI agent** that can navigate the complexity of modern biomedical R&D.

---

## 🚀 Quick Connect

Connect URL:
```
https://connect.patsnap.com/096456/logic-mcp?apikey=YOUR_API_KEY
```

Add the following snippet to your MCP configuration file (e.g., Claude Desktop, Cursor, or any MCP-compatible agent):

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

> **Need an API Key?** Get your free credits at [open.patsnap.com](https://open.patsnap.com)

---

## 🛠️ Tools & API Reference

This MCP server provides **28 specialized tools** covering clinical trials, drug pipelines, biomedical literature, patents, deals, FDA labels, epidemiology, HEOR, financial reports, and pharma news.

For the full list of tools, input parameters, and API specifications, please refer to the official documentation:

- **MCP Server Details**: [open.patsnap.com/marketplace/mcp-servers/245f3ce8-79e4-4c2a-927c-e155c293f097](https://open.patsnap.com/marketplace/mcp-servers/245f3ce8-79e4-4c2a-927c-e155c293f097)
- **API Documentation**: [open.patsnap.com/developers](https://open.patsnap.com/developers)

---

## 💡 Example Use Cases

**Drug Discovery Research**
> "What are the latest EGFR inhibitors in Phase 2 trials for non-small cell lung cancer?"

**Competitive Intelligence**
> "What licensing deals has AstraZeneca signed for oncology assets in the past 2 years?"

**Scientific Evidence Review**
> "Find recent Nature Medicine papers on KRAS G12C inhibitors and their resistance mechanisms."

**IP Landscape Analysis**
> "Retrieve patent records for semaglutide and identify key assignees."

---

## 🔗 Resources

- **Developer Portal**: [open.patsnap.com](https://open.patsnap.com)
- **MCP Server Listing**: [open.patsnap.com/marketplace/mcp-servers](https://open.patsnap.com/marketplace/mcp-servers)
- **API Documentation**: [open.patsnap.com/devportal](https://open.patsnap.com/devportal)
- **PatSnap Life Sciences**: [patsnap.com/solutions/life-sciences](https://www.patsnap.com/solutions/life-sciences/)
- **GitHub (Skills)**: [github.com/patsnap/skills](https://github.com/patsnap/skills)
- **Contact**: [open.patsnap.com/contact](https://open.patsnap.com/contact)

---

*Powered by [PatSnap](https://www.patsnap.com) — Innovate with Confidence.*
