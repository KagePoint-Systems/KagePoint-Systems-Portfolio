# Network

**Status: Documented** - not claimed as implemented, tested, or validated.

Last updated: 2026-08-07

---

## Scope

Segmented design organised by function and trust boundary, with default-deny policy between zones and target-and-port-specific allowances.

## Design principles applied

- Zones are defined by function and trust, not device type or location
- Default deny at every boundary; every allowance explicit and justified
- No component receives unrestricted inter-zone reachability
- The lab zone is treated as assumed hostile and isolated from production
- Cloud boundaries are not trusted extensions of the internal network

## Public-detail note

Addresses, subnets, VLAN identifiers, hostnames, and firewall rule exports are not published.

## Maturity

Planned -> Documented -> Implemented -> Tested -> Validated

Current: **Documented**.
