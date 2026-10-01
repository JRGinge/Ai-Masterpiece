# AI Masterpiece 🧠⚙️

A local-first personal AI system designed to be useful, secure, reliable, maintainable and upgradeable.

## Current Status — 1 October 2026

**Project:** AI Masterpiece
**Current implementation track:** Vektor
**Overall state:** Phase 0 research/design with a verified local-runtime prototype
**Production status:** Not production-ready

The project has now crossed from pure planning into controlled implementation experiments. The first implementation milestone is the **Vektor Local Core**.

```text
VEKTOR
  ↓
Claude Code            [HARNESS]
  ↓
llama.cpp              [INFERENCE ENGINE]
  ↓
Qwen 3.5 9B Q4_K_M    [CURRENT LOCAL MODEL]
```

### Verified prototype

- llama.cpp executable present and runnable
- Qwen 3.5 9B Q4_K_M model present
- llama.cpp API running on `http://127.0.0.1:8080`
- health endpoint verified
- OpenAI-compatible model endpoint verified
- model ID observed as `qwen3.5-9b`
- Claude Code connected to the local endpoint
- local inference successfully exercised

This is a **verified prototype**, not a declaration that the whole Vektor system is complete.

## Current Technical Decisions

The following are locked as the current implementation baseline, subject to later evidence-based revision:

1. **Vektor** is the current system/runtime project name.
2. **Claude Code** is the current control/harness layer.
3. **llama.cpp** is the current local inference engine.
4. **Qwen 3.5 9B Q4_K_M** is the current local model.
5. The current runtime endpoint is `http://127.0.0.1:8080`.
6. The live llama.cpp API is the runtime source of truth when verifying the active model/service.
7. **CLL is retired from the architecture**; it is not required for the current Claude Code → llama.cpp path.
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

- [ ] Final read-only Vektor Doctor
- [ ] Reproducible startup procedure
- [ ] Repeatable benchmark/verification record
- [ ] Runtime documentation committed
- [ ] Trello state reconciled with the implementation
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
