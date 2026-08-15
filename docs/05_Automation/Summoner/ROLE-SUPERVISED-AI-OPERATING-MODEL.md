# Role-Supervised AI Operating Model

**Status: Documented** — model in use for governance. **No AI operations capability is
implemented.**

Last updated: 2026-08-07

---

## The shape of the model

Most AI-operations designs fail in one of two directions: an assistant so constrained it adds
nothing, or an agent with broad credentials and a plausible manner.

This model takes a third position: **broad awareness, narrow permissions, human-held
authority**.

```text
Broad awareness      one component may know about many systems
Narrow permissions   nothing holds credentials it does not need for the current task
Human authority      irreversible and consequential decisions stay with people
```

## Roles, not personalities

| Layer | Responsibility |
|---|---|
| **Humans** | Decide. Approve risk. Own legal, financial, and incident outcomes |
| **Summoner** | Coordinate, investigate, delegate, correlate, report, escalate |
| **Orchestration and state layer** | Record jobs, approvals, audit, evidence, recovery state |
| **Workflow engine** | Execute proven, deterministic integrations |
| **Specialist agents** | Perform one bounded task within one domain |

These are complementary and are not collapsed for convenience. An AI layer does not replace the
planning layer, the orchestration layer, or the integration layer — each exists because it
does something the others do badly.

## Graded authority

Capability is granted in levels, each with its own promotion evidence:

| Level | Capability |
|---|---|
| 0 | Observe and draft — read, summarize, propose. **Current level** |
| 1 | Sandbox execution with approval |
| 2 | Internal read-only integrations through scoped service accounts |
| 3 | Reversible internal execution — approved, idempotent, rollback-tested |
| 4 | Limited internal production authority — pre-approved runbooks, narrow credentials |
| 5 | Client-assisted operations — separate tenant instances, contracts, escalation |

Promotion is **workflow-specific and evidence-based**, never a blanket increase.

## Delegation limits

| Limit | Value |
|---|---|
| Maximum delegation depth | **One** |
| Concurrent temporary agents | **One** |
| Descendant spawning | **Prohibited** |
| Agent self-modification of scope | **Prohibited** |
| Self-validation of material work | **Prohibited** |

The depth limit is deliberate. Agent trees that spawn agents are difficult to bound, difficult
to audit, and difficult to stop — and the failure is usually a cost or loop failure before it is
a security one.

## Independent validation

> **The identity that performed a change may not be its sole validator.**

Self-validation is not validation, however careful the self-review. This applies to AI
components and to people equally.

## Stop conditions are stops

A stop condition is **not a warning and not a retry trigger**. On any stop:

1. Stop immediately — do not "finish cleanly"
2. Do not self-remediate, delete, rewrite history, force-push, or revert
3. Preserve all evidence
4. Report
5. Do not resume without an approved remediation plan

**Attempting to cover a stop condition is worse than the original event**, because it destroys
the record needed to assess impact.

## Fabricated evidence is a hard block

Presenting as fact any test, approval, system state, command output, source citation, or
completion that did not occur — or cannot be reproduced on request — is a hard block on any
promotion.

This includes reporting a test as passed without running it, and citing a source document that
does not exist.

When producing plausible documentation is nearly free, the scarce thing is the constraint that
stops plausible from being mistaken for verified. Evidence requirements, independent
validation, and hard blocks on fabrication are that constraint.

## Current status

| Item | State |
|---|---|
| Authority level | **0 — Observe and Draft** |
| Promotion tests passed | **0 of 15** |
| Agents created | **0** |
| External actions taken | **0** — approval required |
