# KagePoint Systems

**A public, sanitized exploration of how a secure MSP/MSSP-style infrastructure, automation,
documentation, and security ecosystem is being designed and built — deliberately, in phases,
with evidence.**

---

## What this repository is

This is a **portfolio and engineering-exploration repository**. It documents the architecture,
governance model, security principles, and phase-based approach behind KagePoint Systems.

It is a record of **how the work is being reasoned about**, not a product, not a service
listing, and not an operational runbook.

## What this repository is not

- Not a copy of the internal operations repository
- Not a source of operational detail — no addresses, hostnames, credentials, device
  identifiers, or configuration exports appear here
- Not a customer-facing service catalog
- Not a claim of capability beyond what the internal evidence supports

**All public documentation here is sanitized.** Customer information, credentials, and
sensitive operational detail are not published, in any form, anywhere in this repository.

## Why this project exists

Most homelab and MSP write-ups show a finished diagram and a parts list. This one shows the
harder part: deciding what to build, in what order, with what controls, and how to know
whether it actually works.

The organizing constraints are:

- **Security first** — segmentation, least privilege, and default-deny are design inputs, not
  retrofits
- **Recovery first** — a system that cannot be restored is not built
- **Evidence over assertion** — "implemented" means an artifact exists, not that it was
  intended
- **Phase discipline** — a phase advances when its exit criteria are met and validated, not
  when it feels done
- **Documentation as infrastructure** — decisions, conflicts, and gaps are recorded, including
  the inconvenient ones

## Current status — honest version

| Item | State |
|---|---|
| Current phase | **Phase 0 — Business and Service Foundation**, open and awaiting validation |
| Phase 1 | **Not confirmed as started** |
| Phase 2 and beyond | **Not approved** |
| Infrastructure | **Documented and planned.** Not claimed as implemented, tested, or validated |
| Services offered | **None.** KagePoint Systems is not currently delivering managed services |

Governance work is genuinely well advanced: a locked canonical baseline, a decision register, a
conflict register with **open items left open**, an authority matrix, and hard stop conditions
all exist and are in use.

Infrastructure work is **documented, not delivered.** This repository will not claim otherwise.

## Status vocabulary

Every statement in this repository uses one of these, and nothing is promoted without evidence:

| Status | Meaning |
|---|---|
| **Planned** | Intended; not yet documented |
| **Documented** | Design or procedure written down |
| **Implemented** | Built and in place |
| **Tested** | Exercised with a recorded result |
| **Validated** | Independently verified and accepted |

**Nothing in this repository is currently claimed above _Documented_.**

## High-level architecture

Conceptual only. Implementation specifics are deliberately not published.

```text
                        ┌─────────────────────────┐
                        │   Remote Access Zone    │  private gateways, zero-trust
                        └────────────┬────────────┘
                                     │  default deny
   ┌─────────────┬─────────────┬─────┴───────┬─────────────┬─────────────┐
   │ Management  │   Server    │     Lab     │ Monitoring  │   Storage   │
   │  Network    │   Network   │   Network   │   Network   │   Network   │
   │             │             │             │             │             │
   │ admin plane │ production  │  Sentinel   │  telemetry  │  NAS, bulk  │
   │             │  workloads  │    Lab      │  + alerting │   storage   │
   └─────────────┴─────────────┴─────────────┴─────────────┴─────────────┘
   ┌─────────────┬─────────────┐
   │    IoT      │Home/Personal│   untrusted / non-business
   └─────────────┴─────────────┘
```

Design rules applied across every boundary:

- Firewall policy **defaults to deny**; every allowance is explicit
- Access is **target-and-port specific**, never zone-wide
- No component receives unrestricted inter-zone reachability
- Cloud/pilot boundaries are **not** trusted extensions of the internal network — no jump
  hosts, no connectors, no shared credentials
- Management interfaces are **never** publicly exposed

## Phase roadmap

| Phase | Name | Status |
|---|---|---|
| 0 | Business and Service Foundation | **Open in Execution** |
| 1 | Internal Infrastructure Baseline | Not confirmed as started |
| 2 | MSP Service Toolchain | **Not approved** |
| 3 | Internal Managed-Client Validation | Future |
| 4 | Pilot Client Program | Future |
| 5 | Market Proof and Controlled Growth | Future |
| 6 | MSSP Capability Expansion | Future |
| 7 | Forge / Automation Integration | Future |

> **Note on the roadmap.** This structure is currently **pending formal ratification** as a
> controlling document. It is published as the working direction, not as a locked plan. Saying
> so is itself part of the documentation discipline this repository is about.

