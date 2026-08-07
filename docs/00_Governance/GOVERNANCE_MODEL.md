# Governance Model

**Status: Documented** - in active use.

Last updated: 2026-08-07

---

## Authority flow

```text
Execution  ->  Summary  ->  Master Binder
```

- **Execution** - draft, test, inspect, iterate inside an authorised workspace
- **Summary** - validate scope, evidence, risks, changes, and test results. A Summary is where a claim of completion is *tested*, not asserted
- **Master Binder** - only approved, stable, validated decisions and procedures. The source of truth. Promotion requires explicit owner approval

The distinction that makes this work: **writing something down does not make it true.** A
document becomes authoritative by surviving validation, not by existing.

## Decision classification

Every decision carries exactly one classification:

| Classification | Meaning |
|---|---|
| **Locked** | Approved and binding |
| **Draft** | Proposed; requires validation |
| **Future-phase** | Deferred, with a named promotion gate |
| **Rejected/superseded** | No longer applies; names its replacement |

Rejected decisions are kept **with their rejection reason**, so the same ground is not
re-litigated later by someone who does not know it was already considered.

## Conflict handling

Conflicts between sources are **recorded, not silently resolved.**

Source material is never edited to remove a contradiction - correcting the evidence destroys
the audit trail that makes the record worth having.

A conflict register records the conflicting values, the evidence for each, which value
controls, and the resolution status. **Open items stay open.** They are not closed by
restatement, inference, or the passage of time.

## Authority order

When sources disagree, precedence runs: owner-approved governance instructions, then
project-control documents, decision register, source-authority index, roadmap, approved phase
documents, implementation documents, test and evidence records, supporting material, and
finally historical documents.

Historical documents rank last deliberately. A document can be entirely accurate about what was
true in May and entirely wrong about what is true now.

## Always human-controlled

Regardless of automation maturity: legal commitments and contracts; pricing, billing, payments,
purchases, refunds; hiring, firing, payroll; **security incident declaration and breach
notification**; destructive or irreversible changes; access-control ownership and emergency
credentials; final public statements; promotion of governance decisions into the Binder; and
any change to an automated component's own authority, credential scope, or stop controls.

## Evidence discipline

A claim of Implemented, Tested, or Validated requires an artifact.

**Validated** additionally requires an independent validator - the identity that performed the
change may not be its sole validator. Self-validation is not validation.

Fabricated evidence - reporting a test as passed without running it, or citing a source that
does not exist - is a hard block on any promotion.
