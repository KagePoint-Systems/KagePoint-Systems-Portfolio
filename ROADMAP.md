# Roadmap

Last updated: 2026-08-07

---

> **Ratification note.** This eight-phase structure is the **working direction** for KagePoint
> Systems. It is currently pending formal ratification as a controlling document. It is
> published as direction, not as a locked plan.
>
> Publishing that caveat rather than quietly presenting the roadmap as settled is itself part
> of the documentation discipline this repository is about.

## Principles

1. **A phase advances on evidence, not elapsed time.** Exit criteria are met and validated, or
   the phase stays open.
2. **Future phases are not authorized.** Structure exists so work has somewhere to go — not
   because work is underway.
3. **Project phase and system trust level are separate controls.** A phase advancing never
   automatically grants any component more authority.
4. **Nothing is claimed above the evidence that exists.**

## Status vocabulary

**Planned → Documented → Implemented → Tested → Validated**

**Nothing across the roadmap is currently at _Implemented_ or above.**

---

## Phase 0 — Business and Service Foundation

**Status: Open in Execution / awaiting validation**

Establish decision authority, document lifecycle, domain separation, cost control, security
boundaries, and the operating model that every later phase depends on.

| Deliverable | Status |
|---|---|
| Canonical baseline | **Documented** — locked internally |
| Decision register | **Documented** |
| Conflict register | **Documented** — with open items left open |
| Authority model | **Documented** |
| Stop conditions | **Documented** |
| Security policy | **Documented** |
| Controlled deployment design | **Documented** — draft, not locked |
| Cost controls verification | Not started |
| Phase 0 exit review | Not started |
| Independent validation | Not performed |

**Exit:** cost-control verification, a Phase 0 exit review, and independent validation.

---

## Phase 1 — Internal Infrastructure Baseline

**Status: Not confirmed as started**

A documented, segmented, monitored, recoverable internal infrastructure baseline.

Workstreams: network foundation and segmentation · switching · virtualization · storage ·
container platform · administrative access · secrets management · backup and recovery ·
monitoring and alerting · secure remote access · asset, vendor, access, change, risk, and
document registers · Sentinel Lab Module 001 · technician handoff · Phase 2 readiness.

**All workstreams: Planned. No implementation evidence exists.**

**Entry:** Phase 0 exit review and independent validation — neither complete.

**Exit (expected):** every workstream validated with evidence; a **tested** restore; populated
registers; monitoring with **verified** alert delivery.

---

## Phase 2 — MSP Service Toolchain

**Status: Not approved**

Select, deploy, and document the managed-services toolchain: RMM, ticketing, documentation,
monitoring, patching, endpoint security, and reporting — each with defined data boundaries,
scoped credentials, and recovery.

**No vendor is committed. Tool selection is not pre-decided.**

**Entry:** Phase 1 complete and validated, plus explicit approval.

---

## Phase 3 — Internal Managed-Client Validation

**Status: Future — not authorized**

Validate the toolchain and service processes against KagePoint's **own** environment, treated
as the first managed client, before any external client is exposed to the delivery model.

---

## Phase 4 — Pilot Client Program

**Status: Future — not authorized**

Deliver managed services to a small number of real external pilot clients under contract, with
per-tenant credential separation, measurement, and human-owned escalation.

This phase crosses into real customer data. Legal commitments, pricing, billing, incident
declaration, and breach notification remain human-controlled throughout.

---

## Phase 5 — Market Proof and Controlled Growth

**Status: Future — not authorized**

Prove the model commercially and grow capacity deliberately — adding clients only as delivery
capability, staffing, and controls demonstrably support them.

Growth is the phase where controls most commonly erode. Credential separation, tenant
isolation, and approval gates must scale with client count rather than being relaxed.

---

## Phase 6 — MSSP Capability Expansion

**Status: Future — not authorized**

Expand from managed IT into managed **security** services, with the detection, response,
retention, and escalation capability those services genuinely require.

> **Capability constraint.** 24×7 support, a production SOC, MDR, compliance certification, and
> security guarantees are **not claimed now and will not be claimed** until internal evidence
> validates the capability. Detection capability without response capacity is a liability, not
> a service. Any coverage claim must match actually staffed hours.

---

## Phase 7 — Forge / Automation Integration

**Status: Future — not authorized**

Integrate KagePoint Forge and the automation layer into service delivery so repeatable work
executes deterministically with recorded state, approval gates, audit records, and recovery
state.

**Already decided, and not re-opened by this phase:**

- Forge and n8n are deterministic execution layers; AI assistance coordinates and learns, Forge
  tracks state and approvals, n8n executes stable integrations
- Automation does not replace the planning, implementation, orchestration, or integration
  layers
- Agent memory is never the source of truth
- Forge is an execution layer, **not** an autonomous agent

Automation carries an **independent** authority gate: passing a defined acceptance-test suite
plus explicit approval. Currently **zero tests passed**. A phase advancing does not raise it.

---

## What comes next

The immediate next steps are Phase 0 completion items — cost-control verification, a Phase 0
exit review, and independent validation — plus formal ratification of this roadmap.

**No work is authorized against Phase 2 or beyond.**
