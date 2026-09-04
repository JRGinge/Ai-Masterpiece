# AI Masterpiece — Architecture

## Status
**Working architecture — not fully locked.**

```text
USER
  ↓
INTERFACE
  ↓
BOSS / PERSONAL AI
  ↓
MODEL ROUTER (future / only if justified)
  ├── General
  ├── Reasoning
  ├── Coding
  ├── Vision
  └── Fast/simple
  ↓
TOOLS / MCP / SKILLS
  ├── Files
  ├── Web
  ├── Obsidian
  ├── APIs
  ├── Development tools
  └── Computer control (future)
  ↓
MEMORY / KNOWLEDGE
  ├── Raw archive
  ├── Active knowledge
  ├── Structured data
  ├── Documents
  ├── Embeddings/search
  └── Relationships
  ↓
LOCAL INFRASTRUCTURE
```

## Architectural Goals
- Replaceable components.
- No permanent model dependency.
- Data remains accessible without the AI.
- Permissions enforced independently from the model.
- Tools are narrowly scoped.
- Complexity is introduced only when justified.

## Boss AI
Potential responsibilities: understand requests, choose operating mode, plan work, retrieve relevant memory, select tools/models, coordinate workers and produce the final response.

## Adaptive Operating Mode
The AI should determine whether to answer, research, ask, collaborate or work autonomously based on task complexity, uncertainty, risk, required effort and explicit user authorisation.

## Critical Boundary
**Capability ≠ permission.**

The model may propose an action or request permission. It cannot grant itself authority. The security layer independently enforces authority.

## Recovery Principle
The AI is a layer on top of the system, never the system's root of control.