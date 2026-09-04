# AI Masterpiece — Hardware

## Current Platform
- CPU: AMD Ryzen 5 5600X
- GPU: NVIDIA RTX 3070
- Motherboard: ASUS TUF B450-Plus Gaming
- Storage: multiple SSDs

## Strategy
Use the existing machine first. Do not buy hardware until a measured bottleneck demonstrates that an upgrade solves a real workload limitation.

## Metrics
- VRAM usage
- GPU utilisation
- RAM usage
- CPU utilisation
- Model load time
- Tokens/sec
- Storage usage
- Temperature
- Power where useful

## RTX 3070 Constraint
The GPU's 8 GB VRAM is expected to constrain larger local models. Candidate mitigations include quantisation, smaller models and CPU/RAM offload where practical.

## Benchmark Requirement
For serious model candidates record model/version, quantisation, context length, tokens/sec, VRAM/RAM use, quality results and reliability.