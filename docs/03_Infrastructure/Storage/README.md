# Storage

**Status: Documented** - not claimed as implemented, tested, or validated.

Last updated: 2026-08-07

---

## Scope

Bulk and application storage with explicit redundancy, dataset design, and defined consumers.

## Design principles applied

- Redundancy level is a stated design decision, not an artifact of available disks
- Redundancy is only credible once failure behaviour has been exercised
- Storage is reachable only from authorised consumers
- Snapshots are not backups: they share fate with the system they protect

## Public-detail note

Capacity, pool layout, and share paths are not published.

## Maturity

Planned -> Documented -> Implemented -> Tested -> Validated

Current: **Documented**.
