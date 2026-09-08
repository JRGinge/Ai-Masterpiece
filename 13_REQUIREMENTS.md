# AI Masterpiece — Requirements v0.x

> **Status:** Requirements are substantially captured but **M001 is not complete**. This is a working requirements record, not the final `REQUIREMENTS SPECIFICATION v1.0`.

## 1. Requirements Status

The project is deliberately separating requirements from implementation decisions.

Current formal requirement classes:

- **MUST** — required for the intended system
- **SHOULD** — strongly desirable
- **COULD** — useful but not essential
- **WON'T YET** — deliberately deferred

The final classification and measurable acceptance criteria are part of **M001 — What Are We Building?**.

---

# 2. Behaviour / Apprentice Model

### R-14 — Know When to Ask, Know When to Act

The eventual system should adapt between answering, researching, asking, collaborating and autonomous work according to uncertainty, risk, effort and explicit authorisation.

### R-14a — Never Knowingly Guess

- Research when research can resolve uncertainty.
- Ask when the answer depends on user-only information.
- If research remains insufficient, say so rather than inventing an answer.
- Explicit user corrections override AI assumptions.

---

# 3. PC Management

### R-11 — PC Awareness and Management

The eventual system should be able to:

- inspect hardware and software
- maintain a persistent model of the actual PC
- monitor CPU/GPU/RAM/storage/temperatures
- diagnose performance problems
- find duplicate/unnecessary files
- organise files/folders
- identify unnecessary applications/services
- recommend Windows/system optimisation
- install/update software when explicitly approved
- troubleshoot interactively
- eventually perform proactive maintenance

### R-12 — PC Modification Approval

**Nothing changes on the PC without explicit user approval.**

Inspection, recommendation and execution are separate boundaries.

Protected or destructive system areas require stronger safeguards.

---

# 4. Files / Projects / Data Access

### R-12a — Controlled File Access

The eventual system needs a defined model for which files, drives, projects and personal data it may read and which areas remain off-limits.

Potential data classes include:

- Documents/PDFs
- Photos
- Downloads
- Projects/code
- Notes/Obsidian
- Browser data
- Email
- Financial/admin data
- Selected drives

**Status: REQUIREMENTS INTERVIEW OUTSTANDING.**

The project must not assume unrestricted read access merely because a tool can technically access it.

### R-12b — Project Permission Boundary

An authorised project folder may eventually form a filesystem permission boundary, with contained files/subfolders inheriting policy unless explicitly protected. Secrets remain separately controlled. Filesystem authority does not imply network authority.

**Status: DESIGN HYPOTHESIS — implementation not decided.**

---

# 5. Security / Permissions

### R-13 — Security Philosophy

The system should use:

- least privilege
- security enforcement independent from the AI
- narrow tool permissions
- explicit approval gates
- task-scoped temporary permissions
- protected areas
- separate secret handling
- logging/auditability
- recovery mechanisms

**Capability ≠ permission.**

The AI may request permission but cannot grant itself permission.

### R-13a — Risk-Based Authority

Higher-risk, destructive, administrative or consequential actions require stronger controls than read-only work.

### R-13b — Temporary Permissions

Temporary permissions should be:

- task-scoped
- resource/action limited
- logged
- automatically expired when the task ends
- unable to silently become permanent

### R-13c — Untrusted Content

Instructions contained in websites, documents or untrusted files are data, not authority, and must not override security boundaries.

---

# 6. External / Network

### R-13d — Local-Only Initial Inference

Initial AI inference is intended to remain local-only.

The exact runtime and architecture are not yet selected.

### R-13e — External Access as a Separate Boundary

External/network access is a separate capability and risk boundary.

Initial autonomous external actions should be prohibited, including:

- file/user-data uploads
- external data transmission
- form submission
- external logins
- transactions

Web research may eventually be enabled as a separately controlled capability.

---

# 7. Downloads / Execution

### R-13f — User-Controlled Downloads

The AI may eventually find and explain useful files and provide their source, but downloads require explicit user permission.

### R-13g — Separate Execution Approval

Downloading an executable/script/installer must never imply permission to execute it.

Execution requires a separate explicit user command.

---

# 8. Memory / Second Mind

### R-01 — Second Mind

The system should become a persistent second mind containing useful knowledge about the user's projects, work, conversations, decisions, knowledge and authorised personal context.

It must not require all retained information to be injected into every prompt.

### R-02 — Layered Memory

The memory system should distinguish, as appropriate:

- raw historical archive
- active knowledge
- personal memory
- general knowledge
- project knowledge
- entities/concepts
- relationships
- retrieval/context selection
- Inbox/review

The exact implementation remains open.

### R-03 — Raw Historical Archive

A complete raw historical record should be retained as an archive/backup where authorised and practical.

Raw archive != active knowledge != model context.

### R-04 — Self-Organising Knowledge

