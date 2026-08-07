# Document Lifecycle

**Status: Documented** - in active use.

Last updated: 2026-08-07

---

## States

| State | Meaning | Citable as authority? |
|---|---|---|
| **Execution Draft** | Being worked on | No |
| **Summary Candidate** | Submitted for validation | No |
| **Binder Candidate** | Validated, awaiting owner promotion | No |
| **Binder / Locked** | Approved source of truth | **Yes** |
| **Superseded** | Replaced; names its replacement | No - historical only |
| **Historical** | Preserved for provenance | No - historical only |
| **Rejected** | Considered and declined | No |

## Every document declares its own state

Documents carry an explicit header stating status, lifecycle, authority class, applicable
phase, implementation status, validation status, and - importantly - **whether the document
affects a phase gate**.

That last field exists because the most common documentation failure is not inaccuracy. It is
a reader assuming a document carries more authority than it does. Stating "does not approve a
phase transition" on the document itself removes the ambiguity at the point of reading.

## Maturity is separate from document state

Systems and evidence use a different vocabulary from documents:

**Planned -> Documented -> Implemented -> Tested -> Validated**

A document can be complete and well written while the thing it describes is only Planned. These
are independent axes, and conflating them is how a documentation set comes to imply
infrastructure that does not exist.

## Supersession procedure

1. Preserve a copy of the superseded document
2. State the controlling replacement **inside the superseded copy**
3. Record the supersession in the conflict register
4. Update the document register

**The superseded document is never deleted.** Deleting it removes the ability to understand why
the current version says what it says.

## Absence is recorded

A missing document is recorded as missing. An unverified control is recorded as unverified. An
unconfirmed action is recorded as unconfirmed.

`Evidence Needed`, `Owner Decision Required`, and `Not Yet Confirmed` are **valid terminal
states**, not placeholders to be tidied away.

A status table filled with assumptions looks complete and is actively misleading - worse than
an obviously incomplete one, because nobody goes looking for the gap.
