# Customer Support Orchestration

**Status: Documented** — architecture selected. **No customers, no support function, no
ticket system.**

Last updated: 2026-08-07

---

> KagePoint Systems is not currently delivering managed services. Support delivery sits in
> later roadmap phases that are **not approved**. This is design, not description.

## Support as a first-class workload

Support is not an afterthought bolted onto an orchestrator. It is one of the primary workloads
the architecture is designed around.

## Target flow

```text
Customer
    |
    v
Phone / Portal / Email / Chat / Help Desk
    |
    v
Ticket System                      <- authoritative support record
    |
    v
Summoner
    |
    +--> identify customer
    +--> identify service
    +--> identify support entitlement
    +--> load approved customer context   (minimum necessary)
    +--> check monitoring
    +--> check documentation
    +--> check known incidents
    +--> dispatch specialist agents
    +--> collect evidence
    +--> determine likely cause
    +--> prepare recommended remediation
    |
    v
Ticket update / engineer summary
    |
    +--> known approved low-risk remediation  -> future autonomous path
    |
    +--> engineering or high-impact work      -> human approval
```

The **entitlement check** sits early and deliberately: what the contract covers determines what
may be done, before any investigation begins.

## Systems of record

| System | Authoritative for |
|---|---|
| **Ticketing** | The support record — requests, history, resolution, communication |
| **Orchestration and state layer** | Jobs, approvals, workflow state, evidence references, audit |
| **Summoner** | Investigation, correlation, delegation, exception management |
| **Workflow engine** | Approved deterministic execution |
| **Monitoring** | Technical health evidence |
| **Documentation** | Approved configuration and operating knowledge |
| **Secrets manager** | Credential authority |

> **Summoner must not become the ticket database.**

If it did: support would stop when Summoner stopped, the record would not be auditable or
transferable, it would not survive a restart, and a customer dispute could not be resolved from
evidence. Each of those is individually disqualifying.

## Parallel investigation

```text
Customer reports a backup failure.

Summoner dispatches, in parallel:

  Backup Specialist        -> backup platform evidence
  Monitoring Specialist    -> monitoring history
  Documentation Specialist -> approved configuration
  Vendor Specialist        -> vendor incident status

Summoner correlates -> one engineer summary
```

**The engineer receives one consolidated answer instead of manually correlating every system.**

That is the actual value on offer: not replacing engineering judgement, but removing the twenty
minutes of tab-switching that precedes it.

Every specialist is task-scoped and single-customer, and none may cross a boundary.

## Engineer summary standard

Every investigation produces:

```text
Ticket ID · Customer · Affected service · Severity
Observed condition
Evidence reviewed
Likely cause
Confidence
Recommended action
Alternative causes
Automatic remediation status
Required approval
Assigned engineer
Started at · Estimated completion · Next update
Evidence references
```

### The separation that makes it useful

Four categories, never blurred:

| Category | Meaning |
|---|---|
| **Confirmed evidence** | Directly observed, with a retrievable reference |
| **Inference** | Reasoning from evidence — labelled as such |
| **Recommendation** | Proposed action, not taken |
| **Unknown** | Could not be determined — stated, never omitted |

A confident wrong cause is worse than no summary at all: it sends an engineer down the wrong
path faster than they would have gone unaided. So `Confidence: insufficient` is a valid and
correct output, and `Alternative causes` is mandatory below high confidence.

## Separate service domains stay separate

A game-server community support queue and a managed-services customer queue are **different
domains** with different intake, context, and identities.

Customer data and internal infrastructure context are never mixed into a community support
context, and community context never enters customer support.

## Current status

| Item | State |
|---|---|
| Customers | **None** |
| Ticket system | **Not selected** — no vendor committed |
| Support function | **Does not exist** |
| Investigations performed | **0** |
| Engineer summaries produced | **0** |
