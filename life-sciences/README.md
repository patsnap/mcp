# PatSnap Life Sciences MCP Servers 
> by [PatSnap Life Sciences](https://eureka.patsnap.com/ls-landing)

Official Model Context Protocol (MCP) servers for Life Sciences, powered by PatSnap's proprietary biomedical and pharmaceutical intelligence platform. These servers give AI agents direct, structured access to the world's most comprehensive pharmaceutical and biomedical database — covering drugs, targets, diseases, clinical trials, patents, scientific literature, biological sequences, chemical structures, and real‑world evidence.

## Available MCP Servers

| Server | Focus | Tools | Quick Link |
|---|---|---|---|
| **Pharma Intelligence** | Drugs, targets, diseases, clinical trials, patents, papers, deals, FDA labels, epidemiology, HEOR, financial reports, news, translational medicine | 28 | [Pharma Intelligence](https://open.patsnap.com/marketplace/mcp-servers/245f3ce8-79e4-4c2a-927c-e155c293f097) Or [Repo](https://github.com/patsnap/mcp/tree/main/life-sciences/patsnap-pharma-intelligence) |
| **Biology Modality** | Biological sequences, modifications, antibody‑antigen interactions | 5 | [Biology Modality](https://open.patsnap.com/marketplace/mcp-servers/a96c9b0b-2831-4d18-a37d-286896979b8d) Or [Repo](https://github.com/patsnap/mcp/tree/main/life-sciences/patsnap-biology-modality) |
| **Chemical Molecular** | Compound structure search, fragment analysis, ADMET prediction | 3 | [Chemical Molecular](https://open.patsnap.com/marketplace/mcp-servers/96b4a650-d563-4fc5-860d-c99ee8cb5b1e) Or [Repo](https://github.com/patsnap/mcp/tree/main/life-sciences/patsnap-chemical-molecular) |

## Setup

All three servers follow the same three‑step pattern. You can connect one or all of them depending on your use case.

### 1. Get an API Key
Log in to the [PatSnap Developer Platform](https://open.patsnap.com), go to **API Keys**, and create a new key (format: `sk-xxxxxxxxxxxx`).

### 2. Connect the MCP Servers
Run the following commands in your terminal (requires [Claude Code](https://claude.ai) or any MCP‑compatible client):

```bash
# Pharma Intelligence
claude mcp add --transport http pharma_intelligence \
  "https://connect.patsnap.com/096456/Logic-mcp?apiKey=$PATSNAP_API_KEY"

# Biology Modality
claude mcp add --transport http biology_modality \
  "https://connect.patsnap.com/06e741/Logic-mcp?apiKey=$PATSNAP_API_KEY"

# Chemical Molecular
claude mcp add --transport http chemical_molecular \
  "https://connect.patsnap.com/713886/Logic-mcp?apiKey=$PATSNAP_API_KEY"
```

Set your API key as an environment variable:
```bash
export PATSNAP_API_KEY=sk-your-key-here
```

> **Other clients?** Visit the individual server pages on [PatSnap Marketplace](https://open.patsnap.com/marketplace/mcp-servers) and select your agent (Cursor, API, etc.) from the bottom‑right corner to get the appropriate configuration snippet.

### 3. Verify
In Claude Code, type `/mcp` and confirm that the added servers show **Connected**.

## PatSnap Skills Integration

These MCP servers power [PatSnap Skills](https://github.com/patsnap/skills/tree/main/life-sciences) — domain‑specific AI agents purpose‑built for common life sciences workflows. Install them directly into your AI agent for turnkey analysis capabilities.

| Skill | Description | Requires |
|---|---|---|
| **target-intelligence** | Comprehensive target evaluation including tractability, competitive landscape, and biology evidence | Pharma Intelligence, Biology Modality |
| **pharmaceuticals-exploration** | Drug candidate assessment covering structure‑activity, chemical properties, and development progress | Pharma Intelligence, Chemical Molecular |
| **biomarker-investigation** | Biomarker discovery, validation, and clinical utility analysis across disease areas | Pharma Intelligence |
| **disease-investigation** | Disease landscape characterization including epidemiology, pipeline, and standard of care | Pharma Intelligence |
| **company-profiling** | In‑depth company analysis covering pipeline, portfolio, partnerships, and patent strategy | Pharma Intelligence |
| **precision-oncology** | Precision medicine insights for oncology including targeted therapies and biomarker‑matched trials | Pharma Intelligence |

To install all skills:
```bash
npx skills add https://github.com/patsnap/skills/tree/main/life-sciences --all
```

## Resources

- [PatSnap Developer Portal](https://open.patsnap.com) — manage API keys and explore available services
- [PatSnap MCP Marketplace](https://open.patsnap.com/marketplace/mcp-servers) — full list of available MCP servers
- [PatSnap Life Sciences](https://eureka.patsnap.com/ls-landing) — learn more about PatSnap's life sciences platform
- [PatSnap Skills Library](https://github.com/patsnap/skills) — installable domain‑specific AI agent skills
- [PatSnap MCP Server Source](https://github.com/patsnap/mcp) — source code for all MCP servers

## License

MIT

---

Powered by [PatSnap](https://www.patsnap.com) — Innovate with Confidence.
