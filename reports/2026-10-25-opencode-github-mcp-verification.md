# Vektor + OpenCode Work Report

**Date:** 25 October 2026  
**Workspace:** `D:\Users\jenso\Desktop\AI`  
**Active OpenCode workspace:** `Testing`  
**Purpose:** Prepare OpenCode for Vektor, connect the local Qwen model, configure GitHub MCP globally, and reconcile project records.

## Outcome

The user reports that all four end-to-end follow-up checks were completed successfully after the configuration work:

1. `Vektor-OpenCode.bat` starts the local model server and opens OpenCode.
2. A prompt in OpenCode successfully reaches the local Qwen 3.5 9B model.
3. `opencode mcp list` / MCP availability confirms GitHub is available from another project.
4. A read-only GitHub repository README test succeeds.

These results were confirmed by the user in the ChatGPT conversation on 25 October 2026. This report records that confirmation; it is not an independent machine-side log or benchmark.

## Workspace and launcher changes

- Reviewed the AI workspace and existing launchers.
- Updated `Vektor-OpenCode.bat` to start the existing llama.cpp runtime, wait for the server, then open OpenCode using `Testing`.
- Added/retained `Testing\README.md` and `Testing\opencode.json`.
- Validated `Testing\opencode.json` as valid JSON; the local model setting remained present.
- Removed `start-claude.bat` and `vektor.bat` as requested.
- Kept the OC Playground folder and its contents in place.
- The full launcher path was subsequently reported working.

## Local model

- Harness: OpenCode
- Inference server: llama.cpp
- Model: Qwen 3.5 9B
- Expected local API: `http://127.0.0.1:8080`
- The user reports a successful prompt through OpenCode to the local model.

Do not assume the exact active quantization, context size, or other runtime properties from the model name alone. Previous records contain a discrepancy between the intended Q4_K_M model and an earlier runtime report of Q4_K, as well as historical context-size differences. Resolve these in the read-only runtime audit using the live API and actual launch arguments.

## GitHub MCP

- Initial OpenCode CLI failure: HTTP 400, malformed Authorization header.
- A direct request using the token/endpoint returned HTTP 200.
- Subsequent OpenCode CLI output reported `github connected`.
- GitHub MCP configuration was found in OpenCode's global user configuration.
- Removed the duplicate project-level GitHub MCP entry from `Testing\opencode.json`; retained the local model configuration.
- The user subsequently confirmed GitHub MCP availability from a second project and a successful read-only README test.
- Do not put tokens or other credentials in repository files, Trello descriptions, or logs.

## Code Mode catalogue concern

A pasted tool-use catalogue was reviewed. Its text alone did not establish that a system prompt had been created or replaced. Some schema annotations contained formatting artifacts.

## Current architecture

```text
Vektor
  ↓
OpenCode (harness/control)
  ↓
llama.cpp (local inference)
  ↓
Qwen 3.5 9B (local model)

OpenCode ── GitHub MCP (global user configuration)
```

## Remaining work

- [ ] Perform final read-only Vektor Doctor.
- [ ] Record OpenCode version, effective configuration sources, selected provider and model.
- [ ] Inspect effective command, filesystem, MCP and network permissions.
- [ ] Reconcile active quantization and context values against the live runtime; report discrepancies without silently changing settings.
- [ ] Establish reproducible startup and restart/recovery procedures.
- [ ] Record repeatable benchmark and verification results.
- [ ] Verify required tool-calling behaviour with the local model.
- [ ] Preserve approval-first lifecycle: Inspect → Analyse → Propose → Ask approval → Execute → Verify.

## Safety and scope

This is progress on the Stable Local Core, not a declaration that Vektor is production-ready. Memory, Obsidian integration, additional MCP tools, autonomous agents, model routing, voice, computer control, automation, cloud failover and full security sandboxing remain separate capabilities requiring design and verification.

**System of record:** Trello tracks project status and tasks; GitHub holds engineering records and implementation history; Obsidian remains the planned human-readable knowledge layer.
