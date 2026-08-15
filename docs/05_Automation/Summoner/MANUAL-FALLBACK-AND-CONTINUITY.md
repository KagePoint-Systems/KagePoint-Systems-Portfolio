# Manual Fallback and Continuity

**Status: Documented** — standard defined. **No fallback has ever been exercised.**

Last updated: 2026-08-07

---

## The requirement

> **Summoner must never be required for the business to function.**
>
> Every client-impacting capability requires a human-operable fallback, an authoritative system
> of record, documented access, and a recovery path.

## Normal and degraded paths

```text
Normal                          Summoner unavailable
------                          --------------------
Humans                          Humans
   |                               |
Summoner                        Ticketing / Forge / Monitoring
   |                               |
Agents / Forge / n8n            Manual SOPs / Approved Tools
```

**The path does not break. It shortens.** Humans reach the systems of record directly.

## What must continue during an outage

| Capability | Why it continues |
|---|---|
| Tickets | The ticket system is the authoritative support record, not Summoner |
| Customer contact | Support intake does not route through Summoner |
| Monitoring and alerting | Runs independently and alerts humans directly |
| Backups | Run on their own schedule, independent of orchestration |
| Validated workflows | Deterministic; execute without Summoner |
| Engineer system access | Direct and approved; Summoner is not a gateway |
| Documentation | Held in its own systems |
| Job state | Retained by the orchestration and state layer |
| Manual procedures | Written to be executed by a human without AI assistance |

Only two things degrade: investigation correlation, and proposed remediation. Both degrade to
what an engineer would have done unaided.

## The prohibition

> **No critical customer service may depend solely on Summoner's conversational memory.**

Conversational memory is not a system of record. It is not durable, not auditable, not
transferable to another person, and not recoverable after a restart.

## Design consequences

| Consequence | Detail |
|---|---|
| Summoner is not a gateway | It never becomes the only path to a system |
| Summoner is not a database | It never becomes the only place a fact is stored |
| Summoner is not a credential holder | Identities are brokered and resolved at use time |
| Every automation has a documented human fallback | Written **before** the automation is approved |
| Degradation is announced, not absorbed | Reduced capability is stated explicitly |

That last row prevents the worst failure mode: a partially working orchestrator that keeps
answering confidently from stale context while the systems behind it are unreachable. A
component that is plainly down is safer than one that is quietly wrong.

## Fallback documentation standard

Each client-impacting automation documents: the normal automated handler · a **named human**
fallback owner · a manual procedure executable **without AI assistance** · the required human
access · the system of record · the evidence location · a safe stop condition · recovery
prerequisites · a resumption procedure · an escalation route.

The operational template and completed fallback records are held internally.

### The access trap

*Required human access* is the field most likely to be filled optimistically and the one most
likely to fail in practice. If the fallback owner's access has never been tested, the fallback
has never been tested. An owner who discovers during an outage that their entitlement expired is
not a fallback.

## Recovery: unknown stays unknown

After a restart, Summoner reconstructs state from authoritative systems — never from
recollection.

> **Missing state is never invented. Unknown state is reported as unknown.**

A restarted orchestrator has a strong pull toward plausible reconstruction: filling a gap with
what was probably true. That is especially dangerous after a restart, because the gap is
invisible to the person reading the answer.

| Situation | Correct behaviour |
|---|---|
| A source is unreachable | Report it as unreachable; do not infer its contents |
| A job's status is undeterminable | Report unknown; do not assume it completed |
| An approval state is ambiguous | Treat as **not approved** |
| Evidence is missing | Report missing; do not reconstruct what it likely said |

## A fallback that has never been exercised is an assumption

Same principle as an untested backup.

| Check | Status |
|---|---|
| Fallbacks documented per automation | **Standard defined — no automation exists** |
| Fallback owners named | **None assigned** |
| Fallback access verified | **Never** |
| Fallback exercised | **Never** |
| Outage continuity tested | **Never** |
| State reconstruction tested | **Never** |

Publishing a table this empty is deliberate. Claiming tested continuity without evidence would
fail the standard this page describes.
