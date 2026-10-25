# AI Masterpiece — Software Stack

## Status — 25 October 2026

The **Vektor local-core design baseline** is locked for now. The inference path was previously tested, but current live state and OpenCode integration still require verification. The wider software stack remains open where implementation evidence is not yet available.

## Current Locked Core

| Layer | Choice | State |
|---|---|---|
| Project/runtime | Vektor | **LOCKED CURRENT BASELINE** |
| Harness/control | OpenCode | **DECIDED — INTEGRATION RE-VERIFICATION PENDING** |
| Local inference | llama.cpp | **PREVIOUSLY VERIFIED — LIVE STATE TO RECHECK** |
| Local model | Qwen 3.5 9B Q4_K_M | **CURRENT MODEL DECISION — ACTIVE MODEL TO RECHECK** |
| API endpoint | `http://127.0.0.1:8080` | **EXPECTED ENDPOINT — LIVE STATE TO RECHECK** |
| CLL | None | **RETIRED / NOT REQUIRED** |

## Runtime Principle

The live llama.cpp API is the source of truth for runtime state. Documentation records the expected configuration, while health/model endpoints establish what is actually running.

## GUI Candidate (Not Yet Selected)

Morphy is being considered as a visual control-room/workspace. It must be tested alongside the current OpenCode setup before any migration or dependency decision. Do not describe it as selected or installed without evidence.

## Still Open / Future Research

- OS-level sandboxing
- Filesystem permission implementation
- Memory/database
- Vector/search
- Obsidian integration
- GitHub/Trello integration inside Vektor
- MCP/tools/skills
- Specialist models and routing
- Monitoring
- Voice
- Automation
- External/cloud services
- Controlled computer interaction

## Selection Criteria

Capability, hardware compatibility, privacy, security, reliability, maintenance burden, cost, portability, upgradeability and project health.

## Rule

Do not assemble a complicated stack merely because components are popular. The smallest architecture that satisfies the requirements wins.
