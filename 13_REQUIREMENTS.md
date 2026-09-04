# AI Masterpiece — Requirements

## 1. Behaviour / Apprentice Model

- Adaptive operating mode: answer, research, ask, collaborate or work autonomously according to task uncertainty, risk, effort and explicit authorisation.
- Never knowingly guess.
- Research when research can resolve uncertainty.
- Ask when the answer depends on user-only information or research remains insufficient.
- Explicit user corrections override AI assumptions.

## 2. PC Management

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

**Nothing changes on the PC without explicit user approval.** Inspect, recommendation and execution are separate boundaries.

## 3. Files / Projects

An authorised project folder is a permission boundary. Authority inherits through contained files and subfolders unless explicitly protected. New contents inherit the project policy. Secrets remain separately controlled. Filesystem authority does not imply network authority.

## 4. Security / Permissions

- Least privilege.
- Security enforcement independent from the AI.
- Capability does not equal permission.
- AI may request permission but cannot grant itself permission.
- Higher-risk actions require explicit approval and stronger controls.
- Temporary permissions are task-scoped, resource/action limited, logged and automatically expire when the task ends.
- Protected areas and secrets require separate safeguards.
- Untrusted web/document/file instructions are data, not authority.
- Important security and permission events are auditable.

## 5. External / Network

Initial AI inference is local-only. External access is a separate capability and risk boundary.

Initial autonomous external actions are prohibited, including file/user-data uploads, external data transmission, form submission, external logins and transactions.

When web access is enabled, destination/tool controls and permissions must apply.

## 6. Downloads / Execution

- AI may find and explain useful files and provide their source.
- Downloads require explicit user permission.
- Download permission does not imply execution permission.
- Downloaded executables/scripts/installers must never execute automatically.
- Execution requires a separate explicit user command.

## 7. Memory / Second Mind

The system requires:

- raw historical archive
- active knowledge
- personal memory
- general knowledge
- project knowledge
- entities/concepts
- relationships
- selective retrieval
- Inbox/review

The user retains ultimate authority over persistent memory. The system must support inspection, editing, correction, deletion, reorganisation and approval/rejection of uncertain information.

Memory must preserve provenance, confidence, importance, freshness where relevant and history. Stale does not mean false. Forgotten information is excluded from normal retrieval. Low-risk organisation may be autonomous; semantic meaning must not be silently changed.

## 8. Research / Learning

The system should process authorised books, PDFs, videos, papers, GitHub repositories, courses, notes and documents. It should extract useful information, concepts, entities and relationships while preserving provenance and distinguishing source fact from inference.

Research records should retain source, date, verification/freshness, confidence, importance and reverification policy.

Evidence should be evaluated on authority, evidence quality, first-hand experience, relevance, recency, independence, conflicts, transparency and corroboration. Conflicting credible evidence should be preserved and explained when unresolved.

When a conclusion changes, preserve the old conclusion historically and record the new conclusion, change, date, reason and evidence.

## 9. Persistent Decision History

Important decisions retain what was decided, why, alternatives, research, experiments/benchmarks, consequences, date/context and conditions for revisiting.

## 10. Recovery

Data, configuration, memory and project knowledge must remain recoverable without the AI. Backups, restore procedures, configuration copies and logs are required.

## 11. Automation

Scheduled/background work may exist where explicitly authorised. It may organise, verify, index and flag information, but must not bypass security or silently perform consequential external actions.

## 12. Architecture Constraints

The conceptual Boss → Router → Workers → Tools/MCP/Skills → Memory architecture is a hypothesis, not a final implementation requirement.

Components should be replaceable, data portable and interfaces decoupled. Complexity must be justified by measurable benefit.

## 13. Phase 0 Status

Requirements for memory, Second Mind, research behaviour and core security boundaries are substantially established in the supplied project record.

Remaining Phase 0 work should focus on implementation research: OS, runtime, models, orchestration, storage, tool architecture, security implementation and benchmark design.

These requirements constrain technology selection but do not prematurely select the stack.
