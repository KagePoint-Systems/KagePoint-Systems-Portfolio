# KagePoint Systems Architecture

**Status: Documented** — conceptual architecture. Not claimed as implemented, tested, or
validated.

Last updated: 2026-08-07

---

## Scope

Conceptual architecture only. Implementation specifics — addresses, subnets, VLAN IDs,
hostnames, device identifiers, and rule sets — are **deliberately not published**.

## Design constraints

The architecture is driven by five constraints, applied in this order when they conflict:

1. **Containment before capability.** A component gets reachability only where it is needed.
2. **Recoverability before performance.** If it cannot be restored, it is not finished.
3. **Evidence before assertion.** A control counts once it has been exercised and recorded.
4. **Separation before convenience.** Domains, tenants, and credentials stay separate even when
   merging them would be easier.
5. **Human control over irreversible decisions.** Automation proposes; people approve.

## Zone model

Zones are organized by **function and trust**, not by device type or physical location.

| Zone | Purpose | Trust posture |
|---|---|---|
| **Management Network** | Administrative plane for infrastructure | Highest sensitivity; tightest access |
| **Server Network** | Production application workloads | Trusted, but not privileged toward management |
| **Lab Network** | Sentinel Lab and experimentation | **Assumed hostile**; isolated from production |
| **Monitoring Network** | Telemetry collection and alerting | Receives widely, initiates narrowly |
| **Storage Network** | NAS and bulk storage | Restricted to authorized consumers |
| **Remote Access Zone** | Private remote-access gateways | Entry point; never a transit path |
| **IoT Network** | Untrusted appliances and devices | Untrusted; no business reachability |
| **Home/Personal Network** | Non-business use | Outside the business trust boundary |

### Rules applied at every boundary

- **Default deny.** Every allowance is explicit and justified.
- **Target-and-port specific.** No zone-wide or any-any permits.
- **No unrestricted inter-zone reachability** for any component.
- **Management planes are never publicly exposed.**
- **Cloud and pilot boundaries are not trusted extensions** of the internal network. A cloud
  host does not become a jump host, does not become a remote-access connector, and does not
  hold internal or customer credentials.

The lab zone is the one that most often gets designed carelessly. It is treated as **assumed
hostile** — it exists to run things that might break or misbehave, so its isolation is a
security control, not a convenience.

## Platform layers

| Layer | Responsibility |
|---|---|
| Firewall / routing | Zone enforcement, default-deny policy, controlled egress |
| Switching | Physical and logical segmentation |
| Virtualization | Compute for production and lab workloads, separated by zone |
| Storage | Bulk storage, dataset design, redundancy |
| Containers | Application packaging with declared network exposure |
| Remote access | Private, identity-based access — never open management ports |
| Monitoring | Availability and health telemetry with verified alert delivery |
| Backup and recovery | Coverage, retention, offsite copy, and **restore testing** |
| Orchestration (Forge) | Job state, queues, approvals, audit records, recovery state |
| Integration (n8n) | Scheduled and repeatable workflow execution |
| Validation (Sentinel Lab) | Security, failure, rollback, and recovery validation |
| Documentation and evidence | Version-controlled records; the Binder as source of truth |

## Control plane separation

A distinction that shapes much of the design:

```text
   Decides            Records & approves        Executes
   ────────           ──────────────────        ────────
   Humans        ──►  KagePoint Forge     ──►   n8n / scoped
   AI assistance      (state, approvals,        service accounts
   (proposes only)     audit, evidence)
```

AI assistance and automation **request** validated actions. Forge records and gates them. n8n
or a scoped service account performs them.

Nothing in the assistance layer holds direct, unrestricted production access. This is
deliberate: the safest design for an automated component is one where compromising it does not
grant production authority.

## Authority model

Capability is granted in graded levels, each with its own promotion evidence:

| Level | Capability |
|---|---|
| 0 | Observe and draft — read, summarize, propose. **Current level.** |
| 1 | Sandbox execution with approval — disposable containers, test repositories |
| 2 | Internal read-only integrations through scoped service accounts |
| 3 | Reversible internal execution — approved, idempotent, rollback-tested jobs |
| 4 | Limited internal production authority — pre-approved runbooks, narrow credentials |
| 5 | Client-assisted operations — separate tenant instances, contracts, escalation |

Promotion is **workflow-specific and evidence-based**, never a blanket permission increase.

### Always human-controlled, at every level

Legal commitments and contracts · pricing, billing, payments, purchases, refunds · hiring,
firing, payroll · **security incident declaration and breach notification** · destructive or
irreversible changes · access-control ownership and emergency credentials · final public
statements · promotion of governance decisions into the Binder · any change to a component's
own authority, credential scope, or emergency-stop controls.

## Domain separation

**KagePoint Systems** (professional infrastructure and services) and **ShadowForge** (creator
and media ecosystem) are separate operational domains with separate branding, workspaces,
credentials, data, and approval paths.

This is enforced architecturally rather than by convention: cross-domain credential reuse or
data blending is a defined stop condition, and work spanning domains is split into separate
authorized units rather than handled together.

## Tenant separation (future phases)

For any future client work:

- Client access requires **separate credentials**, and preferably separate instances
- **No component holds universal client credentials** — an explicitly rejected design
- Client data never moves into a non-client context

Designed now, before any client exists, because retrofitting tenant isolation reliably fails.

## What is not shown here

Addresses, subnets, VLAN identifiers, hostnames, device serials, MAC addresses, firewall rule
exports, vendor account identifiers, private management URLs, and capacity figures.

Their absence is the point: the architecture should be legible without them.

## Current maturity

| Area | Maturity |
|---|---|
| Zone model | **Documented** |
| Platform layer selection | **Documented** |
| Control plane separation | **Documented** |
| Authority model | **Documented** — in use for governance |
| Domain separation | **Documented** — in use |
| Tenant separation | **Planned** |
| Physical implementation | **Not evidenced** |

**No area is at Implemented, Tested, or Validated.**
