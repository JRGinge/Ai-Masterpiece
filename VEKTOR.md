# VEKTOR — Current System Record

**Record date:** 25 October 2026
**Status:** Current implementation baseline

## What Vektor Is

Vektor is the current name for the local AI system implementation track within AI Masterpiece.

The current Vektor core is deliberately small:

```text
Vektor
  ↓
OpenCode [current harness; integration re-verification pending]
  ↓
llama.cpp [127.0.0.1:8080]
  ↓
Qwen 3.5 9B Q4_K_M
```

Morphy is a candidate GUI/control-room layer under evaluation, not a locked dependency. Claude Code was superseded as the primary harness on 4 October 2026.

The goal at this stage is not to build every planned subsystem. The goal is to establish a stable, observable and reproducible local core before adding complexity.

## Roles

### Vektor
System/project identity and future control architecture.

### OpenCode
Current accepted agent harness/control layer. The decision is locked provisionally for the current baseline; actual provider/model configuration and successful llama.cpp integration must be re-verified.

### Morphy
Optional GUI candidate under evaluation only. Not selected as a required runtime component.

### llama.cpp
Current local inference engine and API server.

### Qwen 3.5 9B Q4_K_M
Current local general-purpose model.

## Operating Protocol

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

The model does not grant itself permission. The user remains the authority for consequential actions.

## Current Rules

1. Prefer inspection before modification.
2. Read-only diagnostics should not alter existing files or configuration.
3. Treat the live runtime/API as authoritative for runtime state.
4. Record significant implementation decisions.
5. Verify changes after execution.
6. Preserve historical decisions rather than silently rewriting them.
7. Add complexity only when a requirement justifies it.

## Current Scope

### In scope

- Local inference
- OpenCode harness (integration verification pending)
- llama.cpp runtime
- Qwen 3.5 9B
- Runtime diagnostics
- Reproducible startup
- Benchmarking and verification

### Not yet implemented

- Persistent memory
- Second Mind runtime
- Obsidian integration
- MCP/tool layer
- Autonomous agents
- Model routing
- Voice
- Computer control
- External automation
- Cloud failover
- Full security sandbox

These remain future project layers and must not be inferred as already implemented.

## Current Milestone

**Vektor Milestone 01 — Stable Local Core**

Acceptance work:

- [x] Local model loads
- [x] llama.cpp API runs
- [x] Health endpoint works
- [x] Model endpoint works
- [ ] OpenCode connects to the configured local endpoint (re-verify after harness change)
- [x] Local inference was previously exercised through the former Claude Code harness
- [ ] Final read-only Vektor Doctor
- [ ] Reproducible startup procedure
- [ ] Repeatable benchmark record
- [ ] Restart/recovery procedure
- [ ] Trello/GitHub status reconciliation

## Change Control

Changing the current runtime should require evidence. A future replacement should be recorded as a new decision with the reason, evidence, consequences and verification result.
