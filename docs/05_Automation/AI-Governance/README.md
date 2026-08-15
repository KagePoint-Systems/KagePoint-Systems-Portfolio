# AI Governance

**Status: Documented** - not claimed as implemented, tested, or validated.

Last updated: 2026-08-07

---

## Scope

The authority model, boundaries, and stop conditions governing AI assistance.

## Design principles applied

- Graded authority levels from observe-and-draft upward, each with its own promotion evidence
- Promotion is workflow-specific and evidence-based, never a blanket permission increase
- **Project phase and system trust level are separate controls** - a phase advancing never raises authority
- Task-scoped authority with explicit tools, limits, evidence, rollback, and stop conditions
- Independent validation required for material changes
- Agent memory is never the source of truth
- Stop conditions are stops, not retry triggers
- Fabricated evidence is a hard block

## Public-detail note

Currently at the lowest authority level with zero promotion tests passed.

## Summoner architecture

The full AI operations architecture built on these principles is documented at
[`../Summoner/`](../Summoner/README.md): global orchestration, trust hierarchy, project and
customer isolation, scoped service identities, identity-based authority, support orchestration,
continuity requirements, and the twelve-requirement autonomy promotion gate.

**Nothing of it is implemented.**

## Maturity

Planned -> Documented -> Implemented -> Tested -> Validated

Current: **Documented**.
