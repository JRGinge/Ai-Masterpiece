# AI Masterpiece — Roadmap

## Current State — 1 October 2026

The project is in **Phase 0 / controlled implementation**, with the **Vektor Local Core** already built and verified as a prototype.

The roadmap remains evidence-driven: phases may be reordered when testing or requirements justify it.

## Phase 0 — Requirements, Architecture & Governance
Define requirements, constraints, architecture and security boundaries while maintaining the project record.

**Current:** Active. The Vektor core has been selected and verified through hands-on experimentation; wider subsystem decisions remain open.

**Exit:** requirements sufficiently complete and the current architecture is justified/documented.

## Phase 1 — Prepare Existing PC
Establish a stable, measured AI development environment on the existing Ryzen 5 5600X / RTX 3070 PC.

**Status:** Baseline known; measurement/documentation continues where needed.

## Phase 2 — Local LLM Runtime
Research, install and benchmark an appropriate local inference runtime.

**Vektor implementation track:** llama.cpp is the current verified runtime and Qwen 3.5 9B Q4_K_M is the current model. This is a scoped prototype decision, not a permanent ban on alternatives.

**Current milestone:** Vektor 01 — Stable Local Core.

Acceptance remaining:
- Final read-only Vektor Doctor
- Reproducible startup
- Repeatable benchmark
- Restart/recovery procedure
- Trello/GitHub reconciliation

## Phase 3 — Basic Personal Assistant
Build the smallest useful local assistant around the verified runtime.

## Phase 4 — Memory & RAG
Implement durable memory and selective retrieval only after the requirements and architecture are sufficiently defined.

## Phase 5 — Obsidian / Knowledge Integration
Connect human-readable project knowledge safely. Obsidian remains planned, not a current Vektor dependency.

## Phase 6 — MCP, Tools & Skills
Add narrowly scoped tools with independent permission/security enforcement.

## Phase 7 — Agents & Model Routing
Add specialist workers/routing only where evidence shows value.

## Phase 8 — Voice & Computer Interaction
Add voice and carefully controlled computer interaction.

## Phase 9 — Automation & External Access
Add scheduled work and external integrations under explicit security controls.

## Phase 10 — Optimisation & Expansion
Benchmark, monitor, improve and upgrade only when justified.

## Governing Rule

Do not add components merely because they are popular or available. Each new layer should satisfy a requirement, survive comparison/testing, and be documented with its evidence and approval state.
