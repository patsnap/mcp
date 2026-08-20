---
name: mcp-documentation-standard
description: Create or update Patsnap MCP catalog documentation in this repository. Use when adding a Marketplace MCP server, refreshing its README or service SKILL, classifying it under ip-intelligence, life-sciences, or rd-innovation, or updating the repository README and Glama indexes.
---

# MCP Documentation Standard

Use this workflow to turn a Patsnap Marketplace MCP detail page into consistent, reviewable repository documentation.

## Required outcome

For every MCP server, create or update these files in its business-domain directory:

- `<category>/<server-directory>/README.md`
- `<category>/<server-directory>/SKILL.md`

Then update all applicable indexes:

- `/README.md`
- `/<category>/README.md`
- `/glama.json`

Do not create a business-server skill under `.agents/skills`. This skill is the reusable documentation standard; each MCP's own `SKILL.md` belongs beside that MCP's `README.md`.

Read [references/templates.md](references/templates.md) before writing or reviewing MCP documentation.

## 1. Collect authoritative Marketplace facts

Open the exact MCP detail page and record:

- Marketplace slug, displayed product name, provider, lifecycle state, and version
- product purpose and stated data coverage
- endpoint URL, MCP configuration key, and transport type
- complete tool names, purposes, required and optional parameters
- enums, limits, defaults, incompatibilities, asynchronous behavior, and prerequisites

For dynamic pages, use a browser capable of reading the rendered detail and tool panels. Treat the Marketplace tool definitions as the source of truth for tool behavior. Do not infer unsupported parameters from general marketing copy or from similarly named MCPs.

## 2. Choose the destination

Map the product to one business domain:

- Patent search, patent analytics, portfolios, legal status, valuation, or workspace collections: `ip-intelligence`
- Drugs, biology, chemistry, clinical, regulatory, or life-science intelligence: `life-sciences`
- TRIZ, engineering innovation, scientific literature, concept generation, or R&D workflows: `rd-innovation`

Use a `patsnap-`-prefixed directory name. Preserve a Marketplace slug that already starts with `patsnap-`; otherwise prefix it, for example `patent-analysis` becomes `patsnap-patent-analysis`. Before creating a directory, search the repository for an existing canonical location.

## 3. Write the server README

Use the README template in the reference. Keep it useful to both humans and catalog consumers:

- define what the MCP does and what it does not do
- identify its data source or dependency on upstream tool output
- list every supported tool with a concise, accurate description
- provide a copyable configuration using the exact endpoint and key
- give realistic usage examples grounded in supported capabilities
- link to the exact Marketplace detail page and repository

Never include a real API key. Use `YOUR_API_KEY` in examples.

## 4. Write the service SKILL

The service `SKILL.md` is an agent operating guide, not a duplicate product brochure. Follow the repository's service frontmatter convention and template in the reference. Document:

- when the MCP should and should not be used
- prerequisites and exact connection configuration
- correct tool ordering and upstream dependencies
- required inputs, important defaults, enums, maximums, and unsupported combinations
- how to interpret empty, partial, asynchronous, or estimated results
- short example workflows and official resources

Do not invent tool schemas. Prefer explicit constraints that prevent invalid calls and misleading conclusions.

## 5. Update discovery indexes

Update the root README's relevant domain description and service table. Update the matching category README in the same way.

Add the server to root `glama.json` as:

`patsnap/mcp/<category>/<server-directory>`

Keep `relatedServers` grouped by category and sorted by directory name. Add narrowly relevant keywords or quality-description coverage when the new capability materially expands the catalog.

Category-level `glama.json` files currently contain only schema and maintainer metadata. Do not add a service list to them unless their schema or existing repository convention changes.

## 6. Verify before handoff

Check all of the following:

- server title, slug, endpoint, configuration key, transport, and version agree across files
- every documented tool exists on the Marketplace page
- required parameters and limits are not weakened or omitted
- every README link and every `relatedServers` path resolves to the intended local directory
- edited JSON parses successfully
- the generic documentation skill passes the official skill validator
- no unfinished placeholder, scaffold text, secret, or accidental unrelated edit remains
- `git diff --check` succeeds

Review the final diff and report exactly which MCP directories and indexes changed.
