# Research 01 — Research Centre Setup

## Processing status

**Partial — consolidated-source extraction**

This note captures the Research Centre themes that are supported by the consolidated project master/context currently available. It is **not** a claim that the complete original chat transcript has been reviewed.

## Purpose of the research

Establish the project's requirements, operating principles, control model, security posture and approach to turning research into durable project knowledge before implementation begins.

## Findings / established direction

### 1. Build philosophy

- The system should be built incrementally.
- Existing hardware should be used before major upgrades are considered.
- Unnecessary infrastructure and complexity should be avoided.
- Decisions should be evidence-driven and current information should be researched rather than guessed.
- Facts, assumptions and recommendations should remain distinguishable.
- The smallest system that solves the current problem is preferred.

**State:** Confirmed project direction.

### 2. Local-first operation

- The project is local-first and privacy-conscious.
- Initial operation is intended to remain local.
- Portability of data and replaceability of components are important architectural goals.

**State:** Confirmed direction.

### 3. AI architecture direction

The intended conceptual architecture contains a central Boss/Personal AI, with possible model routing, specialist workers, tools/MCP/skills and a separate memory/knowledge layer.

The architecture is a **working hypothesis**, not a locked implementation requirement.

**State:** Provisional architecture.

### 4. Control and execution

- The AI must not execute actions merely because it has identified an action to perform.
- Consequential or higher-risk actions require explicit user permission.
- Tool access should be scoped rather than unrestricted.
- Project-folder permissions can inherit to the contents of that folder where explicitly granted.
- Secrets remain separately controlled.
- Autonomous uploads are not currently permitted.

**State:** Confirmed control direction.

### 5. Adaptive permission model

The security model should adapt to risk.

A useful working permission scale is:

- Level 0 — no external action
- Level 1 — read-only
- Level 2 — create/modify non-critical data
- Level 3 — external or consequential actions require approval
- Level 4 — high-risk administrative actions; avoid by default

The project favours stronger security appraisal before expanding control into higher-risk or external operations.

**State:** Confirmed direction; implementation details remain open.

### 6. Security principles

The AI tool layer is treated as an attack surface.

Required principles include:

- least privilege
- explicit permissions
- separation of read/write access where practical
- sandboxing for untrusted code
- network restrictions where appropriate
- logging
- backups and recovery procedures
- approval gates for destructive or consequential actions
- protection of secrets outside prompts and ordinary notes
- treating instructions found in websites, documents and other untrusted content as untrusted data

**State:** Confirmed security direction.

### 7. Memory / second mind

The project should not simply store every conversation as memory.

Durable project knowledge should capture useful information such as:

- decisions
- constraints
- verified discoveries
- research findings
- build/test history
- reusable procedures
- unresolved questions

Knowledge should remain human-readable where practical, editable and deletable, with source/context retained. Uncertainty must not silently become fact.

The Second Mind should therefore be a **curated technical knowledge base**, not a raw chat archive.

**State:** Confirmed direction.

### 8. Research traceability

Research should retain enough provenance to allow the project to determine:

- what was researched
- where information came from
- what conclusion was reached
- what alternatives were considered
- what remains uncertain
- when information should be re-verified

This supports the project's periodic review/re-verification workflow.

**State:** Confirmed direction.

## Open questions

The consolidated material does not establish final decisions for:

- operating system
- local model runtime
- exact model lineup
- orchestration framework
- database/vector-store architecture
- final MCP/tool implementation
- initial agent set
- detailed memory implementation

These remain research/decision work rather than completed decisions.

## Important negative findings

The following should **not** be inferred from this source:

- No specific software stack is final.
- No specific model is final.
- No unrestricted computer control is approved.
- No autonomous external action is approved by default.
- The conceptual Boss/router/worker architecture is not yet proven necessary in full.

## Source limitation

This entry was produced from the consolidated project master material available to the assistant rather than the complete original Research Centre chat transcript. It should therefore remain marked **Partial** until the originating chat is directly available for review.

## Next processing step

When the original Research Centre conversation is available as a source, compare it against this note and:

1. extract any missing research findings;
2. identify explicit decisions and their reasoning;
3. record rejected alternatives where supported;
4. detect contradictions;
5. update canonical project documents;
6. mark this research item complete only after verification.
