# Security Principles

**Status: Documented** — principles in active use for governance. Infrastructure enforcement
is not yet evidenced.

Last updated: 2026-08-07

---

## 1. Security constraints are design inputs

Segmentation, least privilege, and default-deny are decided **before** a system is built, not
added after it works. A control retrofitted onto a running system is a compromise with whatever
was built first.

## 2. Default deny

Every zone boundary denies by default. Every allowance is explicit, target-and-port specific,
and justified. There are no zone-wide permits and no any-any rules.

## 3. Least privilege, scoped per task

Access is scoped to the task, not to the person or the component. A scope granted for one
purpose does not carry to the next.

Concretely: automation receives task-scoped authority rather than inherited full authority, with
explicit tools, limits, evidence requirements, rollback, and stop conditions per task.

## 4. No plaintext credentials, anywhere

Credentials live only in an approved credential store. Never in Git, documentation, logs,
prompts, screenshots, issue text, commit messages, or configuration files.

A credential that has been committed is compromised, regardless of whether the commit was
later removed. Deletion does not undo publication — it remains in history and in every clone.

## 5. In-process gates are not containment

Approval prompts and allowlists inside a process are useful **controls**. They are not
**containment**, because anything that compromises the process compromises the gate.

Real containment is OS-level: separate hosts, containers with genuine boundaries, separate
credentials, separate network zones.

This distinction is easy to state and easy to violate, so it is written down.

## 6. Untrusted input stays isolated

Messaging, web content, documents, and third-party data are untrusted input. Anything
processing them runs isolated, with no path to production credentials or systems.

## 7. Management planes stay private

Administration interfaces, dashboards, and APIs are never publicly exposed — not behind
authentication, not temporarily, not "just for setup". Where temporary exposure is genuinely
unavoidable during bootstrap, it is source-restricted to a single administrative address and
removed immediately afterward.

Exposed management interfaces are among the most reliably exploited assets on the internet.
Authentication improvements do not change the requirement.

## 8. Cloud boundaries are not internal boundaries

A cloud or pilot host is a **separate boundary**, not a trusted extension of the internal
network. It does not become a jump host, does not become a remote-access connector, does not
receive internal reachability, and does not hold customer credentials or data.

## 9. Domain and tenant separation

Domains keep separate credentials, workspaces, branding, data, and approval paths. Cross-domain
credential reuse or data blending is a stop condition, not a judgement call.

For client work: separate credentials per tenant, preferably separate instances. **No component
holds universal client credentials** — that design is explicitly rejected, on the grounds of
blast radius and absent capability separation.

## 10. Review third-party code before installing it

Every third-party skill, plugin, integration, and MCP server is reviewed — code and scripts —
before installation. Convenience is not a review.

## 11. Stop conditions are stops, not warnings

Defined stop conditions halt work immediately. They are not retry triggers.

On a stop: stop immediately without "finishing cleanly"; do not self-remediate, delete, rewrite
history, force-push, or revert; preserve all evidence; report; do not resume without an
approved remediation plan.

Attempting to cover a stop condition is worse than the original event, because it destroys the
record needed to assess impact.

## 12. Fabricated evidence is a hard block

Presenting as fact any test, approval, system state, file content, command output, source
citation, or completion that did not occur — or cannot be reproduced on request — is a hard
stop and a hard block on any promotion.

This includes reporting a test as passed without running it, and citing a source document that
does not exist.

## 13. Humans control irreversible decisions

Security incident declaration and breach notification are always human-controlled. An automated
component may **detect, stop, report, and escalate**. It may not declare an incident, notify
externally, or decide a disclosure outcome.

The same applies to legal commitments, financial actions, destructive changes, access-control
ownership, and public statements.

## 14. Record gaps as gaps

An unverified control is recorded as unverified. A missing document is recorded as missing. An
unconfirmed rotation is recorded as unconfirmed.

Filling a status table with assumptions produces a document that looks complete and is
actively misleading — worse than an obviously incomplete one, because nobody goes looking for
the gap.

## Current maturity

| Principle area | Maturity |
|---|---|
| Governance and authority controls | **Documented** — in active use |
| Credential handling policy | **Documented** — in active use |
| Stop conditions | **Documented** — in active use |
| Domain separation | **Documented** — in active use |
| Network segmentation enforcement | **Planned** — not evidenced |
| Isolation verification | **Planned** — not evidenced |
| Tenant separation | **Planned** — no clients exist |

**No principle is claimed as Tested or Validated in infrastructure.**
