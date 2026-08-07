# Templates

**Status: Documented**

Reusable document templates reflecting the governance model.

## Document header template

Every internal document carries a header of this shape, so a reader can determine its authority
without external context:

```text
Document status:       Execution Draft | Summary Candidate | Binder Candidate | Locked
Lifecycle:             Execution | Summary | Binder
Authority:             Project Control | Supporting | Implementation Evidence | Placeholder
Phase:                 <applicable phase>
Implementation status: Not confirmed unless evidence exists
Validation status:     Not confirmed unless evidence exists
Gate effect:           Does not approve a phase transition
Date:                  <ISO date>
```

## Phase document template

Phase name - Objective - Current status - Scope - Entry criteria - Expected deliverables -
Security considerations - Recovery considerations - Evidence expectations - Known dependencies -
Known blockers - Exit criteria - Next-phase boundary.

## Case study template

Problem - Design constraints - Decision - Implementation status - Validation status - Lessons
learned - Next phase.

## Evidence record template

Evidence ID - Workstream - Requirement - Artifact - Current maturity - Required maturity -
Evidence location - Sensitivity - Owner - Status - Dependency - Gate impact.

## Decision record template

ID - Decision - Rationale - **Boundary (what it does not cover)** - Classification (Locked /
Draft / Future-phase / Rejected-superseded) - Validation needed - Approved by - Date.

The boundary field is not optional. A decision without a stated boundary is an ambiguity waiting
to be resolved by whoever is under the most time pressure.
