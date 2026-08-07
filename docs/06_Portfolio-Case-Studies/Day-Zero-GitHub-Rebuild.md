# Case Study — Day Zero GitHub Rebuild

**Implementation status: Documented** (the rebuild itself completed)
**Validation status: Not confirmed** — independent review outstanding

Date: 2026-08-07

---

## Problem

Several years of KagePoint Systems planning had accumulated in a single local workspace: around
70,000 files, most of them vendor dependencies, mixed in with governance documents, an earlier
creator-media project, a protected external repository checkout, binary software caches, and a
navigation index written for an organizational structure that no longer applied.

The goal was two clean repositories — a public portfolio and a private operations record —
without losing history, misrepresenting status, or leaking anything sensitive.

## Design constraints

1. **The source workspace was read-only.** No deletion, renaming, moving, normalization,
   restructuring, or in-place repair. Everything by copy.
2. **No secret could reach either repository**, and the public one additionally had to carry no
   infrastructure identifiers, customer data, or personal information.
3. **Nothing could be claimed as complete without evidence.**
4. **Domain separation had to hold** — creator-media material could not migrate into the
   professional portfolio.
5. **A protected external repository** was off limits by an existing stop condition.
6. **No phase could be advanced** and nothing promoted to the source of truth.

## What the review found

Three findings changed the shape of the work.

### The roadmap did not exist

The task specified an eight-phase roadmap and instructed that it be verified against the
controlling roadmap in the workspace.

**There was no controlling roadmap.** A content search for the roadmap name, the phase names,
and every roadmap-like filename across all 1,660 Markdown files returned nothing. The only
phase structures that existed were a superseded six-phase map in the legacy index and two
separate "Phase 00" workstreams under different document-ID prefixes.

### The stated active phase was not the actual active phase

The task described Phase 1 as the active execution phase. The most recent governance documents
showed the prior phase still open, with outstanding actions and **zero of fifteen** acceptance
tests passed — and an explicit line stating that a review was required *before Phase 1 is
considered*.

### The legacy index was thoroughly out of date

Its phase map, its "active phase" designation, and its list of most-used documents all
described an organizational structure that had since been superseded — and pointed at
creator-media material as the master reference for professional operations.

## Decision

The temptation in all three cases is to smooth it over: adopt the roadmap silently, mark Phase
1 active because the instruction said so, and quietly not mention the index.

Instead:

- **The roadmap was used as structural scaffolding and labelled owner-asserted, pending
  ratification** — in both repositories, in every phase document, and in two registers. No
  version number was invented, and no roadmap document was fabricated.
- **Phase 1 was recorded as *Owner Decision Required*, not *Active Execution*.** The scaffolding
  was built out completely so no work is lost, with every item marked `Evidence Needed`.
- **The legacy index was reconciled statement by statement** — seventeen of them — each with its
  current status and what replaced it. The original was left untouched.

The reasoning: recording Phase 1 as active without a phase-exit record would have been a
fabricated completion claim, which the project's own stop conditions treat as a hard block. An
instruction to record a state is not evidence of that state.

Two of the seventeen index statements turned out to be *inaccurate in the other direction* —
folders described as empty that were not, and a document count that was off by one. Those were
recorded too. The point of a reconciliation is accuracy, not vindication.

## Sanitization

The public repository carries conceptual zone names — Management, Server, Lab, Monitoring,
Storage, Remote Access — and no addresses, subnets, zone identifiers, hostnames, device
identifiers, rule exports, or vendor account references.

Whole source trees were excluded rather than filtered: the creator-media project, two separate
creator-platform codebases, a protected external repository, and a binary software cache of
roughly ten gigabytes.

## Security findings

A conservative pattern scan across fifteen credential classes found **no live-format credential**
in any file placed in either repository.

It did surface two open findings in the source workspace, both escalated rather than resolved:

- A **plaintext password-manager export** sitting unencrypted on disk. It was deliberately *not
  opened* — reading it would have printed credential values into a transcript, which is itself
  an exposure. Classification came from filename, extension, size, and location.
- A **prior audit's P0 token-rotation recommendation** from three months earlier, with **no
  record anywhere of whether the rotation happened.**

Neither blocked publication, since neither file is in either repository. Both were recorded as
owner actions.

## Implementation status

**Documented.** Both repositories were built, reviewed, and published. The rebuild is complete.

## Validation status

**Not confirmed.** Independent review is outstanding. Under this project's own rules, the
identity that performed work may not be its sole validator — which applies to this rebuild as
much as anything else.

## Lessons learned

**An instruction to record a state is not evidence of that state.** The most consequential
decision in the whole exercise was declining to mark a phase active because a task said it was.

**"Verify this against the controlling document" has a third answer.** Not just *matches* or
*differs* — sometimes *the controlling document does not exist*. That possibility is worth
planning for explicitly, because the natural response is to assume the search was inadequate.

**Not reading a file can be the correct handling.** For a suspected credential export, opening
it to confirm severity would create the exposure being assessed.

**Duplicating a controlling document is a governance failure, not thoroughness.** An existing
private repository already held the authoritative governance records. Copying them into a
second repository would have created a drift-prone second copy that could be mistaken for
authority. They were referenced instead.

**Excluding a whole tree beats filtering one.** For a creator-media project with hundreds of
files, a whole-tree exclusion is auditable in one line. A per-file filter is a maintenance
burden and a leak waiting to happen.

## Next phase

The rebuild produced five next actions, four of which are owner decisions: ratify or supply the
roadmap, resolve the phase state, review the credential export, close the outstanding
repository controls, and complete the independent validation that was already pending.

The repositories are infrastructure for the work. They are not the work.
