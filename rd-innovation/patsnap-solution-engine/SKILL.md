---
name: patsnap-solution-engine
description: Patsnap TRIZ Concept Solution Engine MCP for AI agents. Generates innovation or product cost-reduction concepts through asynchronous TRIZ and TRIZ/DFMA workflows. Use for engineering problem solving, concept alternatives, cost-reduction analysis, task-progress retrieval, and selected-solution details.
homepage: https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-solution-engine
metadata:
  author: Patsnap
  category: "RD Innovation"
  version: 1.0.0
  requires:
    mcp_endpoint: "https://connect.zhihuiya.com/c18800/mcp?apikey=YOUR_API_KEY"
---

## Setup
Get your API key at https://open.zhihuiya.com

# TRIZ Concept Solution Engine

This skill connects your AI agent to **Patsnap's TRIZ Concept Solution Engine MCP server**.

## Prerequisites

```json
{
  "mcpServers": {
    "patsnap_solution_engine": {
      "url": "https://connect.zhihuiya.com/c18800/mcp?apikey=YOUR_API_KEY",
      "type": "streamableHttp"
    }
  }
}
```

For the full tool schema, refer to:
https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-solution-engine

---

## Instructions for AI Agents

### Choose one workflow

- Innovation: `run_triz_innovation_task` → `fetch_triz_innovation_task_stream` → `fetch_triz_innovation_solution_detail`.
- Cost reduction: `run_triz_reduction_task` → `fetch_triz_reduction_task_stream` → `fetch_triz_reduction_solution_detail`.

Do not mix innovation and reduction tool families for one task. Preserve the returned `job_id`; after candidates arrive, preserve the selected `idea_id`.

### Prepare the input

The start tools require `user_input`. Include the current design, desired outcome, constraints, unacceptable trade-offs, and known function or cost information. The CN endpoint accepts at most 1,000 characters; non-CN environments may allow only 500.

### Track asynchronous execution

Poll only the stream tool matching the start tool until candidates or a terminal failure are returned. A complete task normally takes 5–10 minutes and may take longer with complex or incomplete input. Intermediate selection points run automatically using the highest-priority option; do not represent them as user-approved choices.

### Evaluate and expand candidates

Compare candidate concepts using feasibility, expected impact, implementation complexity, risk, and the user's constraints. Retrieve details only after an `idea_id` is selected. Separate service output from your own assessment and state unresolved engineering assumptions.

For reduction tasks, retain returned cost analysis, trimming analysis, DFMA findings, and benefit estimates. Treat estimates as hypotheses until checked against BOM, process, quality, and supplier data.

## Example Workflows

- Generate concepts to prevent enclosure-seal leakage during thermal cycling.
- Reduce pump-assembly cost without lowering performance, lifetime, or safety.
- Track a TRIZ task and compare its candidate concepts.
- Expand a selected idea into a detailed concept and validation plan.

## Resources

- **MCP Server**: [TRIZ Concept Solution Engine](https://open.zhihuiya.com/marketplace/mcp-servers/patsnap-solution-engine)
- **Patsnap Open Platform**: [open.zhihuiya.com](https://open.zhihuiya.com)
- Patsnap: [https://www.patsnap.com](https://www.patsnap.com)