## Technology direction

Selected and in use for design work:

| Layer | Direction |
|---|---|
| Firewall / routing | pfSense |
| Virtualization | Proxmox |
| Storage | TrueNAS |
| Containers | Docker |
| Remote access | Twingate |
| Workflow automation | n8n |
| Availability monitoring | Uptime Kuma |
| Orchestration and state | KagePoint Forge |
| Validation environment | Sentinel Lab |
| Version control and evidence | GitHub |
| Code and document knowledge graphs | Graphify |
| AI assistance | Controlled, authority-gated tooling |

Direction, not deployment record. See [`docs/03_Infrastructure/`](docs/03_Infrastructure/).

## Security-first principles

- Segmentation by function and trust, not by convenience
- Default-deny between zones
- Least privilege, scoped per task rather than per person
- No plaintext credentials, ever, anywhere
- OS-level isolation for untrusted input — in-process approval gates are **not** containment
- Management planes stay private
- Third-party skills, plugins, and integrations are reviewed before installation

[`docs/01_Architecture/SECURITY_PRINCIPLES.md`](docs/01_Architecture/SECURITY_PRINCIPLES.md)

## Recovery-first principles

- Backup coverage is designed before a system is trusted
- A backup that has not been restored is a hypothesis
- Recovery objectives are stated per system
- Recovery evidence is retained, including failed attempts

[`docs/01_Architecture/RECOVERY_PRINCIPLES.md`](docs/01_Architecture/RECOVERY_PRINCIPLES.md)

## Documentation governance

```text
Execution  ->  Summary  ->  Master Binder
```

Work is drafted in Execution, tested in Summary, and only promoted to the Binder — the approved
source of truth — by explicit owner approval. Every decision carries exactly one
classification: **Locked**, **Draft**, **Future-phase**, or **Rejected/superseded**.

Conflicts between sources are **recorded, not silently resolved**, and source material is never
edited to remove a contradiction. Open evidence gaps stay open.

[`docs/00_Governance/`](docs/00_Governance/)

## Validation approach

The **Sentinel Lab** is an isolated environment for validating security controls, failure
modes, rollback, and recovery — so that failures happen there rather than in production.

[`docs/04_Security/Sentinel-Lab/`](docs/04_Security/Sentinel-Lab/)

## Automation direction

**KagePoint Forge** is the deterministic orchestration and state layer: job state, queues,
approvals, audit records, evidence, recovery state. **n8n** executes stable, repeatable
integrations.

The deliberate design choice: automation and AI assistance **request** validated actions
through Forge or n8n, which perform them using scoped service accounts. Nothing gets direct,
unrestricted production access.

[`docs/05_Automation/`](docs/05_Automation/)

## Capability disclaimer

KagePoint Systems makes **no** claim to any of the following, and none should be inferred from
this repository:

- 24×7 support
- A production Security Operations Center
- Managed Detection and Response
- Compliance certification of any kind
- Security guarantees

These are recorded as future-phase capabilities with defined gates. They will only ever be
claimed here when internal evidence supports them.

## Repository map

| Path | Content |
|---|---|
| [`docs/00_Governance/`](docs/00_Governance/) | Governance model, decision classification, document lifecycle |
| [`docs/01_Architecture/`](docs/01_Architecture/) | System architecture, security and recovery principles |
| [`docs/02_Phases/`](docs/02_Phases/) | Phase 0–7 objectives and status |
| [`docs/03_Infrastructure/`](docs/03_Infrastructure/) | Network, virtualization, storage, monitoring, remote access, backup |
| [`docs/04_Security/`](docs/04_Security/) | Sentinel Lab, access control, segmentation, validation |
| [`docs/05_Automation/`](docs/05_Automation/) | n8n, KagePoint Forge, AI governance, Graphify |
| [`docs/06_Portfolio-Case-Studies/`](docs/06_Portfolio-Case-Studies/) | Case studies with honest status labels |
| [`diagrams/`](diagrams/) · [`examples/`](examples/) · [`templates/`](templates/) | Supporting material |

## A note on scope

KagePoint Systems is the professional infrastructure and services business. **ShadowForge** is
a separate creator and media ecosystem, run as a distinct operational domain with its own
workspaces, credentials, and approval paths. Nothing from that domain is published here. The
separation is architectural and intentional.

## License

[MIT](LICENSE) — documentation and examples.

---

*Author: Allen Rhodes · Organization: KagePoint Systems · Last updated: 2026-08-07*
