# Autonomy Promotion Model

**Status: Documented** — model defined. **No capability is autonomous. Nothing has entered this
flow.**

Last updated: 2026-08-07

---

## Current position

> **External actions require approval. No capability is autonomous. Autonomy is not production
> validated.**

## Autonomy is capability-specific

Promotion is **never** a blanket permission increase.

*"Summoner is trusted now"* is not a state this model can reach. *"This specific remediation,
for this specific failure, in this specific environment, is approved for autonomous
execution"* is.

A capability earns autonomy individually, on its own evidence, and loses it individually.

## The twelve-requirement gate

A known remediation may become autonomous **only after all twelve**:

| # | Requirement |
|---|---|
| 1 | **Repeatable success** — demonstrated repeatedly, not once |
| 2 | **Defined risk** — risk class assessed and recorded |
| 3 | **Approved playbook** — the exact procedure, written and approved |
| 4 | **Customer authorization** where a customer environment is touched |
| 5 | **Tested rollback** — exercised, not merely designed |
| 6 | **Monitoring** — the action and its effect are observable |
| 7 | **Audit evidence** — complete records of each execution |
| 8 | **Kill switch** — immediate disable, with a named human who can operate it |
| 9 | **Rate limits** — bounded execution frequency |
| 10 | **Cost limits** — bounded spend |
| 11 | **Error threshold** — automatic suspension on repeated failure |
| 12 | **Recorded promotion decision** — dated, by an authorized human |

**All twelve are mandatory.** A capability meeting eleven is not promoted.

## Independent of project phase

> **Project phase and system trust level are separate controls.**
>
> A phase advancing does **not** grant any component more authority.

These are frequently conflated, and conflating them is how autonomy arrives by accident: the
project reaches a milestone, and the automation is quietly assumed to have earned something.
It has not. Trust is earned per capability, on evidence, and never by calendar or milestone.

## Automatic demotion

A promoted capability is **suspended automatically** on: error threshold breach · rate limit
breach · cost limit breach · any stop condition · any unexplained outcome.

Restoration requires investigation, remediation, and a **fresh promotion decision** — not a
reset. An unexplained outcome counts even when it was benign; "it worked but we don't know why"
is a suspension condition.

## Target future capability

```text
02:13 — approved service fails
02:14 — monitoring creates incident
02:14 — Summoner classifies known failure
02:15 — approved remediation executes
02:16 — service returns
02:18 — validation succeeds
02:18 — ticket/evidence record updated
07:00 — morning brief reports self-healed incident
```

> ### This is a future validated capability.
> **It is not operational. No such remediation exists, has been approved, or has run.**

The 07:00 line is part of the design, not decoration: an autonomous action nobody reviews is not
supervised autonomy, it is just an unobserved change.

## Never autonomous

Regardless of evidence: legal commitments and contracts · pricing, billing, payments, refunds ·
hiring, firing, payroll · **security incident declaration and breach notification** ·
destructive or irreversible changes · access-control ownership and emergency credentials ·
final public statements and sensitive customer communications · **any change to a component's
own authority, credential scope, delegation depth, or stop controls**.

No amount of evidence and no promotion decision moves an item off this list.

## Current status

| Item | State |
|---|---|
| Capabilities promoted | **0** |
| Capabilities in evaluation | **0** |
| Autonomous executions to date | **0** |
| Evidence captured | **0 of 15** |
