# Summoner Architecture Diagrams

**Status: Documented** — conceptual diagrams. **Nothing shown here is built.**

Last updated: 2026-08-07

---

## 1. Orchestration overview

```mermaid
flowchart TD
    H["Authorized Humans<br/><i>verified identity + role</i>"]
    S["SUMMONER<br/><b>Global AI Engineer</b><br/><i>no unrestricted credentials</i>"]

    F["Job & State Layer<br/><i>approvals · audit</i>"]
    T["Ticketing<br/><i>support record</i>"]
    P["Policy<br/><i>entitlement · disclosure</i>"]
    C["Context<br/><i>minimum necessary</i>"]

    PC["Project Controllers<br/><i>one per domain</i>"]
    SA["Specialist Agents<br/><i>one task, one domain</i>"]
    EX["Execution Systems<br/><i>workflow engines · APIs · code agents</i>"]
    AS["Approved Systems"]

    H --> S
    S --> F
    S --> T
    S --> P
    S --> C
    F --> PC
    P --> PC
    PC --> SA
    SA --> EX
    EX --> AS

    S -.->|"approval required"| H
```

## 2. Authority narrows at every tier

```mermaid
flowchart TD
    T0["<b>Authorized Humans</b><br/>broadest — accountable, identity-verified"]
    T1["<b>Summoner</b><br/>broad awareness · brokered access<br/>no unrestricted credentials"]
    T2["<b>Project Controllers</b><br/>single project"]
    T3["<b>Specialist Agents</b><br/>single task · depth 1 · no descendants"]
    T4["<b>Execution Systems</b><br/>single action · scoped service account"]

    T0 --> T1 --> T2 --> T3 --> T4

    R1["Cross-project brokering:<br/><b>Summoner only</b>"]
    R2["No tier may widen its own scope,<br/>authority, credential scope,<br/>delegation depth, or stop controls"]

    T1 -.- R1
    T4 -.- R2
```

## 3. Awareness without access

```mermaid
sequenceDiagram
    participant U as Requester<br/>(Project A context)
    participant S as Summoner
    participant P as Policy
    participant B as Project B

    U->>S: question about a Project B system
    S->>S: identify owning domain
    S->>P: identity · role · domain · action · risk
    P-->>S: permitted — sanitized detail
    S->>B: query via Project B scoped identity
    B-->>S: status
    S-->>U: sanitized summary
    Note over U: The requester receives the answer.<br/>The requester's context does NOT<br/>receive Project B access.
```

## 4. Continuity — normal vs degraded

```mermaid
flowchart LR
    subgraph N["Normal"]
        direction TB
        H1["Humans"] --> S1["Summoner"] --> A1["Agents · State layer · Workflows"]
    end

    subgraph D["Summoner unavailable"]
        direction TB
        H2["Humans"] --> R2["Ticketing · State layer · Monitoring"] --> M2["Manual procedures · Approved tools"]
    end

    N -.->|"Summoner lost"| D
```

**The path does not break — it shortens.** Humans reach the systems of record directly.

## 5. Autonomy promotion

```mermaid
flowchart TD
    CAP["Candidate capability"] --> G{"All 12 requirements met?"}
    G -->|no| STAY["Remains approval-required"]
    G -->|yes| OWN{"Recorded promotion<br/>decision?"}
    OWN -->|no| STAY
    OWN -->|yes| AUTO["Autonomous —<br/>this capability only"]
    AUTO --> W{"Threshold breach or<br/>stop condition?"}
    W -->|yes| SUSP["Automatic suspension"]
    SUSP --> INV["Investigate + remediate"]
    INV --> G
    W -->|no| AUTO

    NEVER["<b>Never autonomous</b><br/>legal · financial · destructive<br/>incident declaration · public<br/>access control · self-modification"]
```

**No capability has entered this flow.**

## What these diagrams omit

Internal component names, credential-store relationships, the ticket-system integration detail,
support-investigation internals, project and customer names, and every implementation
specific.

The architecture should be legible without them — and their absence is the point.

## Current status

Nothing depicted is implemented. Authority level **0**, promotion tests **0 of 15**, agents
**0**, autonomous capabilities **0**.
