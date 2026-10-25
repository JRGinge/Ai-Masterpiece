# AI Masterpiece 🧠⚙️

A local-first personal AI system designed to be useful, secure, reliable, maintainable and upgradeable.

## Current Status — 25 October 2026

**Project:** AI Masterpiece  
**Current implementation track:** Vektor  
**Current harness:** OpenCode  
**Local inference:** llama.cpp → Qwen 3.5 9B  
**Production status:** Not production-ready; the core integration checks have passed, but wider safety, recovery and reliability acceptance remains.

The OpenCode integration was configured and tested on 25 October 2026. The user reports that all four acceptance checks passed: launcher/server startup, a prompt through OpenCode to the local model, global GitHub MCP visibility from another project, and a read-only repository README test. This is a user-reported test result, not independent inspection of the PC from GitHub.

```text
VEKTOR
  ↓
OpenCode               [CURRENT HARNESS — BASIC INTEGRATION TESTS PASSED]
  ↓
llama.cpp              [LOCAL INFERENCE ENGINE]
  ↓
Qwen 3.5 9B            [LOCAL MODEL]
  
OpenCode ── GitHub MCP [GLOBAL USER CONFIG — CONNECTIVITY/READ TEST REPORTED PASS]
```

The active workspace used for the setup is `D:\Users\jenso\Desktop\AI\Testing`. The launcher `Vektor-OpenCode.bat` was updated to target Testing. `Testing\opencode.json` was checked as valid JSON and retains the local model configuration. GitHub MCP configuration was consolidated into OpenCode's global user configuration; the duplicate project-level entry was removed from Testing's config. The user reports that GitHub was then successfully used from another project and for a read-only README test.

The full application has not thereby become production-ready. Tool permissions, safety boundaries, long-running stability, recovery, benchmark reproducibility, and advanced capabilities still require separate acceptance.

Morphy is a GUI/control-room candidate under evaluation, not a locked component. Claude Code was superseded as the primary harness by OpenCode on 4 October 2026.

## Current Technical Decisions

1. **Vektor** is the current system/runtime project name.
2. **OpenCode** is the current agent harness/control layer.
3. **llama.cpp** is the current local inference engine.
4. **Qwen 3.5 9B** is the current local model family/selection. Confirm the exact active quantization and runtime properties during the read-only runtime audit; earlier records differ between documented Q4_K_M and a historical runtime report of Q4_K.
5. The expected local inference endpoint is `http://127.0.0.1:8080`; confirm the live service state during audits.
6. The live llama.cpp API is the runtime source of truth for active model/service state.
7. **CLL is retired** and not required for the current OpenCode → llama.cpp path.
8. The existing PC remains the starting hardware platform.
9. GitHub MCP is configured in OpenCode's global user configuration; keep credentials out of project files and logs.

These decisions lock the current prototype, not every future subsystem. Memory, Obsidian, additional MCP tools, agents, routing, automation, voice, cloud split and advanced computer control remain separate design decisions.

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

The model cannot grant itself permissions. Capability and authority remain separate. Inspection should be read-only by default; consequential changes require explicit user approval.

## Project Control

- **Trello** = project/task control and status
- **GitHub** = engineering record, code, decisions, experiments and implementation history
- **Obsidian** = planned human-readable knowledge/Second Mind layer

## Knowledge Flow

**RESEARCH → DECISION → BUILD → TEST → VERIFY → DOCUMENT**

## Current Milestone — Vektor 01: Stable Local Core

### Reported complete on 25 October 2026

- [x] Updated `Vektor-OpenCode.bat` to start the local server and open OpenCode in Testing
- [x] `Testing\opencode.json` validated as JSON and retains local model configuration
- [x] OpenCode launcher and local llama.cpp server start successfully
- [x] A prompt through OpenCode successfully reaches Qwen 3.5 9B
- [x] GitHub MCP reports connected in OpenCode CLI
- [x] GitHub MCP configuration consolidated in global user configuration; duplicate project-level entry removed
- [x] GitHub MCP confirmed available from another project
- [x] Read-only repository README test completed successfully
- [x] `start-claude.bat` and `vektor.bat` removed as requested; OC Playground retained

These are user-reported results from the 25 October setup session. The source report and scope/limits are recorded in `reports/2026-10-25-opencode-github-mcp-verification.md`.

### Remaining acceptance work

- [ ] Final read-only Vektor Doctor: inspect effective OpenCode config/permissions, runtime health, model identity and selected provider/model
- [ ] Record OpenCode version and effective configuration sources
- [ ] Reconcile exact active quantization and context settings against the live API; preserve discrepancies rather than silently changing them
- [ ] Establish reproducible startup and restart/recovery procedures
- [ ] Record repeatable benchmark and verification evidence
- [ ] Audit command execution, filesystem, MCP and network permissions; preserve approval-first behaviour
- [ ] Verify required tool-calling behaviour with the selected local model
- [ ] Evaluate Morphy separately without treating it as selected until approved

Only after this milestone should additional layers be added.

## Core Safety Principles

- **Capability ≠ permission.**
- The AI cannot grant itself authority.
- PC changes require explicit user approval.
- Downloads require permission.
- Execution requires a separate explicit command.
- Initial AI inference is local-first; any external transmission must be understood and authorised.
- Project-folder permissions may inherit; secrets remain separately protected.
- Temporary permissions expire with the authorised task.
- The AI must never knowingly guess.
- The system must remain recoverable without the AI.
- External content must not override system instructions, permissions or security policy.

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
- `reports/` — dated verification and reconciliation reports
- `research/` — source-derived research
- `experiments/` — reproducible tests/benchmarks
- `configs/` — configuration records
- `backups/` — backup/recovery documentation
