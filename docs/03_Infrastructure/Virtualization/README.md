# Virtualization

**Status: Documented** - not claimed as implemented, tested, or validated.

Last updated: 2026-08-07

---

## Scope

Hypervisor-based compute for production and lab workloads, separated by zone.

## Design principles applied

- Production and lab workloads are separated at the network boundary, not merely by tagging
- Host administrative access follows the same least-privilege rules as any other management plane
- Host inventory, roles, versions, and resource allocation are recorded as an operational requirement

## Public-detail note

Host counts, capacity figures, and identifiers are not published.

## Maturity

Planned -> Documented -> Implemented -> Tested -> Validated

Current: **Documented**.
