# AI Masterpiece — Decision & Evidence Log

> This file records proposed decisions, source-derived constraints and decisions that have actually been accepted.
>
> **Critical rule:** appearing in this log does not automatically make an item a final technical decision.

## Decision Record

For significant decisions record:

- ID
- Date/context
- Requirement(s)
- Decision/proposal
- Status
- Why
- Alternatives considered
- Research/evidence
- Experiments/benchmarks
- Consequences
- Revisit conditions

## Accepted Decision

### D001 — Existing Hardware First

**Status: DECIDED**

Use the current PC as the starting platform:

- CPU: AMD Ryzen 5 5600X
- GPU: NVIDIA RTX 3070
- Motherboard: ASUS TUF B450-Plus Gaming

Upgrade only when measured workload limitations demonstrate that an upgrade solves a real requirement.

---

# Source-Derived Requirements / Constraints

The following were established during the requirements work but are **not implementation decisions**. They constrain later technology selection and architecture research.

### C001 — Incremental Build
Build in phases and prove each layer before adding unnecessary complexity.

### C002 — Portable Data
Prefer human-readable and portable formats where practical.

### C003 — Local-Only Initial AI
Initial AI inference is intended to remain on local hardware. The exact runtime and model are not yet selected.

### C004 — Explicit Execution Authority
The AI must not execute consequential actions merely because it believes they are useful. Explicit user authority is required.

### C005 — Adaptive Permissions
Permissions should be scoped to risk and task. Higher-risk or external actions require stronger controls.

### C006 — Project Permission Boundary
An authorised project folder is a candidate filesystem permission boundary. Permissions may inherit through contained files/subfolders unless explicitly protected. Network access remains separate. Secrets remain separately controlled.

**Status: REQUIREMENT / DESIGN CONSTRAINT — implementation not decided.**

### C007 — No Autonomous Uploads Initially
Initial autonomous uploads, external data transmission, form submission, external logins and transactions are prohibited.

### C008 — User-Controlled Downloads
Downloads require explicit user permission.

### C009 — Separate Execution Approval
Download approval never implies execution approval. Execution requires a separate explicit user command.

### C010 — Task-Scoped Temporary Permissions
Temporary permissions should expire when the authorised task finishes, be resource/action scoped and be logged.

### C011 — No Self-Granted Permissions
Neither the AI nor a security agent may grant itself additional authority. The user remains the final authority.

### C012 — User Authority Over Memory
The user must be able to inspect, edit, correct, delete and reorganise persistent memory. User corrections outrank AI assumptions.

### C013 — Raw Archive + Active Knowledge
Historical records should be preserved while active knowledge can evolve without silently destroying history.

### C014 — Apprentice Behaviour
If the AI does not know, it should research when appropriate; if uncertainty remains, it should ask or say it does not know. It must never knowingly guess.

### C015 — Explicit Correction & Error Learning
User corrections override AI assumptions. Important corrections should update current knowledge, preserve useful history and trigger checks of related knowledge where necessary.

### C016 — Persistent Decision History
Important decisions should retain what was decided, why, alternatives, research, experiments, consequences, date/context and revisit conditions.

### C017 — Authorised-Source Learning
The AI may eventually process authorised books, PDFs, videos, papers, GitHub repositories, courses, notes and documents while preserving provenance, distinguishing source fact from inference and flagging uncertainty.

### C018 — Evidence-Based Research Evaluation
Research should evaluate actual evidence using factors such as authority, evidence quality, first-hand experience, relevance, recency, independence, conflicts, transparency and corroboration.

### C019 — Preserve Conflicting Credible Evidence
When credible sources disagree, investigate the conditions and evidence. If unresolved, preserve both claims and explain the dispute rather than arbitrarily selecting a winner.

### C020 — Confidence-Based Research Conclusions
High-confidence research may become current knowledge. Uncertain, conflicting or important unresolved conclusions should go through review rather than silently becoming fact.

### C021 — Evolving Research Conclusions
When evidence changes a conclusion, retain the old conclusion as historical and record the new current conclusion, change, date, reason and supporting evidence.

### C022 — Contextual Memory Retrieval
Retrieval should consider relevance, trust, recency, importance and current context. Linked knowledge should reduce unnecessary context stuffing.

### C023 — Deduplication With Provenance
Consolidate genuine duplicates while preserving provenance and meaningful differences between distinct claims.

### C024 — Low-Risk Automatic Organisation
Trusted knowledge may eventually be organised automatically, but changes to factual meaning, confidence, interpretation, important relationships or conclusions require review.

### C025 — Comprehensive Personal Representation
The system should eventually maintain a comprehensive authorised representation of relevant personal information while retrieving it selectively.

### C026 — Adaptive Personal Learning
The AI may learn from authorised interactions/sources, but uncertain personal facts require confirmation rather than silent assumption.

### C027 — Memory Transparency
The user should be able to inspect memory details, provenance, confidence, importance, status and history when requested.

### C028 — Selective Freshness
Actively track freshness for information likely to change. Stale information is not automatically false; historical knowledge remains available.

### C029 — Audited Time-Aware Memory
When knowledge changes, preserve the previous state and record the new state, date, reason, source and history.

### C030 — Soft Deletion / Forgetting
Forgotten information should leave normal retrieval while historical/audit information may remain unless explicit hard deletion is required.

### C031 — Adaptive Knowledge Organisation
Trusted knowledge may be organised and linked automatically; uncertain or materially meaning-changing relationships should go to review.

### C032 — PC Management With Explicit Approval
The eventual AI may inspect, monitor, diagnose, organise and recommend PC changes and eventually perform approved maintenance. Nothing changes on the PC without explicit user approval.

### C033 — Recovery Independence
The AI must never be the root of control or the sole means of recovering the machine, data or configuration.

---

# Decision Status Rule

A proposal becomes an implementation decision only after:

1. The relevant requirement is understood.
2. Appropriate research/evidence is gathered.
3. Alternatives are compared where applicable.
4. A recommendation is made.
5. The user explicitly accepts the recommendation.
6. The decision is documented.

Therefore, during **Phase 0**, most entries above remain **requirements/constraints**, not locked technology choices.

The current technical decision set is intentionally minimal: **existing hardware first**.
