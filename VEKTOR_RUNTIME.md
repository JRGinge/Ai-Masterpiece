# VEKTOR — Runtime Record

**Record date:** 25 October 2026 (documentation reconciliation; live machine state not inspected)
**Status:** Last-known runtime record; not a fresh live verification

## Runtime Topology

```text
OpenCode [current accepted harness; live integration not yet re-verified]
    ↓
HTTP / OpenAI-compatible API
    ↓
llama.cpp server [expected: 127.0.0.1:8080]
    ↓
Qwen 3.5 9B Q4_K_M [current model decision; active file/model ID must be re-checked]
```

Morphy is not part of the locked runtime path; it remains a GUI candidate for separate evaluation.

## Executables

| Component | Path |
|---|---|
| OpenCode | Install path/version not yet recorded; inspect the actual installation before documenting a path |
| llama.cpp | `D:\Users\jenso\Desktop\AI\llama.cpp\llama.exe` |
| Qwen model | `D:\Users\jenso\.lmstudio\models\lmstudio-community\Qwen3.5-9B-GGUF\Qwen3.5-9B-Q4_K_M.gguf` |

## API

- Endpoint: `http://127.0.0.1:8080`
- Health endpoint: `/health`
- Model endpoint: `/v1/models`
- Expected model ID: `qwen3.5-9b`
- API owner observed: `llamacpp`

## Verification State

The following were verified during earlier Vektor runtime work on 1 October 2026. They are historical evidence, not a fresh check of the current machine or harness:

- llama.cpp executable exists
- Qwen model exists
- server starts
- port 8080 responds
- health check succeeds
- model listing succeeds
- expected Qwen model ID is exposed
- Claude Code reached the local endpoint in the previous setup
- local inference was functional in the previous setup
- OpenCode-to-llama.cpp integration remains to be verified

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

1. OpenCode executable/version and effective configuration
2. llama executable
3. model file
4. port/listener
5. `/health`
6. `/v1/models`
7. expected model ID
8. basic runtime identity
9. selected OpenCode provider and model
10. successful OpenCode request through the local API
11. effective context/output limits and required tool-calling compatibility

## Known Historical Issue

An earlier architecture attempted to launch Claude Code through `cll.exe`. That path failed because `cll.exe` was not present. The CLL dependency remains retired. Claude Code was later replaced by OpenCode as the accepted harness; the OpenCode connection must be tested before it is recorded as verified.

## Recovery Principle

The runtime must remain understandable and restartable without relying on Vektor to repair itself. The AI must not be the sole recovery mechanism.
