# Portfolio Overview

*What this repository demonstrates, and what it deliberately does not claim.*

Last updated: 2026-08-07

---

## Purpose

This repository exists to show engineering judgement — the reasoning, constraints, and
discipline behind an infrastructure build — rather than a finished topology diagram.

Anyone can post a rack photo. The harder and more transferable skill is deciding what to build,
in what order, under what controls, and knowing how to tell whether it works.

## What this demonstrates

### Systems thinking

Infrastructure is treated as one system with interacting failure modes, not a collection of
appliances. Segmentation, monitoring, backup, and access control are designed against each
other rather than bolted together.

### Network and infrastructure architecture

A segmented design organized by function and trust boundary — management, server, lab,
monitoring, storage, remote access, and untrusted zones — with default-deny policy between them
and target-and-port-specific allowances.

### Security-first design

Security constraints are design **inputs**. Concretely: no plaintext credentials; OS-level
isolation for untrusted input, with explicit recognition that in-process approval gates are not
containment; management planes never publicly exposed; cloud boundaries not treated as trusted
extensions of the internal network; third-party integrations reviewed before installation.

### Documentation discipline

Documents carry lifecycle state, authority classification, and an explicit statement of whether
they affect a phase gate. Decisions carry exactly one classification. Conflicts between sources
are recorded in a register rather than resolved by editing the evidence.

**The clearest demonstration of this discipline is that open items are left open.** Missing
documents are recorded as missing. Unconfirmed states are recorded as unconfirmed. Nothing is
inferred to make a status table look complete.

### Recovery planning

Backup coverage, retention, offsite copy, and recovery objectives are treated as design
requirements. A backup that has not been restored is recorded as untested — not as protection.

### Phase-based implementation

Eight phases from business foundation through MSSP capability, each with objectives, entry
criteria, deliverables, security and recovery considerations, evidence expectations, blockers,
and exit criteria. Future phases are labelled future and are **not authorized for execution**.

### Automation planning

A deliberate separation: an orchestration layer that owns job state, queues, approvals, and
audit records; an integration engine that executes proven workflows; and AI assistance that
**requests** validated actions rather than performing them directly. Automation earns authority
by passing tests, not by being convenient.

### Validation methodology

A five-level maturity vocabulary — Planned, Documented, Implemented, Tested, Validated — where
promotion requires an artifact, and *Validated* additionally requires a validator independent of
whoever did the work.

### Sentinel Lab

An isolated environment for exercising security controls, failure modes, rollback, and recovery
before those paths are needed in production.

### KagePoint Forge

The deterministic orchestration and state backbone. Notably, Forge is **not** an autonomous
agent — a design decision recorded explicitly, along with the reasoning.

### MSP/MSSP service architecture

A service model built around tenant separation, scoped credentials, and human control over
legal, financial, and incident decisions — designed before any client exists, rather than
retrofitted after the first one.

### Technical decision discipline

Decisions are recorded with rationale and boundary. Rejected options are recorded **with their
rejection reason**, so the same ground is not re-litigated. Superseded decisions name their
replacement.

## What this does not claim

| Not claimed | Actual state |
|---|---|
| Working production infrastructure | Documented and planned |
| Managed services in delivery | None. No clients |
| 24×7 support | Not claimed. Future-phase with a defined gate |
| Production SOC | Not claimed. Future-phase |
| Managed Detection and Response | Not claimed. Future-phase |
| Compliance certification | Not claimed. None held |
| Security guarantees | Not claimed. None offered |
| Validated infrastructure | **Nothing is currently at Validated maturity** |

## Current honest status

**Governance: substantially advanced.** A locked canonical baseline, decision register,
conflict register, authority matrix, source manifest with integrity hashes, and hard stop
conditions all exist and are actively used.

**Infrastructure: documented, not delivered.** Design direction and principles are recorded.
Implementation evidence does not yet exist.

**Services: none.** KagePoint Systems is not currently delivering managed services to anyone.

That gap between governance maturity and implementation maturity is real, and showing it
accurately is more useful than hiding it.

## Sanitization

This is a **public-safe derivative**, not a copy of internal documentation.

Excluded by design: credentials and secrets of every kind; IP addresses, subnets, and VLAN IDs;
hostnames and device identifiers; MAC addresses and serial numbers; firewall rule exports;
vendor account identifiers; private management URLs; customer, employee, and personal data;
internal operational evidence.

Published instead: conceptual zone names, design principles, decision rationale, phase
structure, and validation methodology.

## Intended audience

Engineers, hiring managers, and peers evaluating how someone approaches infrastructure,
security, and operational discipline — particularly anyone who cares more about whether
somebody can reason about failure modes and evidence than whether they can name products.
