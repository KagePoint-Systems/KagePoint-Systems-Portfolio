# Summoner — Global Orchestration Baseline

**Status: Documented** — architecture baseline selected. **Not implemented, not validated.**

Last updated: 2026-08-07

---

## What Summoner is

Summoner is the planned **global AI engineer and orchestration broker** for KagePoint Systems.

The design intent: one component maintains awareness across authorized projects and systems,
and brokers work across those boundaries under policy — while everything *below* it stays
tightly scoped.

> Summoner may maintain awareness across all authorized projects, customers, systems, agents,
> and workflows and may cross those boundaries under policy. Subordinate agents, workers,
> service identities, and project contexts remain isolated. Human users receive authority
> according to verified identity and role. Summoner delegates work into the owning environment,
> observes progress, gathers evidence, manages exceptions, and reports results back to the
> requester.

## The rule that matters more

> **Summoner must never be required for the business to function.**
>
> Every client-impacting capability requires a human-operable fallback, an authoritative system
> of record, documented access, and a recovery path.

Shorthand: **AI-first speed without AI-only dependency.**

These two rules are a matched pair, and the second is the one that will be under pressure when
the first starts working well. An orchestrator that becomes genuinely useful becomes genuinely
load-bearing, and that is precisely when nobody wants to spend time maintaining the manual path.

Writing the continuity requirement *before* building the capability is the only point at which
it can be set honestly.

## Current status — stated plainly

| Item | State |
|---|---|
| Architecture | **Selected baseline**, recorded 2026-08-07 |
| Implementation | **None. Nothing is built.** |
| Validation | **None** |
| External actions | **Approval required** |
| Autonomy | **None. Not production validated** |
| Evidence captured | **0 of 15** |
| Customers | **None** |
| Phase effect | **Does not approve any phase** |

There is no Summoner. This is a design, recorded before implementation so that the constraints
are fixed while they are still cheap to fix.

## Trust hierarchy

```text
TIER 0 — AUTHORIZED HUMANS
  Authority by verified identity, role, project, customer, risk, and approved policy
        |
        v
TIER 1 — SUMMONER
  Global orchestration authority · cross-project awareness and routing
  job supervision · exception management · evidence coordination
        |
        v
TIER 2 — PROJECT CONTROLLERS
  One per project domain — scoped to that domain only
        |
        v
TIER 3 — SPECIALIST AGENTS
  Bounded, task-scoped, retired at completion
        |
        v
TIER 4 — EXECUTION SYSTEMS
  Workflow engines · APIs · code agents · approved adapters
```

**Only Summoner receives AI-level cross-project orchestration authority.** Everything below it
is locally scoped.

Authority **narrows** at each tier:

| Tier | Scope |
|---|---|
| 0 | Broadest — but human, accountable, identity-verified |
| 1 | Broad awareness, brokered access, **no unrestricted credentials** |
| 2 | Single project |
| 3 | Single task within a single project |
| 4 | Single action with a scoped service account |

Nothing at Tier 2 or below may widen its own scope, and nothing may modify its own authority,
credential scope, delegation depth, or stop controls.

## Component model

| Component | Responsibility |
|---|---|
| Identity Broker | Verify who is asking |
| Context Broker | Determine which domain owns the request; load minimum necessary context |
| Policy Engine | Evaluate identity, role, action, and risk |
| Service Identity Broker | Select the correct scoped identity for the target environment |
| Job Controller | Create, track, and report jobs |
| Approval Controller | Enforce approval gates |
| Evidence Manager | Collect and reference evidence, including failures |
| Exception Manager | Handle blocked, failed, and ambiguous outcomes |
| Continuity Controller | Maintain fallback readiness; degrade safely |

**None of these is built.**

## A recorded conflict, published deliberately

This baseline creates a real conflict with an existing internal stop condition, which currently
treats handling a multi-domain task in one unit of work as a hard stop.

The baseline preserves that rule's **intent** — no credential reuse across domains, no data
blending, minimum necessary context, subordinate agents still cannot cross boundaries — but
changes the **mechanism** from *split the task* to *broker the task through a supervising
identity with per-domain credentials*.

**The existing stop condition stands.** Until it is formally amended in its own controlling
document, this baseline is target architecture, not operating permission.

It is mentioned here because a governance model that only records the conflicts it has already
resolved is not doing anything difficult. This one is open, it blocks real work, and saying so
is the honest position.

## Related

- [Role-Supervised AI Operating Model](ROLE-SUPERVISED-AI-OPERATING-MODEL.md)
- [Project and Customer Isolation](PROJECT-AND-CUSTOMER-ISOLATION.md)
- [Human in the Loop and RBAC](HUMAN-IN-THE-LOOP-AND-RBAC.md)
- [Customer Support Orchestration](CUSTOMER-SUPPORT-ORCHESTRATION.md)
- [Manual Fallback and Continuity](MANUAL-FALLBACK-AND-CONTINUITY.md)
- [Autonomy Promotion Model](AUTONOMY-PROMOTION-MODEL.md)
- [Architecture Diagrams](SUMMONER-ARCHITECTURE-DIAGRAMS.md)
