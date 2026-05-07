---
name: patsnap-biological-modality
description: Biological sequence and modality intelligence via PatSnap MCP.
homepage: https://open.patsnap.com/marketplace/mcp-servers/a96c9b0b-2831-4d18-a37d-286896979b8d
metadata:
  patsnap:
    category: "Biology"
    requires:
      env: ["PATSNAP_API_KEY"]
      mcp_endpoint: "https://connect.patsnap.com/06e741/logic-mcp?apikey=YOUR_API_KEY"
    setup_guide: "Get your API Key at https://open.patsnap.com"
---

# PatSnap Biology Modality

This skill connects your AI agent to **PatSnap's Biology Modality MCP server** — providing professional-grade biological sequence and modality analysis capabilities.

With this skill, your agent can navigate the world of large molecules, from sequence-based patent searching to antibody-antigen interaction discovery and multi-omics data retrieval.

## Prerequisites

This skill requires the **PatSnap Biology Modality MCP server** to be configured in your environment:

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

Get your API key at [open.patsnap.com](https://open.patsnap.com).

For the full list of available tools and input parameters, refer to the official MCP server documentation:
[open.patsnap.com/marketplace/mcp-servers/96b4a650-d563-4fc5-860d-c99ee8cb5b1e](https://open.patsnap.com/marketplace/mcp-servers/96b4a650-d563-4fc5-860d-c99ee8cb5b1e)

---

## Instructions for AI Agents

### Step 1: Sequence Identification & Normalization
When a user provides a protein or nucleotide sequence (FASTA format) or a gene name, use the biological normalization tools to resolve the entity to a standard ID or sequence.

### Step 2: Sequence-Based Search
- Use **Sequence Identity Search** to find homologs in patents and literature.
- Use **Motif Search** to identify specific functional regions within a sequence.
- Filter results by organism, sequence length, and patent publication date.

### Step 3: Modality-Specific Analysis
- For **Antibodies**: Analyze CDR regions and antigen binding affinity.
- For **Nucleotides**: Investigate gene expression and multi-omics associations.

### Step 4: Output Synthesis
Present biological data with:
- **Sequence alignments** showing identity and gaps.
- **Functional annotations** (e.g., active sites, PTMs).
- **IP landscape summaries** for specific sequences.

---

## Example Workflows

### Antibody IP Clearance
1. Input an antibody heavy/light chain sequence.
2. Run sequence identity search across global patent databases.
3. Identify patents with high-identity sequences that may pose FTO risks.

### Target Discovery Support
1. Input a gene or protein name.
2. Retrieve associated multi-omics data and expression profiles.
3. Search for similar sequences in literature to identify potential functional homologs.

---

## Resources

- **PatSnap Life Sciences**: [eureka.patsnap.com/ls-landing](https://eureka.patsnap.com/ls-landing)
- **MCP Server**: [open.patsnap.com/marketplace/mcp-servers](https://open.patsnap.com/marketplace/mcp-servers/96b4a650-d563-4fc5-860d-c99ee8cb5b1e)
- **API Docs**: [open.patsnap.com/developers](https://open.patsnap.com/developers)
