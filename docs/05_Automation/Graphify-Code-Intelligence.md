# Graphify — Code and Document Knowledge Graphs

**Status: Documented** — see the verification note below for what actually ran.

Last updated: 2026-08-07

---

## What it is

[Graphify](https://github.com/rustyrazorblade/graphify) builds a knowledge graph over a
repository — files, documents, symbols, and the relationships between them — and exposes it to
an AI assistant through a local MCP (Model Context Protocol) server.

The value for a documentation-heavy project is structural: it answers questions like *which
governance documents reference each other*, *where does this decision get cited*, and *which
documents overlap or duplicate* — questions that are tedious to answer by reading, and easy to
answer wrong from memory.

## Why it fits this project

KagePoint Systems documentation has a deliberate authority structure: controlling documents,
project-control documents, execution drafts, historical material, and superseded material, with
explicit cross-references between them.

That structure is only useful if it is **navigable and consistent**. Graphify supports:

- Mapping which documents reference which
- Finding governance documents that overlap or duplicate
- Tracing cross-reference dependencies before a document is changed
- Spotting orphaned documents nothing links to
- Identifying where a superseded document is still cited as current

## How it is used here

| Property | Value |
|---|---|
| Scope | **Project-local** — one graph per repository |
| Transport | **stdio** (local process) |
| Network exposure | **None.** No HTTP server, no internet-accessible endpoint |
| Output | Local generated artifacts, **not committed** |
| Authority | **Analysis aid only** |

### Not exposed publicly

Graphify runs entirely locally over stdio. No Graphify HTTP service is configured, and no
Graphify endpoint is internet-accessible. Generated graph artifacts are git-ignored in both
repositories so repository structure and document relationships are not published as a
byproduct.

### Not a source of authority

This one matters more than the tooling detail:

> **Graphify is an analysis aid, not governance authority.**

Source documents are never modified on the strength of graph output alone. A graph can show
that two documents overlap; it cannot decide which one controls. That decision follows the
authority order and, where contested, the owner.

The same principle applies to every AI-assisted tool in this project: it informs a decision, it
does not make one.

## Verification note — stated accurately

| Step | Result |
|---|---|
| Graphify installed | ✅ **Yes** — v0.9.35 |
| Project-local integration | ✅ **Yes** — both repositories |
| Graph generated | ❌ **No** |
| MCP server registered | ❌ **No** — nothing to serve without a graph |
| Verification queries run | ❌ **No** |

**Installation and project-local integration completed. Graph generation did not.**

Both repositories are documentation-only — 0 code files against 46 documents in this one. The
local, no-credential extraction path indexes code via AST parsing, so on a documentation corpus
it produces an empty graph. Building a useful graph here needs **semantic document
extraction**, which requires a billed LLM API key.

No such key was provisioned, for two reasons that are themselves part of the governance model:
credential provisioning is an owner action, not an automated one; and adding a billed provider
is a spend decision against a defined ceiling.

So the honest status is **Documented, not Implemented** — the tooling is installed and
configured, the design above is the intended configuration, and the graph itself does not exist.

There is a mildly interesting failure here worth recording: the extraction backend named
`claude` requires an `ANTHROPIC_API_KEY` and does **not** use an authenticated Claude Code CLI
subscription, even when that CLI is installed and working. Those are different access paths to
the same model family, and assuming otherwise wastes time.

### One thing worth flagging for anyone doing the same

`graphify install --project` writes a `.claude/settings.json` containing a **hardcoded absolute
executable path** including the local username. That file is git-ignored here rather than
committed — it is not portable across machines, and publishing workstation path structure in a
public repository is free disclosure with no upside. Anyone cloning re-runs the install command
locally instead.

Internal detail is held in the operations repository's Graphify setup report.

## Related

- [AI Governance](AI-Governance/README.md) — authority model for AI-assisted tooling
- [Validation](../04_Security/Validation/README.md) — the evidence model behind status labels
