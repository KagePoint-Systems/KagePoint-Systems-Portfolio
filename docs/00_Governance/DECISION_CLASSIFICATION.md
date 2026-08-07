# Decision Classification

**Status: Documented** - in active use.

Last updated: 2026-08-07

---

## The four classifications

Every decision carries exactly one. There is no "mostly decided".

### Locked

Approved and binding. Changing a Locked decision requires a new approved decision that
explicitly supersedes it and names what changed.

A Locked decision records: the decision, its rationale, its boundary (what it does *not*
cover), and who approved it.

### Draft

Proposed and recorded, but not binding. A Draft states **what validation it needs** to become
Locked. Drafts are safe to write and safe to disagree with - that is their purpose.

### Future-phase

Deliberately deferred, with a **named promotion gate**: the specific evidence required before
it is reconsidered. "Later" is not a gate. "After the integration passes read-only tests with
narrow scopes and complete audit logs" is.

### Rejected / superseded

Considered and declined, or replaced. Kept permanently **with the reason**.

This is the classification most often skipped and most often regretted. Without it, a rejected
option returns six months later with no record of why it was rejected, and the analysis is
redone from scratch - or worse, decided differently by accident.

## Boundaries are part of the decision

A decision without a boundary is an ambiguity waiting to be resolved by whoever is under the
most time pressure.

Example of a bounded decision: an operational identity is adopted, **and** the underlying
technical dependency name is explicitly retained in technical records - both correct, at
different layers, with the boundary written down so neither erodes the other.

## Supersession is partial by default

When a decision is superseded, **only the named field is superseded.** The rest of the original
stands, and the original text is retained as the approved record.

This prevents a small correction from silently invalidating an entire decision - and prevents
the opposite failure, where a superseded field keeps getting cited because the document still
looks current.

## What this repository can and cannot do

Public and Execution-stage repositories **cannot create a Locked decision.** Only owner approval
through Summary can.

Any decision recorded during ordinary work is **Draft** until it goes through that path,
regardless of how confident it is.
