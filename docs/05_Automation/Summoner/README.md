# Summoner — AI Operations Architecture

**Status: Documented** — owner-selected architecture baseline. **Nothing is implemented.**

Last updated: 2026-08-07

---

## Read this first

| Item | State |
|---|---|
| Architecture | **Selected baseline**, 2026-08-07 |
| Implementation | **None** |
| Validation | **None** |
| Authority level | **0 — Observe and Draft** |
| Promotion tests passed | **0 of 15** |
| External actions | **Approval required** |
| Autonomy | **None. Not production validated** |
| Customers | **None** |
| Evidence captured | **0 of 15** |

There is no Summoner. This is a design recorded before implementation, so the constraints are
fixed while they are still cheap to fix.

## The pair of rules this rests on

> **Summoner may maintain awareness across authorized projects, customers, systems, agents, and
> workflows, and may cross those boundaries under policy** — while everything below it stays
> tightly scoped.

> **Summoner must never be required for the business to function.** Every client-impacting
> capability requires a human-operable fallback, an authoritative system of record, documented
> access, and a recovery path.

Shorthand: **AI-first speed without AI-only dependency.**

The second rule is the one that will be under pressure when the first starts working well.

## Documents

| Document | Subject |
|---|---|
| [Global Orchestration Baseline](SUMMONER-GLOBAL-ORCHESTRATION-BASELINE.md) | The core rule, trust hierarchy, component model, and an open conflict |
| [Role-Supervised AI Operating Model](ROLE-SUPERVISED-AI-OPERATING-MODEL.md) | Graded authority, delegation limits, independent validation, stop conditions |
| [Project and Customer Isolation](PROJECT-AND-CUSTOMER-ISOLATION.md) | Boundaries, disclosure levels, scoped service identities |
| [Human in the Loop and RBAC](HUMAN-IN-THE-LOOP-AND-RBAC.md) | Identity-based authority, approval discipline, what stays human |
| [Customer Support Orchestration](CUSTOMER-SUPPORT-ORCHESTRATION.md) | Support flow, parallel investigation, engineer summary standard |
| [Manual Fallback and Continuity](MANUAL-FALLBACK-AND-CONTINUITY.md) | Degraded operation, fallback standard, recovery honesty |
| [Autonomy Promotion Model](AUTONOMY-PROMOTION-MODEL.md) | The twelve-requirement gate and automatic demotion |
| [Architecture Diagrams](SUMMONER-ARCHITECTURE-DIAGRAMS.md) | Conceptual diagrams |

## An open conflict, published on purpose

This baseline conflicts with an existing internal stop condition that treats handling a
multi-domain task in one unit of work as a hard stop.

The baseline keeps that rule's intent — no credential reuse across domains, no data blending,
minimum necessary context — but changes the mechanism from *split the task* to *broker the task
through a supervising identity with per-domain credentials*.

**The existing stop condition stands** until it is formally amended in its own controlling
document. Until then this is target architecture, not operating permission.

A governance model that only records the conflicts it has already resolved is not doing
anything difficult. This one is open, it blocks real work, and saying so is the honest position.

## Related

- [AI Governance](../AI-Governance/README.md)
- [KagePoint Forge](../KagePoint-Forge/README.md)
- [n8n](../n8n/README.md)
- [Validation](../../04_Security/Validation/README.md)
