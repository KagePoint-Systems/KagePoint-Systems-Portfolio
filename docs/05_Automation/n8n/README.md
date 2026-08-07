# n8n

**Status: Planned** - not claimed as implemented, tested, or validated.

Last updated: 2026-08-07

---

## Scope

Integration engine for schedules, webhooks, notifications, approval routing, and repeatable data movement.

## Design principles applied

- n8n executes proven, stable integrations - it does not decide what should happen
- Workflows must be idempotent, reversible, and rollback-tested before promotion
- Actions are performed with scoped service accounts, never broad credentials
- No workflow is production-approved at present

## Public-detail note

Workflow definitions, endpoints, and credential references are not published.

## Maturity

Planned -> Documented -> Implemented -> Tested -> Validated

Current: **Planned**.
