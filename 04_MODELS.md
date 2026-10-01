# AI Masterpiece — Model Registry

## Status — 1 October 2026

A current local model is now selected for the **Vektor prototype**. This does not prevent later benchmark-driven replacement or specialist models.

| Role | Primary | Runtime | Status |
|---|---|---|---|
| Vektor general/local core | Qwen 3.5 9B Q4_K_M | llama.cpp | **CURRENT / VERIFIED PROTOTYPE** |
| Coding specialist | TBD | TBD | Future research |
| Reasoning specialist | TBD | TBD | Future research |
| Research specialist | TBD | TBD | Future research |
| Vision | TBD | TBD | Future research |
| Fast/simple worker | TBD | TBD | Future research |
| Embeddings | TBD | TBD | Future research |

## Current Model Record

- Model family: Qwen 3.5
- Model size: 9B
- Quantisation: Q4_K_M
- Model file: `Qwen3.5-9B-Q4_K_M.gguf`
- Model location: `D:\Users\jenso\.lmstudio\models\lmstudio-community\Qwen3.5-9B-GGUF\Qwen3.5-9B-Q4_K_M.gguf`
- Runtime: llama.cpp
- API model ID observed: `qwen3.5-9b`

## Evidence

The model has been loaded and exercised through the local llama.cpp server and reached the Claude Code harness through the OpenAI-compatible API.

The model is therefore **verified as the current working local prototype**, not merely a candidate from research.

## Future Evaluation

Quality, reasoning, coding, tool calling, context handling, speed, VRAM/RAM usage, reliability, licensing and local availability remain relevant for future model changes.

## Rule

Do not choose future models solely by parameter count. Benchmark candidates on the actual hardware and workloads. A replacement requires evidence and should be recorded as a new decision rather than silently changing the current model record.
