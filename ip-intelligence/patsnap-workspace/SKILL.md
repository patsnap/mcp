---
name: patsnap-workspace
description: Patsnap Workspace MCP for AI agents. Browses accessible workspaces and folders, lists fields, reads patents in a folder, and retrieves AI-label or custom-field annotations and comments. Use for existing workspace patent collections, not global patent discovery.
homepage: https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-workspace
metadata:
  author: Patsnap
  category: "IP Intelligence"
  version: 1.0.0
  requires:
    mcp_endpoint: "https://connect.zhihuiya.com/48a232/logic-mcp?apikey=YOUR_API_KEY"
---

## Setup
Get your API key at https://open.zhihuiya.com

# Workspace Patent Collection Reader

This skill connects your AI agent to **Patsnap's Workspace MCP server**.

## Prerequisites

```json
{
  "mcpServers": {
    "patsnap_workspace": {
      "url": "https://connect.zhihuiya.com/48a232/logic-mcp?apikey=YOUR_API_KEY",
      "type": "streamableHttp"
    }
  }
}
```

For the full tool schema, refer to:
https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-workspace

---

## Instructions for AI Agents

### Follow the identifier chain

1. Call `list_workspace_spaces`, optionally filtering `type` by `all`, `self`, `shared`, or `public`, or using `search_name`.
2. Use the returned `space_id` with `list_workspace_folders`; optionally search folder names.
3. Call `list_workspace_fields(space_id)` when fields, AI labels, custom fields, or annotations are involved.
4. Call `get_workspace_patents(space_id, folder_id, ...)` for folder patents.
5. Call `get_workspace_annotations(space_id, folder_id, ...)` for AI-label/custom-field values and optional comments.

Never guess `space_id`, `folder_id`, or `field_ids`. When multiple names match, present candidates before reading a large collection.

### Respect tool limits

`get_workspace_patents` supports `keyword`, `limit`, and zero-based `offset`. It does not support filters, sorting, ranges, custom-field filters, or AI-label filters. If you post-filter a manageable returned set, label that as local processing rather than a server-side query.

`get_workspace_annotations` accepts optional `patent_ids` or publication numbers, with a maximum of 200, optional `field_ids`, `include_comments`, and pagination controls. Empty `annotations` mean no stored value, not a negative classification.

### Report scope

Preserve workspace and folder names with their IDs, state whether results are complete or sampled, cite publication numbers or returned IDs, and distinguish comments from structured field values. The MCP is read-oriented; do not imply it edits workspace content.

## Example Workflows

- List shared workspaces whose names contain “battery”.
- Read the first 50 patents from a selected folder.
- List custom fields and AI-label fields in a workspace.
- Retrieve annotations and comments for selected publication numbers.

## Resources

- **MCP Server**: [Workspace](https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-workspace)
- **Patsnap Open Platform**: [open.zhihuiya.com](https://open.zhihuiya.com)
- Patsnap: [https://www.patsnap.com](https://www.patsnap.com)
