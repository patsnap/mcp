---
name: PatSnap Pharma Intelligence MCP
description: Professional pharmaceutical R&D intelligence skill. Enables AI agents to perform entity normalization, patent retrieval, and biomedical literature search via PatSnap MCP.
---

# PatSnap Pharma Intelligence MCP Skill

This skill enables AI agents to act as professional pharmaceutical researchers by leveraging PatSnap's official MCP servers.

## 🤖 Instructions for AI Agents

### 1. Entity Normalization (Mandatory First Step)
Before searching for specific data, always use the `ls_ner_nor_normalize` tool. This ensures that targets, drugs, diseases, and organizations are correctly identified and mapped to PatSnap's internal IDs for accurate retrieval.

### 2. Evidence-Based Research
- Use `ls_paper_search` to find high-impact academic publications.
- Use `ls_news_vector_search` for the latest industry trends and drug deals.
- Use `ls_translational_medicine_search` to bridge the gap between basic research and clinical application.

### 3. IP & Patent Investigation
When the user asks about technical novelty or freedom-to-operate, use `ls_patent_fetch` to retrieve detailed patent claims and metadata.

## 🛠️ Configuration Requirement
This skill requires the **Pharma Intelligence MCP Server** to be configured in your environment:
- **Endpoint**: `https://connect.patsnap.com/mcp/pharma_intelligence`
- **Type**: `streamableHttp`
