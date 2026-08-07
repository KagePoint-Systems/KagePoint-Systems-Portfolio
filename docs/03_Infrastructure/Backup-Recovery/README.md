# Backup and Recovery

**Status: Documented** - not claimed as implemented, tested, or validated.

Last updated: 2026-08-07

---

## Scope

Backup coverage, retention, offsite copy, restore testing, and recovery objectives.

## Design principles applied

- **A backup that has not been restored is a hypothesis, not protection**
- Recovery Time and Recovery Point Objectives are stated per system
- Restore tests are scheduled with recorded date, method, operator, and result
- Failed restore tests are retained as evidence, never deleted
- Backup destinations are separated by credential and trust boundary from what they protect
- Version control is not a backup strategy

## Public-detail note

**No restore test has been performed or evidenced.** Destinations and schedules are not published.

## Maturity

Planned -> Documented -> Implemented -> Tested -> Validated

Current: **Documented**.
