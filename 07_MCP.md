# AI Masterpiece — MCP & Tools

## Purpose
Provide controlled access to useful capabilities without giving the model unrestricted machine access.

## Candidate Tools
- Filesystem
- Web/research
- Obsidian
- Git
- Databases
- Development environment
- APIs
- Calendar/tasks
- Computer interaction (future)

## Tool Contract
Every tool should have a clear purpose, defined inputs/outputs, permission boundary, error handling, logging and documentation.

## Permission Model
**0 — No external action**

**1 — Read-only**

**2 — Create/modify non-critical data**

**3 — External/consequential action requiring approval**

**4 — High-risk administrative action; avoid by default**

Network permission is separate from filesystem permission.

## Core Rule
Capability ≠ permission. The security layer enforces authority independently from the model.