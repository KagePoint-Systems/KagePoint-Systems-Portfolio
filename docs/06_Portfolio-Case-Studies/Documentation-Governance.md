# Case Study — Documentation Governance

**Implementation status: Documented** — the model is in active use
**Validation status: Not confirmed** — no independent review has been performed

Date: 2026-08-07

---

## Problem

Technical documentation fails in a predictable way. It does not usually become *wrong* all at
once — it becomes **ambiguous about its own authority**.

Two documents describe the same system differently and nobody knows which one governs. A
decision gets revisited because no one recorded why the alternative was rejected. A status
table says "complete" because someone filled in a blank rather than leaving it empty. A
navigation index quietly becomes the thing people trust, because it is easier to read than the
documents it links to.

Every one of those failures is a governance problem, not a writing problem.

## Design constraints

1. A reader must be able to tell a document's authority **from the document itself**, without
   external context.
2. Contradictions between sources must survive discovery rather than be smoothed away.
3. Gaps must be visible.
4. History must be recoverable, so a current decision can be traced to its reasoning.
5. The model must work under AI-assisted authoring, where volume is cheap and plausible-sounding
   fabrication is the main risk.

## Decisions

### Documents declare their own authority

Every document carries a header stating status, lifecycle, authority class, applicable phase,
implementation status, validation status, and **whether it affects a phase gate**.

That last field does most of the work. The common failure is not a reader misunderstanding
content — it is a reader assuming a document carries more weight than it does. Stating *"does
not approve a phase transition"* on the document removes the ambiguity at the point of reading,
where it matters.

### Exactly one classification per decision

**Locked**, **Draft**, **Future-phase**, or **Rejected/superseded**. No "mostly decided."

Rejected decisions are kept **with their reason**. This is the classification most often
skipped and most often regretted — without it, a rejected option returns later with no record
of why it lost, and either gets re-analyzed from scratch or accepted by accident.

### Supersession is partial by default

When a decision is superseded, **only the named field is superseded** and the original text is
retained as the approved record.

This came directly from a real case: a repository's owner changed from a personal account to an
organization. Treating that as superseding the *entire* baseline would have silently
invalidated the project name, runtime path, promotion gate, and agent structure — none of which
changed. Scoping supersession to the one field kept the rest intact.

### Conflicts are registered, not resolved by editing

A conflict register records the conflicting values, the evidence for each, which value
controls, and the resolution status.

**Source documents are never edited to remove a contradiction.** Correcting the evidence
destroys the audit trail that makes the record worth keeping. A document that states a
superseded value remains valid as evidence of what was believed at the time — it is simply not
authoritative for that field.

### Open items stay open

`Evidence Needed`, `Owner Decision Required`, and `Not Yet Confirmed` are **valid terminal
states**, not blanks to be tidied.

A status table filled with assumptions looks complete and is actively misleading — strictly
worse than an obviously incomplete one, because nobody goes looking for the gap.

The current governance set carries several long-open items, including missing upstream brand
documentation that has been recorded as missing rather than reconstructed, with an explicit
instruction not to fabricate or infer it.

### Maturity is separate from document state

Documents use lifecycle states. Systems and evidence use **Planned → Documented → Implemented →
Tested → Validated**.

Keeping them on separate axes prevents the failure where a well-written design document implies
deployed infrastructure. A document can be finished while the thing it describes has not been
started.

### Validation requires someone else

**Validated** requires a validator independent of whoever did the work. Self-validation is not
validation, however careful the self-review.

### Navigation indexes are explicitly not authority

Indexes state, in their own header, that they are navigation aids and that linked documents
remain the authority.

This was learned the hard way: a prior index drifted into being treated as the map of the
project, and continued asserting an active phase and a master reference document long after
both had changed.

## Implementation status

**Documented and in active use.** The model governs a locked canonical baseline, a decision
register, a conflict register with open items genuinely left open, an authority matrix, a
source manifest with integrity hashes, and a defined set of stop conditions.

## Validation status

**Not confirmed.** No independent review of the governance model itself has been performed.
Recording that, rather than treating "we use it" as validation, is the model applied to itself.

## Lessons learned

**Authority ambiguity is the real failure mode.** Most documentation advice targets clarity of
content. In practice, well-written documents that disagree about which one governs cause more
damage than a badly written document that is unambiguously authoritative.

**Registers beat rewrites.** Recording a conflict takes minutes and preserves the reasoning.
Rewriting sources to agree takes longer, destroys the trail, and tends to encode whichever
version was most recently read.

**The discipline shows up in what is left empty.** Any governance model can produce a complete
status table. The test is whether it can produce an *incomplete* one and leave it that way.

**AI-assisted authoring makes this more important, not less.** When producing plausible
documentation is nearly free, the scarce thing is the constraint that stops plausible from
being mistaken for verified. Evidence requirements, independent validation, and hard blocks on
fabricated evidence are that constraint.

## Next phase

Independent review of the governance model; ratification of documents currently pending it; and
closing the long-open evidence gaps — which requires supplying the missing material, not
writing around it.