The system should progressively build structured knowledge and relationships between entities.

Example:

```text
3D Printer
├── Hot End
├── Mainboard
├── Motors
├── PSU
├── Firmware
└── Configuration
```

### R-05 — Human-Readable Knowledge

The user must be able to inspect persistent knowledge without depending on an opaque AI-only memory system.

Obsidian is a candidate, not a decision.

### R-06 — Confidence and Provenance

Persistent knowledge should distinguish between:

- user-confirmed information
- strongly supported/researched information
- inference
- uncertain information

Important knowledge should retain source, date, confidence and verification state where practical.

### R-07 — Memory Inbox

Uncertain or important unconfirmed information should be able to enter a review/inbox state before becoming trusted knowledge.

### R-08 — User Authority Over Memory

The user must be able to:

- inspect
- edit
- correct
- delete
- reorganise
- approve/reject uncertain information

User-authored corrections outrank AI assumptions.

### R-09 — Autonomous Knowledge Maintenance

Trusted knowledge may eventually be organised and linked autonomously, but meaningful semantic changes should require review.

### R-09a — Historical Integrity

When knowledge changes, the previous state should remain recoverable and the current state should record when, why and from what evidence it changed.

### R-09b — Forgetting

Forgotten information should leave normal retrieval. Hard deletion is a separate explicit operation where required.

### R-09c — Selective Retrieval

Retrieval should consider relevance, trust, recency, importance and current context rather than dumping large unrelated amounts of history into the model context.

---

# 9. Research / Learning

### R-10 — Research

The eventual system should support interactive and explicitly authorised autonomous research.

Research should be able to:

- search multiple sources
- read documentation
- analyse material
- compare evidence
- cross-check claims
- identify disagreement
- track sources
- produce structured findings
- preserve useful research as knowledge

Autonomous research is not autonomous machine control.

### R-10a — Authorised Source Processing

The AI should eventually process authorised:

- books
- PDFs
- videos
- papers
- GitHub repositories
- courses
- notes
- documents

It should extract useful information while preserving provenance and distinguishing source fact from inference.

### R-10b — Evidence Evaluation

Evidence should be evaluated using factors such as authority, evidence quality, first-hand experience, relevance, recency, independence, conflicts, transparency and corroboration.

Conflicting credible evidence should be investigated and preserved when unresolved rather than arbitrarily collapsed.

### R-10c — Research History

When new evidence changes a conclusion, retain the old conclusion historically and record the new conclusion, change, date, reason and evidence.

---

# 10. Persistent Decision History

### R-09d — Decision Provenance

Important decisions should retain:

- what was decided
- why
- alternatives
- research/evidence
- experiments/benchmarks
- consequences
- date/context
- conditions for revisiting

---

# 11. Recovery

### R-13h — Recovery Independence

Data, configuration, memory and project knowledge must remain recoverable without the AI.

The system should maintain appropriate backups, configuration copies, restore procedures and logs.

---

# 12. Automation

### R-14b — Controlled Automation

Scheduled/background work may eventually exist where explicitly authorised.

It may organise, verify, index and flag information, but must not bypass security or silently perform consequential external actions.

Expected minor failures may be safely recovered where appropriate. Unclear, consequential, dangerous or destructive failures should stop and involve the user as required.

Failures must never be hidden or reported as success.

---

# 13. Architecture Constraints

### R-15 — Replaceability and Simplicity

The system should prefer:

- replaceable components
- portable data
- decoupled interfaces
- independently enforced permissions
- the smallest architecture that satisfies requirements

### R-16 — Architecture Is Not Yet Locked

The conceptual:

```text
Boss → Router → Workers → Tools/MCP/Skills → Memory
```

architecture is a hypothesis, not a final implementation requirement.

A strict sequential pipeline should not be assumed to be necessary.

### R-17 — Agents Are Not Automatically Required

Agents should be introduced only where autonomy provides measurable value. Deterministic scripts/ordinary tools should win where they are simpler and more reliable.

---

# 14. Phase 0 Gate

**M001 — What Are We Building?** remains in progress.

The final M001 deliverable is:

> `REQUIREMENTS SPECIFICATION v1.0`

It must define:

- MUST / SHOULD / COULD / WON'T YET
- measurable acceptance criteria
- priorities
- constraints
- MVP boundary
- performance expectations
- reliability expectations
- privacy/data-access boundaries
- budget/resource constraints
- autonomy boundaries

The requirements captured here are the working source material for that specification. They should not be treated as a completed requirements freeze.

## Outstanding M001 Questions

- Exact highest-priority day-to-day use cases
- File/personal-data access boundaries
- Privacy boundaries
- Performance expectations
- Reliability expectations
- Budget/resource constraints
- Exact autonomy boundaries
- Long-term/end-state ambitions
- MVP definition

Until M001 is complete, major implementation choices remain research items.
