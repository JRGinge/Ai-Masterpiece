# AI Masterpiece — Decision & Evidence Log

> This file records durable project decisions, source-derived constraints, experiments and their evidence.
>
> A technical choice is locked only for the scope explicitly stated in its decision record. Future evidence may justify a new decision and should preserve the old record.

## Decision Record Format

For significant decisions record:

- ID
- Date/context
- Requirement(s)
- Decision/proposal
- Scope
- Status
- Why
- Alternatives considered
- Research/evidence
- Experiments/benchmarks
- Consequences
- Revisit conditions

---

## Accepted Decisions

### D001 — Existing Hardware First

**Status: DECIDED**

Use the current PC as the starting platform:

- CPU: AMD Ryzen 5 5600X
- GPU: NVIDIA RTX 3070
- Motherboard: ASUS TUF B450-Plus Gaming

Upgrade only when measured workload limitations demonstrate that an upgrade solves a real requirement.

---

### D002 — Vektor Is the Current Runtime Project Name

**Date:** 2026-09-28 onward

**Status: DECIDED — CURRENT BASELINE**

The active local AI implementation track is named **Vektor**.

The previous Bionic/AI Masterpiece naming remains historical project context; Vektor is the current runtime/system name.

---

### D003 — Claude Code Is the Current Harness

**Status: DECIDED — CURRENT PROTOTYPE**

Claude Code is the control/harness layer used to interact with the local model runtime.

This does not lock Claude Code as the permanent end-state orchestration architecture. It locks its role in the current Vektor prototype.

---

### D004 — llama.cpp Is the Current Local Inference Engine

**Status: DECIDED — CURRENT PROTOTYPE**

llama.cpp is the current local inference engine/server for Vektor.

Current endpoint:

`http://127.0.0.1:8080`

The live API is the source of truth for active runtime verification.

Alternatives such as Ollama, vLLM and other runtimes remain future research options rather than current components.

---

### D005 — Qwen 3.5 9B Q4_K_M Is the Current Local Model

**Status: DECIDED — CURRENT PROTOTYPE**

Qwen 3.5 9B Q4_K_M is the current local Vektor model.

Observed API model ID:

`qwen3.5-9b`

The model has been loaded and exercised through llama.cpp and reached through the Claude Code harness.

This is a current prototype selection, not a claim that it is the permanent or only model Vektor will ever use.

---

### D006 — Direct Claude Code → llama.cpp Path

**Status: DECIDED — CURRENT PROTOTYPE**

The current runtime does not require `cll.exe` or a separate CLL layer.

The architecture is:

```text
Claude Code → llama.cpp API → Qwen 3.5 9B
```

The earlier CLL-based setup is retained as historical troubleshooting context and is considered retired.

---

### D007 — Read-Only Vektor Doctor

**Status: DECIDED — IMPLEMENTATION REQUIRED**

The runtime doctor must inspect and report state without modifying existing files, configuration or runtime decisions.

It should verify at minimum:

- expected executables
- expected model file
- server/port
- API health
- active model ID
- expected model match
- basic runtime identity

---

# Source-Derived Requirements / Constraints

### C001 — Incremental Build
Build in phases and prove each layer before adding unnecessary complexity.

### C002 — Portable Data
Prefer human-readable and portable formats where practical.

### C003 — Local-Only Initial AI
Initial AI inference is intended to remain on local hardware.

### C004 — Explicit Execution Authority
The AI must not execute consequential actions merely because it believes they are useful. Explicit user authority is required.

### C005 — Adaptive Permissions
Permissions should be scoped to risk and task. Higher-risk or external actions require stronger controls.

### C006 — Project Permission Boundary
An authorised project folder is a candidate filesystem permission boundary. Network access remains separate. Secrets remain separately controlled.

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
The AI may eventually process authorised books, PDFs, videos, papers, GitHub repositories, courses, notes and documents while preserving provenance and uncertainty.

### C018 — Evidence-Based Research Evaluation
Research should evaluate evidence using authority, quality, relevance, recency, independence, conflicts, transparency and corroboration.

### C019 — Preserve Conflicting Credible Evidence
When credible sources disagree, investigate the conditions and evidence. If unresolved, preserve the dispute rather than arbitrarily selecting a winner.

### C020 — Confidence-Based Research Conclusions
High-confidence research may become current knowledge. Uncertain, conflicting or important unresolved conclusions should go through review.

### C021 — Evolving Research Conclusions
When evidence changes a conclusion, retain the old conclusion as historical and record the new current conclusion, date, reason and evidence.

### C022 — Contextual Memory Retrieval
Retrieval should consider relevance, trust, recency, importance and current context.

### C023 — Deduplication With Provenance
Consolidate genuine duplicates while preserving provenance and meaningful differences.

### C024 — Low-Risk Automatic Organisation
Trusted knowledge may eventually be organised automatically, but changes to factual meaning or important conclusions require review.

### C025 — Comprehensive Personal Representation
The system should eventually maintain a comprehensive authorised representation of relevant personal information while retrieving it selectively.

### C026 — Adaptive Personal Learning
The AI may learn from authorised interactions/sources, but uncertain personal facts require confirmation.

### C027 — Memory Transparency
The user should be able to inspect memory details, provenance, confidence, importance, status and history.

### C028 — Selective Freshness
Track freshness for information likely to change. Historical knowledge remains available.

### C029 — Audited Time-Aware Memory
When knowledge changes, preserve previous state and record new state, date, reason, source and history.

### C030 — Soft Deletion / Forgetting
Forgotten information should leave normal retrieval while historical/audit information may remain unless hard deletion is explicitly required.

### C031 — Adaptive Knowledge Organisation
Trusted knowledge may be organised and linked automatically; uncertain or materially meaning-changing relationships should go to review.

### C032 — PC Management With Explicit Approval
The eventual AI may inspect, monitor, diagnose, organise and recommend PC changes and eventually perform approved maintenance. Nothing changes on the PC without explicit user approval.

### C033 — Recovery Independence
The AI must never be the root of control or the sole means of recovering the machine, data or configuration.

---

## Decision State Rule

A future major technical choice becomes an implementation decision only after:

1. The relevant requirement is understood.
2. Appropriate research/evidence is gathered.
3. Alternatives are compared where applicable.
4. A recommendation is made.
5. The user explicitly accepts the recommendation.
6. The decision is documented.

The Vektor core is now an exception only in the sense that the user has explicitly accepted the tested prototype choices after hands-on experimentation. The choices remain scoped to the current implementation baseline and can be superseded by a new documented decision.
