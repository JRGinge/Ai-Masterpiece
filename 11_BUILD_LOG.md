# AI Masterpiece — Build Log

## Current Build Status — 25 October 2026

**Vektor Local Inference Core:** previously verified prototype; current OpenCode harness integration needs re-verification

The project has moved from planning-only into controlled implementation. The first implementation milestone establishes a working local inference path without claiming that the wider Vektor system is production-ready.

---

# Vektor Milestone 01 — Local Core

## Architecture Reconciliation — 25 October 2026

The 1 October build record below documents the earlier Claude Code harness and is retained as historical evidence. On 4 October, the user accepted OpenCode as the current harness, replacing Claude Code. The current architecture is OpenCode → llama.cpp API (`127.0.0.1:8080`) → Qwen 3.5 9B Q4_K_M. This document update does not claim that OpenCode is currently configured or successfully connected; that requires a fresh read-only verification.

Morphy was discussed on 24 October as a possible GUI/control-room layer. It remains an evaluation candidate, not a selected component.

### Follow-up acceptance checks

- [ ] Record installed OpenCode version and effective config source(s)
- [ ] Confirm selected provider and model ID
- [ ] Verify OpenCode reaches the local llama.cpp API
- [ ] Verify tool calling/agent features required by Vektor against the selected model
- [ ] Keep Morphy out of the runtime baseline unless separately tested and approved

---

## Historical Build Record — 1 October 2026

### Architecture

```text
Claude Code [historical harness at time of this test]
    ↓
llama.cpp
    ↓
Qwen 3.5 9B Q4_K_M
```

### Runtime

- Endpoint: `http://127.0.0.1:8080`
- Model ID observed: `qwen3.5-9b`
- llama executable: `D:\Users\jenso\Desktop\AI\llama.cpp\llama.exe`
- Model file: `D:\Users\jenso\.lmstudio\models\lmstudio-community\Qwen3.5-9B-GGUF\Qwen3.5-9B-Q4_K_M.gguf`
- Claude executable: `C:\Users\jenso\.local\bin\claude.exe`

### Verified

- [x] llama.cpp executable found
- [x] Qwen 3.5 9B model found
- [x] llama.cpp server started
- [x] Port 8080 reachable
- [x] `/health` endpoint responded successfully
- [x] `/v1/models` returned the expected local model ID
- [x] Claude Code connected to the local endpoint
- [x] Local inference exercised successfully

### Known Diagnostic History

At the time of this historical test, earlier setup attempts encountered a missing `cll.exe` path and API connection failures. The setup was simplified so Claude Code connected directly to llama.cpp. CLL remains retired; OpenCode is now the accepted harness, pending fresh integration verification.

The Vektor Doctor is intended to be **read-only**: inspect and report runtime state without modifying existing configuration or files.

### Result

**PASS — working local runtime prototype.**

This milestone does not prove:

- long-running stability
- complete tool calling
- MCP integration
- memory
- Obsidian integration
- autonomous execution
- security enforcement
- model routing
- production recovery
- full Second Mind behaviour

### Next Step

Finish the Stable Local Core acceptance work:

1. Finalise the read-only Vektor Doctor.
2. Establish a reproducible startup procedure.
3. Record a repeatable benchmark.
4. Document restart/recovery.
5. Reconcile Trello with the actual implementation state.

---

# Engineering Rule

**Installed ≠ working.** Every implementation must be tested and verified with evidence.
