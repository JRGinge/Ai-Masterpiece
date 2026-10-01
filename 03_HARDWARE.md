# AI Masterpiece — Hardware Baseline

## Status — 1 October 2026

The existing PC is the locked starting platform for the current Vektor prototype. Hardware upgrades remain evidence-driven rather than assumed.

| Component | Current baseline |
|---|---|
| CPU | AMD Ryzen 5 5600X |
| GPU | ASUS TUF RTX 3070, 8 GB VRAM |
| Motherboard | ASUS TUF B450-Plus Gaming |
| RAM | 16 GB DDR4 |
| Storage | 2 × 1 TB SSD + 512 GB SSD (approximately 2.5 TB nominal) |
| OS | Windows |

## Vektor Relevance

The current machine is sufficient to run the verified Qwen 3.5 9B Q4_K_M local prototype through llama.cpp. The 8 GB VRAM and 16 GB system RAM are important constraints for larger models, larger contexts and parallel workloads.

Current strategy:

> **Measure the bottleneck before buying the chrome.**

Potential future mitigations include quantisation, CPU/RAM offload, model-size changes and hardware upgrades where measurements demonstrate a real limitation.

## Required Benchmark Metrics

For serious model/runtime comparisons record:

- Model/version
- Quantisation
- Context length
- Tokens/sec
- Prompt/eval performance where available
- VRAM usage
- RAM usage
- CPU utilisation
- Model load time
- Temperature
- Storage usage
- Stability/reliability
- Task-quality observations

## Upgrade Rule

Do not treat a larger GPU, more RAM or a new platform as automatically necessary. An upgrade should be tied to a measured workload limitation and a specific requirement it solves.
