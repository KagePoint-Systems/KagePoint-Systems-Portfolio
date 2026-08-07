# Segmentation

**Status: Documented** - not claimed as implemented, tested, or validated.

Last updated: 2026-08-07

---

## Scope

Zone-based segmentation by function and trust, enforced with default-deny policy.

## Design principles applied

- Segmentation is a design input, not a retrofit
- Every inter-zone allowance is explicit, target-and-port specific, and justified
- Segmentation is only credible once reachability has been tested against the design
- Domain and tenant separation extend the same principle to credentials and data

## Public-detail note

Zone identifiers, rule sets, and address plans are not published.

## Maturity

Planned -> Documented -> Implemented -> Tested -> Validated

Current: **Documented**.
