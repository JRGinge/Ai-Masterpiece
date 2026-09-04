# AI Masterpiece — Decision Log

Important decisions must retain context and remain revisitable when their assumptions change.

## Decision Record

- ID
- Date/context
- Decision
- Status
- Why
- Alternatives considered
- Research/evidence
- Experiments/benchmarks
- Consequences
- Revisit conditions

## Established Decisions

### D001 — Existing Hardware First
Use the current PC initially. Upgrade only when measured workload limitations justify it.

### D002 — Incremental Build
Build in phases and prove each layer before adding unnecessary complexity.

### D003 — Portable Data
Prefer human-readable and portable formats where practical.

### D004 — Local-Only Initial AI — M001-LOC-01
Initial AI inference remains on local hardware. No cloud LLM fallback initially. This can be revisited later if a compelling requirement emerges.

### D005 — Explicit Execution Authority
The AI never executes consequential actions merely because it believes they are useful. Explicit user authority is required.

### D006 — Adaptive Permissions
Permissions are scoped to risk and task. Higher-risk or external actions require stronger controls.

### D007 — Project Permission Inheritance — M002-SEC-33
An authorised project folder is the filesystem permission boundary. Permissions inherit through contained files/subfolders unless explicitly protected. Network access remains separate. Secrets remain separately controlled.

### D008 — No Autonomous Uploads Initially — M002-SEC-14
The initial system does not independently upload files/user data, submit forms, log in externally or transact.

### D009 — User-Controlled Downloads — M002-SEC-15
Downloads require explicit user permission.

### D010 — Separate Execution Approval — M002-SEC-16
Download approval never implies execution approval. The user must explicitly command execution.

### D011 — Task-Scoped Temporary Permissions — M002-SEC-32
Temporary permissions expire when the authorised task finishes, are resource/action scoped and are logged.

### D012 — No Self-Granted Permissions — M002-SEC-31
Neither the AI nor the security agent can grant itself additional authority. The user is the final authority.

### D013 — User Authority Over Memory — M001-MEM-02
The user can inspect, edit, correct, delete and reorganise persistent memory. User corrections outrank AI assumptions.

### D014 — Raw Archive + Active Knowledge — M001-MEM-14
Historical records are preserved while active knowledge can evolve without silently destroying history.

### D015 — Apprentice Behaviour — M001-TRUST-01
If the AI does not know, it researches when appropriate; if still uncertain, it asks or says it does not know. It never knowingly guesses.

### D016 — Explicit Correction & Error Learning — M001-TRUST-02
User corrections override AI assumptions. Important corrections update current knowledge, preserve useful history and trigger checks of related knowledge where necessary.

### D017 — Persistent Decision History — M001-DECISION-01
Important decisions retain what, why, alternatives, research, experiments, consequences, date/context and revisit conditions.

### D018 — Authorised-Source Learning — M001-KNOWLEDGE-01
The AI may learn from authorised books, PDFs, videos, papers, GitHub repositories, courses, notes and documents while preserving provenance, distinguishing source fact from inference and flagging uncertainty.

### D019 — Evidence-Based Research Evaluation — M001-RES-02
Evaluate actual evidence using authority, evidence quality, first-hand experience, relevance, recency, independence, conflicts, transparency and corroboration rather than assuming source categories are automatically equal.

### D020 — Preserve Conflicting Credible Evidence — M001-RES-03
When credible sources disagree, investigate the conditions and evidence. If unresolved, preserve both claims and explain the dispute rather than arbitrarily selecting a winner.

### D021 — Confidence-Based Research Conclusions — M001-RES-04
High-confidence research can become current knowledge. Uncertain, conflicting or important unresolved conclusions go through Inbox/review rather than silently becoming fact.

### D022 — Evolving Research Conclusions — M001-RES-05
When evidence changes a conclusion, retain the old conclusion as historical and record the new current conclusion, change, date, reason and supporting evidence.

### D023 — Contextual Memory Retrieval — M001-MEM-07
Retrieval considers relevance, trust, recency, importance and current context. Linked knowledge should reduce unnecessary context stuffing.

### D024 — Deduplication With Provenance — M001-MEM-17
Consolidate genuine duplicates while preserving provenance and meaningful differences between distinct claims.

### D025 — Low-Risk Automatic Consolidation — M001-MEM-18
The AI may autonomously organise trusted knowledge, but changes to factual meaning, confidence, interpretation, important relationships or conclusions require review.

### D026 — Comprehensive Personal Representation — M001-PERSONAL-01
The AI should eventually maintain a comprehensive authorised representation of the user while retrieving personal information selectively.

### D027 — Adaptive Personal Learning — M001-PERSONAL-02
The AI may learn from authorised interactions/sources, but uncertain personal facts require confirmation rather than silent assumption.

### D028 — Memory Transparency — M001-MEM-16
The user should be able to inspect memory details, provenance, confidence, importance, status and history when requested.

### D029 — Selective Freshness — M001-MEM-10
Actively track freshness for information likely to change. Stale information is not automatically false; historical knowledge remains available.

### D030 — Audited Time-Aware Memory — M001-MEM-03
When knowledge changes, preserve the previous state and record the new state, date, reason, source and history.

### D031 — Soft Deletion / Forgetting — M001-MEM-04
Forgotten information leaves normal retrieval but may remain in the historical/audit layer unless explicitly hard-deleted.

### D032 — Adaptive Knowledge Organisation — M001-MEM-06
Trusted knowledge can be organised and linked automatically; uncertain or materially meaning-changing relationships go to review.

### D033 — PC Management With Explicit Approval — M001-PC
The eventual AI may inspect, monitor, diagnose, organise and recommend PC changes and eventually perform approved maintenance. Nothing changes on the PC without explicit user approval.

### D034 — Recovery Independence
The AI must never be the root of control or the sole means of recovering the machine, data or configuration.

## Decision Status Rule

These decisions are source-derived project requirements. Implementation choices remain open until separately researched, compared and explicitly promoted to implementation decisions.
