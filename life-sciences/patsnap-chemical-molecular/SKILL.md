---
name: patsnap-chemical-molecular
description: PatSnap Chemical Molecular MCP for AI agents. Search 160M+ chemical structures, synthetic routes, and bioactivity data via specialized chemistry tools.
---

# PatSnap Chemical Molecular

This skill connects your AI agent to **PatSnap's Chemical Molecular MCP server** — providing professional-grade chemistry search and analysis capabilities.

With this skill, your agent can navigate the complex world of small molecules, from structure-based patent searching to bioactivity data retrieval and synthetic route analysis.

## Prerequisites

This skill requires the **PatSnap Chemical Intelligence MCP server** to be configured in your environment:

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

Get your API key at [open.patsnap.com](https://open.patsnap.com).

For the full list of available tools and input parameters, refer to the official MCP server documentation:
[open.patsnap.com/marketplace/mcp-servers/a96c9b0b-2831-4d18-a37d-286896979b8d](https://open.patsnap.com/marketplace/mcp-servers/a96c9b0b-2831-4d18-a37d-286896979b8d)

---

## Instructions for AI Agents

### Step 1: Chemical Entity Recognition
When a user mentions a chemical name, drug, or SMILES string, use the chemical normalization tools to resolve the entity to a standard structure or PatSnap internal ID.

### Step 2: Structure-Based Search
- Use **Substructure Search** to find molecules containing a specific scaffold.
- Use **Similarity Search** to find analogs of a lead compound.
- Combine structure search with patent filters to investigate the chemical IP landscape.

### Step 3: Bioactivity & Property Analysis
Retrieve IC50, Ki, and other bioactivity data from literature and patents to evaluate compound potency and selectivity.

### Step 4: Output Synthesis
Present chemical data with:
- **SMILES/InChI strings** for precise identification.
- **Visual descriptions** of scaffolds and functional groups.
- **Tabular comparisons** of bioactivity across different analogs.

---

## Example Workflows

### Lead Optimization Support
1. Identify lead compound structure.
2. Run similarity search to find known analogs.
3. Retrieve bioactivity data for all analogs to identify SAR (Structure-Activity Relationship) trends.

### Chemical IP Clearance
1. Input a candidate molecule structure.
2. Run substructure search across global patent databases.
3. Identify key patents that may cover the candidate scaffold.

---

## Resources

- **MCP Server**: [open.patsnap.com/marketplace/mcp-servers](https://open.patsnap.com/marketplace/mcp-servers/a96c9b0b-2831-4d18-a37d-286896979b8d)
- **API Docs**: [open.patsnap.com/devportal](https://open.patsnap.com/devportal)
- **PatSnap Life Sciences**: [patsnap.com/solutions/life-sciences](https://www.patsnap.com/solutions/life-sciences/)
