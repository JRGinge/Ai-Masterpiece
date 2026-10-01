# VEKTOR — Runtime Record

**Record date:** 1 October 2026
**Status:** Current prototype configuration

## Runtime Topology

```text
Claude Code
    ↓
HTTP / OpenAI-compatible API
    ↓
llama.cpp server
    ↓
Qwen 3.5 9B Q4_K_M
```

## Executables

| Component | Path |
|---|---|
| Claude Code | `C:\Users\jenso\.local\bin\claude.exe` |
| llama.cpp | `D:\Users\jenso\Desktop\AI\llama.cpp\llama.exe` |
| Qwen model | `D:\Users\jenso\.lmstudio\models\lmstudio-community\Qwen3.5-9B-GGUF\Qwen3.5-9B-Q4_K_M.gguf` |

## API

- Endpoint: `http://127.0.0.1:8080`
- Health endpoint: `/health`
- Model endpoint: `/v1/models`
- Expected model ID: `qwen3.5-9b`
- API owner observed: `llamacpp`

## Verification State

The following have been verified during the Vektor runtime work:

- llama.cpp executable exists
- Qwen model exists
- server starts
- port 8080 responds
- health check succeeds
- model listing succeeds
- expected Qwen model ID is exposed
- Claude Code reaches the local endpoint
- local inference is functional

## Observed Runtime Detail

A verified server instance was observed on port 8080 with PID `18384` during diagnosis. The PID is **not** a persistent configuration value and must not be treated as an expected PID after restart.

## Context

A 32,768-token context was observed during the runtime verification. This is an observed runtime setting, not a claim that future configurations must retain it.

## Source of Truth

Configuration documents describe the intended state. The live llama.cpp API is authoritative for:

- whether the server is alive
- which model is currently exposed
- runtime identity
- current service availability

## Diagnostics

The Vektor Doctor must be read-only. It should report discrepancies rather than silently modifying the runtime or its configuration.

Minimum checks:

1. Claude executable
2. llama executable
3. model file
4. port/listener
5. `/health`
6. `/v1/models`
7. expected model ID
8. basic runtime identity

## Known Historical Issue

An earlier architecture attempted to launch Claude Code through `cll.exe`. That path failed because `cll.exe` was not present. The current architecture removes that dependency and uses Claude Code directly against the llama.cpp API.

## Recovery Principle

The runtime must remain understandable and restartable without relying on Vektor to repair itself. The AI must not be the sole recovery mechanism.
