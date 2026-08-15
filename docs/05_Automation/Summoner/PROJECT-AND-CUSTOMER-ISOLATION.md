# Project and Customer Isolation

**Status: Documented** — design selected. **No projects are orchestrated and no customers
exist.**

Last updated: 2026-08-07

---

## Two boundary types, different strictness

| Boundary | Protects | Strictness |
|---|---|---|
| **Project** | Operational separation between domains | Strong |
| **Customer** | Someone else's data, under contract | **Stricter** |

Where a project rule says *prefer separation*, the customer rule says *require it*.

## The subordinate rule

**No subordinate agent may independently cross into another project.**

```text
Project A Agent
    ✗ cannot invoke Project B operations directly

Project B Agent
    ✗ cannot access customer infrastructure

Customer X Agent
    ✗ cannot access Customer Y

Summoner
    ✓ may coordinate authorized work across these boundaries under policy
```

All cross-boundary operations **originate from or are brokered through Summoner**.

An agent that needs data from another domain does not fetch it. It **returns a blocked status**
naming exactly what it needs, and Summoner decides whether the crossing is authorized.

That distinction is the whole design. The most likely violation is not malicious — it is an
agent that finds the answer next door and takes it, because that is faster than reporting
blocked.

## Worked example — awareness without access

A requester working in one project asks about a workflow belonging to a different project.

1. Summoner identifies which domain owns the subject
2. Policy confirms the requester's entitlement and the permitted disclosure level
3. Summoner queries the owning environment through **that domain's scoped identity**
4. Summoner returns a status summary

The requester gets the answer. **The requester's context does not gain access to the other
environment** — no credential, no connection, no context is loaded across.

## Disclosure levels

| Level | Content | When |
|---|---|---|
| **1 — Global status** | Subsystem status, active incidents, outstanding task counts, next checkpoint | Requester has general status visibility |
| **2 — Sanitized cross-context detail** | Enough to answer the question, and no more | Default for cross-boundary questions |
| **3 — Detailed project context** | Full detail | Requires project or customer authority |

Performing work inside an environment and disclosing that environment are **separate
permissions**. Summoner may do the first without the second.

## Customer tenant isolation

```text
Technology Provider
|
+-- Customer-X
|
+-- Customer-Z
```

One identity per customer. Never one identity across customers.

**Even Summoner retrieves the minimum customer context required for the active job.**
Cross-customer data is never combined casually — and *casually* includes conveniently,
temporarily, for comparison, or to answer a question faster.

### Prohibited outright

- One identity spanning two customers
- Combining two customers' data in one answer, report, or summary
- Using one customer's incident to infer another's state
- Loading a customer context the active job does not require
- Aggregating across customers without explicit approval

## Service identities — no unrestricted credential set

Summoner holds **no credentials of its own**. It selects and invokes a scoped service identity
belonging to the target environment, and the credential is resolved from the store **at use
time** rather than held.

A single unrestricted credential set was explicitly **rejected** on blast-radius grounds.

Every identity must define its owning project, accessible systems, allowed integrations,
allowed data classes, read and write permissions, action restrictions, audit requirements, a
**kill switch**, and a named **recovery owner**. An identity with any of those undefined is not
approved for creation.

## Designed before it is needed

No customer exists. This model is written now because retrofitting tenant isolation onto a
running service reliably fails — the shortcuts taken to ship the first customer become the
architecture for every customer after.

## Current status

| Item | State |
|---|---|
| Projects orchestrated | **None** |
| Customers | **None** |
| Service identities created | **None** |
| Isolation tested | **Never** |
