# AI Masterpiece — Software Stack

## Status — 1 October 2026

The **Vektor local core** is now locked as the current working prototype. The wider software stack remains open where implementation evidence is not yet available.

## Current Locked Core

| Layer | Choice | State |
|---|---|---|
| Project/runtime | Vektor | **LOCKED CURRENT BASELINE** |
| Harness/control | Claude Code | **VERIFIED** |
| Local inference | llama.cpp | **VERIFIED** |
| Local model | Qwen 3.5 9B Q4_K_M | **VERIFIED** |
| API endpoint | `http://127.0.0.1:8080` | **VERIFIED** |
| CLL | None | **RETIRED / NOT REQUIRED** |

## Runtime Principle

The live llama.cpp API is the source of truth for runtime state. Documentation records the expected configuration, while health/model endpoints establish what is actually running.

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
