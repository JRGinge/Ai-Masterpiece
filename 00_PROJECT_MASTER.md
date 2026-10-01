# AI Masterpiece — Project Master Record

> **Status:** Phase 0 / controlled implementation
> **Current implementation:** Vektor Local Core
> **Build status:** Verified prototype; Milestone 01 acceptance work remains
> **Record date:** 1 October 2026

## Current State

AI Masterpiece has moved beyond planning-only work. The current implementation track is **Vektor**, a deliberately small local AI core built and tested on the existing PC.

```text
VEKTOR
  ↓
Claude Code              [HARNESS / CONTROL]
  ↓
llama.cpp                [LOCAL INFERENCE]
  ↓
Qwen 3.5 9B Q4_K_M      [CURRENT MODEL]
```

Current runtime endpoint: `http://127.0.0.1:8080`.

The local core has been exercised successfully. This does **not** mean the complete personal AI system is finished or production-ready.

## Locked Current Prototype Decisions

These choices are locked for the current Vektor implementation baseline because they have been tested and explicitly accepted. They can be superseded only by a new documented decision backed by evidence.

| Item | Current choice | State |
|---|---|---|
| System/runtime name | Vektor | DECIDED — CURRENT BASELINE |
| Harness/control | Claude Code | VERIFIED |
| Inference engine | llama.cpp | VERIFIED |
| Local model | Qwen 3.5 9B Q4_K_M | VERIFIED |
| API endpoint | `http://127.0.0.1:8080` | VERIFIED |
| Runtime source of truth | Live llama.cpp API | DECIDED |
| CLL | Retired / not required | RETIRED |
| Starting hardware | Existing Ryzen 5 5600X / RTX 3070 PC | DECIDED |

The lock applies to the **current local prototype**, not to every future subsystem or the eventual end-state architecture.

## Vektor Operating Protocol

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

The AI may inspect, analyse and propose. It cannot grant itself authority. Consequential actions require the appropriate explicit user approval.

## Current Verified Evidence

- llama.cpp executable is present and runnable.
- Qwen 3.5 9B Q4_K_M model is present.
- llama.cpp server starts on port 8080.
- `/health` responds successfully.
- `/v1/models` exposes `qwen3.5-9b`.
- The API reports the local llama.cpp runtime identity.
- Claude Code reaches the local endpoint.
- Local inference has been exercised successfully.

A server instance with PID `18384` was observed during diagnosis. This is historical runtime evidence only; PIDs are not persistent configuration.

A 32,768-token context was observed during verification. This is an observed configuration, not a permanent requirement.

## Not Yet Proven

- Long-running stability
- Reproducible startup/restart
- Formal benchmark baseline
- Tool calling
- MCP
- Persistent memory
- Second Mind runtime
- Obsidian integration
- GitHub/Trello control from inside Vektor
- Autonomous agents
- Model routing
- Voice
- Computer control
- External automation
- Cloud failover
- Full security sandboxing
- Production recovery

## System-of-Record Boundaries

**Trello** = project control: tasks, status, backlog, milestones and execution state.

**GitHub** = engineering record: code, architecture, decisions, experiments, build evidence and implementation history.

**Obsidian** = planned human-readable knowledge / Second Mind layer. It is not yet a Vektor runtime dependency.

## Current Milestone — Vektor 01: Stable Local Core

Completed:

- [x] Local model loads
- [x] llama.cpp API runs
- [x] Health endpoint works
- [x] Model endpoint works
- [x] Claude Code connects
- [x] Local inference works

Remaining:

- [ ] Final read-only Vektor Doctor
- [ ] Reproducible startup procedure
- [ ] Repeatable benchmark/verification record
- [ ] Restart/recovery procedure
- [ ] Reconcile Trello/GitHub implementation state

## Core Safety Principles

- **Capability ≠ permission.**
- The AI cannot grant itself authority.
- PC changes require explicit user approval.
- Downloads and execution remain separately authorised.
- Initial AI inference is local-only.
- External data transmission is restricted.
- Project-folder permissions may inherit; secrets remain separately controlled.
- Temporary permissions expire with the authorised task.
- The AI must never knowingly guess.
- The system must remain recoverable without the AI.
- External content must not override system instructions, permissions or security policy.

## Historical Naming

**AI Masterpiece** remains the umbrella project/repository.

**Bionic** is historical naming from earlier runtime work.

**Vektor** is the current local system/runtime implementation name.

The earlier CLL-based launcher path is retired; the current architecture uses Claude Code directly against the llama.cpp API.

## Decision / Build Discipline

```text
REQUIREMENTS → RESEARCH → COMPARE → TEST → USER DECISION → DOCUMENT

PLAN → BUILD → TEST → VERIFY → DOCUMENT
```

A suggestion is not a decision. A working experiment is not automatically a permanent architecture. Significant changes must preserve the historical record and document the evidence for the replacement.
