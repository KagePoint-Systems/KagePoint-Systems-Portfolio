# AGENTS.md — Operating instructions for coding agents

```text
Document status:       Execution Draft
Lifecycle:             Execution
Authority:             Supporting
Phase:                 All phases (not phase-specific)
Implementation status: Not confirmed
Validation status:     Not confirmed
Gate effect:           Does not approve a phase transition
Date:                  2026-09-06
```

Applies to every Claude Code and Codex session in this repository. `CLAUDE.md` imports this file.

This document has two parts with different provenance. **Part A** restates existing repository
governance and cites its source for every statement. **Part B** contains owner-provided operating
instructions for agent sessions in the current execution scope. Part B is **not** repository
governance: it is **Draft** under `docs/00_Governance/DECISION_CLASSIFICATION.md` ("Any decision
recorded during ordinary work is Draft"), it is not Locked, and it creates no authority.

---

## Part A — Repository governance (canonical sources cited)

### A1. Repository identity

- `KagePoint-Systems/KagePoint-Systems-Portfolio` — **public**.
- A public, sanitized portfolio documenting how KagePoint Systems is being designed and built; a
  record of engineering reasoning, not a collaborative product (`CONTRIBUTING.md`).
- Authority flow: `Execution -> Summary -> Master Binder`. Public and Execution-stage
  repositories cannot create a Locked decision; only owner approval through Summary can
  (`docs/00_Governance/DECISION_CLASSIFICATION.md`, `docs/00_Governance/GOVERNANCE_MODEL.md`).
- Every document declares its own state in a header of the shape defined in
  `templates/README.md` (`docs/00_Governance/DOCUMENT_LIFECYCLE.md`).

### A2. Read first

1. `README.md`, `CONTRIBUTING.md`, `SECURITY.md`
2. `docs/00_Governance/GOVERNANCE_MODEL.md`
3. `docs/00_Governance/DOCUMENT_LIFECYCLE.md`
4. `docs/00_Governance/DECISION_CLASSIFICATION.md`
5. `templates/README.md` — the document header template

### A3. Public-repository constraints (`SECURITY.md`, `.github/PULL_REQUEST_TEMPLATE.md`)

Never add any of the following, in any file, commit, branch, or discussion:

- credentials, tokens, keys, passwords, recovery codes, certificate material
- IP addresses, subnets, network zone identifiers
- hostnames, device serial numbers, MAC addresses, device identifiers
- firewall rule exports, configuration backups, private or internal administrative URLs, vendor
  account identifiers
- customer, client, or employee data; personal contact information; internal operational
  evidence
- content from the separate ShadowForge creator/media domain
- a status label moved up the maturity scale without evidence
- a capability claim internal evidence does not support — in particular no 24x7, SOC, MDR,
  compliance, or guarantee claim

Conceptual zone names and design principles are published. Implementation specifics are not.

### A4. The honesty rule (`CONTRIBUTING.md`, `README.md` status vocabulary)

Status vocabulary is **Planned, Documented, Implemented, Tested, Validated**. Nothing moves up
that scale without evidence. *Documented* means the design is written down and the
implementation is **not** evidenced; that must stay accurate. Nothing in this repository is
currently claimed above *Documented*. Document state (Execution Draft, Summary Candidate, Binder
Candidate, Binder / Locked, Superseded, Historical, Rejected) is a separate axis from system
maturity; do not conflate them (`docs/00_Governance/DOCUMENT_LIFECYCLE.md`).

### A5. Evidence discipline (`docs/00_Governance/GOVERNANCE_MODEL.md`)

A claim of Implemented, Tested, or Validated requires an artifact. **Validated** additionally
requires an independent validator: the identity that performed the change may not be its sole
validator. Fabricated evidence, including citing a source that does not exist, is a hard block on
any promotion.

### A6. Process and supersession (`CONTRIBUTING.md`, `docs/00_Governance/DOCUMENT_LIFECYCLE.md`)

- Substantial changes start as an issue. Keep each pull request focused on one thing. Match the
  existing tone: direct, specific, no marketing language. Confirm no sensitive information is
  included. Every pull request follows `.github/PULL_REQUEST_TEMPLATE.md`.
- **Exception — suspected exposure.** A suspected credential, infrastructure identifier,
  personal-data, or other exposure is **not** raised as a public issue. It is reported privately
  through the GitHub security advisory named in `SECURITY.md`, stating what was found and where.
  The sensitive value itself is never included in the report, in an issue, or in agent output
  (`SECURITY.md`, "Reporting a concern"; `CONTRIBUTING.md`, "Reporting a security or privacy
  concern").
- Superseded documents are **never deleted**: preserve a copy, state the controlling replacement
  inside the superseded copy, record the supersession in the conflict register, update the
  document register. Where a register does not exist, its absence is recorded, because absence is
  recorded and `Owner Decision Required` is a valid terminal state.
- Conflicts between sources are recorded, not silently resolved; source material is never edited
  to remove a contradiction (`docs/00_Governance/GOVERNANCE_MODEL.md`).

### A7. Superseded agent-instruction files in this repository

- The former root `CLAUDE.md` (Graphify instructions, committed 2026-08-07) is superseded by this
  file. Its preserved copy, with the controlling replacement stated inside, is
  `docs/00_Governance/superseded/CLAUDE-MD_GRAPHIFY-INSTRUCTIONS_SUPERSEDED_2026-09-06.md`.
- `.claude/CLAUDE.md` is superseded **in place**: retained, not deleted, with its supersession
  statement and original content inside it. Do not act on the instructions it contains.
- This repository has no conflict register and no document register; steps 3 and 4 of the
  supersession procedure are therefore recorded as absent. Owner Decision Required.

---

## Part B — Owner-provided operating instructions (not repository governance; Draft)

Provenance: provided by the repository owner for agent sessions during the current execution
scope (the agent-instructions change of 2026-09-06). These are operating instructions for this
agent, not repository governance. They do not appear in any canonical Portfolio document, are
not Locked, and may be changed by the owner at any time.

### B1. Roles

- **Claude Code** — drafts and implements documentation changes within the scope the owner
  approves.
- **Codex** — reviews for accuracy, sanitization, status honesty, and focus, acting as the
  independent validator that Part A5 requires.
- **Owner** — sets Locked, approves promotion, decides what is published.

### B2. Session rules

- Confirm the Git root and `origin` before changing anything. Work only inside this repository.
- Work on an explicit branch the owner designates. Do not modify `main` directly.
- Do not commit, push, merge, open pull requests, or change Git configuration unless the owner
  instructs it in the current session.

### B3. Summary handling

`docs/00_Governance/DOCUMENT_LIFECYCLE.md` defines **Summary Candidate** as a document state
declared in the document header (Part A).

- **Owner instruction (this scoped change):** do not invent a Summary record location in this
  repository.
- **Repository lifecycle state, not an owner instruction:** the conflict-register and
  document-register steps of the supersession procedure cannot currently be completed because
  those registers are absent from this tracked repository. They are recorded as Owner Decision
  Required (Part A7) and are not claimed complete. Whether such registers are created later is a
  future owner/governance decision, not decided here.
