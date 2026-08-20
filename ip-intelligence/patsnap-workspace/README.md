# Workspace Patent Collection Reader

> by [Patsnap](https://www.patsnap.com)

## Product Definition

Patsnap Workspace MCP provides read access to patent collections already stored in workspaces available to the authenticated user. It can list spaces, folders, and fields; read patents from a folder; and retrieve AI-label or custom-field annotations and optional comments.

## Quick Links

- [Patsnap](https://www.patsnap.com)
- [Patsnap Open Platform](https://open.zhihuiya.com)
- [Workspace MCP](https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-workspace)

## Data Sources and Coverage

Coverage is limited to Patsnap workspaces and folders accessible to the authenticated account. The service is read-oriented and does not edit workspace structures, patent collections, labels, fields, or comments.

## Supported Tools

- `list_workspace_spaces`: list accessible self, shared, public, or all workspaces.
- `list_workspace_folders`: list folders in a selected workspace.
- `list_workspace_fields`: list standard, custom, and special fields.
- `get_workspace_patents`: read patents from a selected folder with keyword and offset/limit pagination.
- `get_workspace_annotations`: read AI-label/custom-field values and optional comments.

`get_workspace_patents` does not currently support filters, sorting, range conditions, custom-field filtering, or AI-label filtering. `get_workspace_annotations` accepts at most 200 patent IDs or publication numbers in one request.

## Installation

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

Get your API key at [Patsnap Open Platform](https://open.zhihuiya.com).

## Usage Examples

- List shared workspaces whose names contain “battery”.
- Show folders in a workspace and read the first 50 patents from one folder.
- List the custom fields and AI-label fields available in a workspace.
- Retrieve annotations and comments for selected publication numbers.

## Related Links

- Official MCP page: [https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-workspace](https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-workspace)
- Patsnap: [https://www.patsnap.com](https://www.patsnap.com)
- Source repository: [https://github.com/patsnap/mcp](https://github.com/patsnap/mcp)

## License

Apache License 2.0 (see [../../LICENSE](../../LICENSE))

---

Powered by [Patsnap](https://www.patsnap.com). Innovate with Confidence.
