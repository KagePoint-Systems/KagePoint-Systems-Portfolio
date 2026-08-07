# Monitoring

**Status: Documented** - not claimed as implemented, tested, or validated.

Last updated: 2026-08-07

---

## Scope

Availability and health monitoring across hosts, services, storage, and network, with alert routing.

## Design principles applied

- Coverage is defined deliberately rather than emerging from whatever was easy to instrument
- **Alert delivery is verified end to end.** Monitoring that collects but does not successfully notify is not monitoring
- The monitoring zone receives widely and initiates narrowly

## Public-detail note

Endpoints, dashboards, and alert destinations are not published.

## Maturity

Planned -> Documented -> Implemented -> Tested -> Validated

Current: **Documented**.
