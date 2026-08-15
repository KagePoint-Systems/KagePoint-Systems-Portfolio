# Human in the Loop and RBAC

**Status: Documented** — model selected. **No identity registry exists.**

Last updated: 2026-08-07

---

## Multi-user by design

Summoner is designed for **multiple authorized human users**, not a single operator. Candidate
identity types include owner, engineers, approvers, help desk tiers, service managers, and
customer-facing personnel.

## Authority never derives from a name

> **Privileges are never hard-coded from a person's name.**

Authority derives from an identity and access policy: a **verified identity**, an **assigned
role**, and a **recorded scope**.

Name-based privilege produces a system where adding a person means editing logic, removing a
person means remembering to, and nobody can answer *"what can this person do?"* without reading
code.

## RBAC now, ABAC later

**Role-Based Access Control** is the starting model:

```text
Identity  ->  Role(s)  ->  Permissions  ->  Decision
```

**Attribute-Based Access Control** is a future refinement, evaluating requests against
attributes rather than role membership alone: identity, role, project, customer, action, risk,
location, time, contract scope, and approval level.

Moving to ABAC requires a separate approved decision. Starting with ABAC would be designing for
a complexity that does not exist yet.

## Registers

| Register | State |
|---|---|
| Human Identity Registry | **Empty** |
| Role Registry | **Empty** |
| Approval Authority Matrix | **Empty** |
| Project Access Matrix | **Empty** |
| Customer Access Matrix | **Empty** |

> **No permission is populated.** Unverified permissions are not recorded, because a permission
> written down tends to get honoured whether or not anyone approved it.

## Approval discipline

| Rule | Detail |
|---|---|
| Approval is explicit | Never inferred from silence, prior approval, or an unrelated approval |
| Approval is scoped | Covers the specific action, target, and time window |
| Approval is recorded | With identity, timestamp, and scope |
| **Ambiguity resolves to _not approved_** | Never to approved |
| Self-approval is prohibited | A requester may not approve its own request |

Proceeding past a required gate — including self-approving, inferring approval from silence, or
widening scope mid-task — is treated as a hard stop, not a process deviation.

## Read-only is not a loophole

An investigation that modifies anything is not read-only. If proceeding requires a change —
enabling a log, restarting a service to reproduce, clearing a cache — that change **requires
approval on its own merits**. It is not covered by an instruction to investigate.

## Always human-controlled

Regardless of role, evidence, or automation maturity:

Legal commitments and contracts · pricing, billing, payments, purchases, refunds · hiring,
firing, payroll · **security incident declaration and breach notification** · destructive or
irreversible changes · access-control ownership and emergency credentials · final public
statements and sensitive customer communications · promotion of governance decisions to the
source of truth · **any change to a component's own authority, credential scope, delegation
depth, or stop controls**.

An automated component may **detect, stop, report, and escalate**. It may not declare an
incident, notify externally, or decide a disclosure outcome.

That last item — self-modification of authority — is the one that makes the rest durable. A
system that can widen its own permissions has no permissions.

## Current status

| Item | State |
|---|---|
| Identities registered | **None** |
| Roles defined | **None** |
| Approval authority assigned | **None** |
| Enforcement tested | **Never** |
