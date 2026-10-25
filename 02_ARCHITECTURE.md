# AI Masterpiece — Architecture

## Status — 25 October 2026

**Current state:** Vektor's local inference choices remain the current implementation baseline, but the former Claude Code harness has been superseded. OpenCode integration is not yet freshly verified. The wider system architecture remains deliberately modular and is not fully locked.

## Current Vektor Core

```text
USER
  ↓
OpenCode
  [CURRENT AGENT HARNESS — INTEGRATION RE-VERIFICATION PENDING]
  ↓
llama.cpp
  [LOCAL INFERENCE ENGINE]
  ↓
Qwen 3.5 9B Q4_K_M
  [CURRENT MODEL DECISION]
```

Morphy is a GUI/control-room candidate only; it is not part of the locked runtime path. Claude Code was superseded as the primary harness on 4 October 2026.

Runtime endpoint:

```text
http://127.0.0.1:8080
```

The live llama.cpp API is the source of truth for active runtime/model verification.

## Locked Current Choices

- Project/runtime name: **Vektor**
- Harness: **OpenCode** (accepted current baseline; live integration not yet re-verified)
- Inference engine: **llama.cpp**
- Current model: **Qwen 3.5 9B Q4_K_M**
- API endpoint: **http://127.0.0.1:8080**
- CLL: **retired from the current architecture**

These choices describe the intended current baseline, not a fresh runtime verification. They may be revised only through the normal research/evidence/decision process.

## Vektor Operating Loop

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

This is the intended control discipline. A model may propose or request an action but cannot grant itself authority.

## GUI / Interface Status

- **Current harness:** OpenCode.
- **GUI candidate:** Morphy, evaluation pending; not yet selected.
- **Runtime management:** llama.cpp's API remains the local inference interface. A GUI choice does not itself change the runtime architecture.

## Wider Architecture — Future Layers

```text
USER
 ↓
INTERFACE
 ↓
VEKTOR / CONTROL
 ↓
MODEL(S)
 ↓
TOOLS / MCP / SKILLS
 ↓
MEMORY / KNOWLEDGE
 ↓
LOCAL INFRASTRUCTURE
```

Possible future components include routing, specialist models, Obsidian, memory/retrieval, GitHub, Trello, MCP, deterministic tools, research systems, automation and controlled computer interaction.

None of those are required to declare the Vektor local core working.

## Architectural Goals

- Replaceable components.
- No permanent model dependency.
- Data remains accessible without the AI.
- Permissions enforced independently from the model.
- Tools are narrowly scoped.
- Complexity is introduced only when justified.
- The AI is never the root of control or the sole recovery mechanism.

## Critical Boundary

**Capability ≠ permission.**

The model may propose an action or request permission. It cannot grant itself authority. The security layer must independently enforce authority as the project develops.
