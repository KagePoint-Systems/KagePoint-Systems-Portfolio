# Recovery Principles

**Status: Documented** — principles defined. **No recovery testing has been performed or
evidenced.**

Last updated: 2026-08-07

---

## 1. A backup that has not been restored is a hypothesis

Until a restore has been performed and verified, a backup is an assumption about future
behaviour. It is recorded as **untested**, never as protection.

This is the single principle most often stated and least often practised, so it leads.

## 2. Recoverability is a design requirement

Backup coverage, retention, offsite copy, and recovery objectives are decided **before** a
system is trusted with anything that matters — not after the first incident.

## 3. Recovery objectives are stated per system

Each system carries an explicit **Recovery Time Objective** (how long restoration may take) and
**Recovery Point Objective** (how much data loss is acceptable).

Undefined objectives mean the answer is discovered during an incident, which is the worst
possible time to find out that "as fast as possible" and "hours" were different expectations.

## 4. Restore testing is scheduled, not incidental

Restore tests happen on a schedule with recorded date, method, operator, and result — not
opportunistically when someone has time, and not only after a failure.

## 5. Failed recovery tests are evidence and are retained

A failed restore is one of the most valuable artifacts a system produces: it identifies a real
gap before that gap matters.

Failures are recorded and kept. They are never deleted, and a failed test is never quietly
re-run until it passes without recording the earlier result.

## 6. GitHub is not a backup

Version control is a collaboration and history tool. A single hosted copy under one account is
not a backup strategy — it shares fate with account availability, access, and error.

Backup destinations for documentation repositories are decided and recorded explicitly. As of
this writing, that decision is **open**.

## 7. Recovery state is orchestrated, not remembered

Recovery state, job state, and approval records live in the orchestration layer with an audit
trail — not in someone's memory, and not in an automated component's context.

## 8. Automation must be reversible before it is trusted

Any automated action touching something material must be **idempotent**, **reversible**, and
**rollback-tested** before promotion. Rollback is designed with the action, not afterward.

## 9. Recovery includes credentials

A recovery plan that restores systems but not access is incomplete. Emergency credentials,
recovery codes, and access ownership are explicitly human-controlled and part of recovery
planning.

## 10. Separate the backup from what it protects

A backup reachable with the same credentials, on the same host, or in the same trust zone as
the system it protects will be lost with that system. Backup destinations are separated by
credential and boundary.

## Current maturity — stated plainly

| Recovery capability | Maturity |
|---|---|
| Recovery principles defined | **Documented** |
| Backup coverage design | **Planned** |
| Retention and offsite design | **Planned** |
| Recovery objectives per system | **Not defined** |
| **Restore testing** | **Not performed — no evidence exists** |
| Redundancy failure testing | **Not performed** |
| Backup destination for documentation repositories | **Open decision** |
| Rollback testing for automation | **Not performed** |

**Nothing in this area is at Implemented, Tested, or Validated maturity.**

Publishing a recovery table this empty is deliberate. A portfolio that claimed tested recovery
without evidence would fail the first principle on this page.
