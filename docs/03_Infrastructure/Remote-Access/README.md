# Remote Access

**Status: Documented** - not claimed as implemented, tested, or validated.

Last updated: 2026-08-07

---

## Scope

Private, identity-based remote access. No open management ports.

## Design principles applied

- Management interfaces are never publicly exposed - not behind authentication, not temporarily
- Access is identity-based and per-target, not a flat tunnel into a zone
- The remote-access zone is an entry point, never a transit path
- External exposure is verified by testing from outside, not assumed from configuration

## Public-detail note

Gateway addresses, connector topology, and account inventory are not published.

## Maturity

Planned -> Documented -> Implemented -> Tested -> Validated

Current: **Documented**.
