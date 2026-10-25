# AI Masterpiece 🧠⚙️

A local-first personal AI system designed to be useful, secure, reliable, maintainable and upgradeable.

## Current Status — 25 October 2026

**Project:** AI Masterpiece
**Current implementation track:** Vektor
**Overall state:** Phase 0 research/design; local inference prototype was previously verified, while the current OpenCode integration is awaiting re-verification
**Production status:** Not production-ready

The project has now crossed from pure planning into controlled implementation experiments. The first implementation milestone is the **Vektor Local Core**.

```text
VEKTOR
  ↓
OpenCode               [CURRENT AGENT HARNESS — INTEGRATION TO RE-VERIFY]
  ↓
llama.cpp              [INFERENCE ENGINE]
  ↓
Qwen 3.5 9B Q4_K_M    [CURRENT LOCAL MODEL]
```

Morphy is a GUI/control-room candidate under evaluation, not a locked component. Claude Code was superseded as the primary harness on 4 October 2026.

### Previously verified local inference prototype (1 October 2026; historical evidence)

- The earlier test recorded the llama.cpp executable and Qwen model file as present
- The earlier test recorded the API at `http://127.0.0.1:8080`, health success, and model ID `qwen3.5-9b`
- These observations are historical and have not been rechecked as part of this documentation update
- local inference was successfully exercised through the former Claude Code harness
- OpenCode is the accepted current harness, but its connection to the local endpoint must be re-verified

The local inference path was previously exercised, but current server state and OpenCode integration are **not freshly verified**. This is not a declaration that the wider Vektor system is complete.

## Current Technical Decisions

The following are locked as the current implementation baseline, subject to later evidence-based revision:

1. **Vektor** is the current system/runtime project name.
2. **OpenCode** is the current agent harness/control layer (decision accepted 4 October 2026; live integration still requires verification).
3. **llama.cpp** is the current local inference engine.
4. **Qwen 3.5 9B Q4_K_M** is the current local model.
5. The expected local inference endpoint is `http://127.0.0.1:8080`; confirm it during the next read-only runtime audit.
6. The live llama.cpp API is the runtime source of truth when verifying the active model/service.
7. **CLL is retired from the architecture**; it is not required for the current OpenCode → llama.cpp path.
8. The existing PC remains the starting hardware platform.

These decisions lock the **current prototype**, not every future subsystem. Memory, Obsidian, MCP, agents, routing, automation, voice, cloud split and advanced computer control remain separate design decisions.

## Vektor Operating Workflow

```text
INSPECT
   ↓
ANALYSE
   ↓
PROPOSE
   ↓
ASK APPROVAL
   ↓
EXECUTE
   ↓
VERIFY
```

The model cannot grant itself permissions. Capability and authority remain separate.

## Project Control

- **Trello** = project/task control and status
- **GitHub** = engineering record, code, decisions, experiments and implementation history
- **Obsidian** = planned human-readable knowledge/Second Mind layer

## Knowledge Flow

**RESEARCH → DECISION → BUILD → TEST → VERIFY → DOCUMENT**

## Next Milestone

### Vektor Milestone 01 — Stable Local Core

Remaining acceptance work:

- [ ] Verify OpenCode version, effective configuration, selected provider/model and connection to llama.cpp
- [ ] Final read-only Vektor Doctor
- [ ] Reproducible startup procedure
- [ ] Repeatable benchmark/verification record
- [ ] Runtime documentation committed
- [ ] Trello state reconciled with the implementation
- [ ] Evaluate Morphy as an optional GUI without treating it as selected until approved
- [ ] Confirm recovery/restart procedure

Only after this milestone should additional layers be added.

## Core Safety Principles

- **Capability ≠ permission.**
- The AI cannot grant itself authority.
- PC changes require explicit user approval.
- Downloads require permission.
- Execution requires a separate explicit command.
- Initial AI inference is local-only.
- External data transmission is restricted.
- Project-folder permissions may inherit; secrets remain separately protected.
- Temporary permissions expire with the authorised task.
- The AI must never knowingly guess.
- The system must remain recoverable without the AI.

## Repository Structure

- `00_PROJECT_MASTER.md` — governing state and principles
- `01_ROADMAP.md` — staged development plan
- `02_ARCHITECTURE.md` — current and future architecture
- `03_HARDWARE.md` — hardware baseline
- `04_MODELS.md` — model registry
- `05_MEMORY.md` — memory requirements
- `06_AGENTS.md` — agents/skills framework
- `07_MCP.md` — tools/MCP framework
- `08_SECURITY.md` — security requirements
- `09_AUTOMATION.md` — automation boundaries
- `10_SOFTWARE_STACK.md` — software decisions and candidates
- `11_BUILD_LOG.md` — implementation/test evidence
- `12_DECISION_LOG.md` — durable decisions
- `13_REQUIREMENTS.md` — requirements
- `14_SECOND_MIND.md` — Second Mind design
- `VEKTOR.md` — Vektor operating model and architecture
- `VEKTOR_RUNTIME.md` — exact local runtime record
- `research/` — source-derived research
- `experiments/` — reproducible tests/benchmarks
- `configs/` — configuration records
- `backups/` — backup/recovery documentation
