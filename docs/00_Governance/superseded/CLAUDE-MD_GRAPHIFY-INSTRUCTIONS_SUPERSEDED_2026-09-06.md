# Superseded — root `CLAUDE.md` (Graphify agent instructions)

```text
Document status:       Superseded
Lifecycle:             Execution
Authority:             Supporting
Phase:                 All phases (not phase-specific)
Implementation status: Not confirmed
Validation status:     Not confirmed
Gate effect:           Does not approve a phase transition
Date:                  2026-09-06
```

**Controlling replacement:** `AGENTS.md` at the repository root, imported by the live `CLAUDE.md`,
whose entire content is now `@AGENTS.md`.

**What this preserves:** the complete original content of the root `CLAUDE.md` as committed on
2026-08-07 (commit `c79f97c`, "chore: configure Graphify and MCP integration"), reproduced verbatim
below and unchanged.

**Why it was superseded:** the owner-approved agent-instructions change (branch
`work/agent-instructions`, 2026-09-06) replaced tool-specific Graphify instructions with the
repository operating instructions in `AGENTS.md`. The Graphify artifacts the original text
depends on — `graphify-out/` and `.claude/skills/` — are excluded from this repository by
`.gitignore`, and Graphify's status is documented separately in
`docs/05_Automation/Graphify-Code-Intelligence.md`.

**Supersession procedure** (`docs/00_Governance/DOCUMENT_LIFECYCLE.md`):

1. Preserve a copy of the superseded document — **this file.**
2. State the controlling replacement inside the superseded copy — **stated above.**
3. Record the supersession in the conflict register — **this repository has no conflict
   register.** Absence recorded here. Owner Decision Required.
4. Update the document register — **this repository has no document register.** Absence recorded
   here. Owner Decision Required.

The related nested file `.claude/CLAUDE.md` is superseded in place: it is retained, not deleted,
and carries its own supersession statement.

---

## Original content (verbatim, as committed 2026-08-07)

## graphify

This project has a knowledge graph at graphify-out/ with god nodes, community structure, and cross-file relationships.

Rules:
- For codebase questions, first run `graphify query "<question>"` when graphify-out/graph.json exists. Use `graphify path "<A>" "<B>"` for relationships and `graphify explain "<concept>"` for focused concepts. These return a scoped subgraph, usually much smaller than GRAPH_REPORT.md or raw grep output.
- If graphify-out/wiki/index.md exists, use it for broad navigation instead of raw source browsing.
- Read graphify-out/GRAPH_REPORT.md only for broad architecture review or when query/path/explain do not surface enough context.
- After modifying code, run `graphify update .` to keep the graph current (AST-only, no API cost).
