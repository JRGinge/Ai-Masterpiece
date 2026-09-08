# AI Masterpiece — Clean-Slate Project Record v1.0

> **Status:** Phase 0 — Requirements & Research  
> **Technical decisions:** None, except the existing PC hardware baseline  
> **Build status:** Not authorised  
> **Purpose:** Replace the merged conversation dump with a structured engineering record.

---

# 1. Operating Workflow

This project uses two separate workflows.

## 1.1 Decision workflow

```text
REQUIREMENTS
     ↓
RESEARCH
     ↓
COMPARE
     ↓
TEST / EXPERIMENT (where needed)
     ↓
RECOMMEND
     ↓
USER DECISION
     ↓
DOCUMENT
```

A candidate, suggestion, or popular technology is **not** a decision.

## 1.2 Build workflow

```text
PLAN
 ↓
BUILD
 ↓
TEST
 ↓
VERIFY
 ↓
DOCUMENT
```

## 1.3 Core rule

> **No installation or implementation of a major technology until the relevant requirements and research have been completed and the user is happy with the decision.**

---

# 2. Current Project State

## DECIDED

### Hardware starting platform

- CPU: Ryzen 5 5600X
- GPU: RTX 3070
- Motherboard: ASUS TUF B450-Plus Gaming

The existing PC is the starting platform.

## NOT DECIDED

Everything else remains open, including:

- Operating system
- AI runtime
- Ollama
- llama.cpp
- vLLM
- Open WebUI
- Docker
- Python stack
- Git workflow
- Orchestration
- Boss AI architecture
- Model selection
- Model routing
- Agents
- MCP
- Memory architecture
- Databases
- Vector database
- RAG implementation
- Obsidian architecture
- Graph/knowledge-graph tooling
- Voice
- Computer control
- Browser control
- Automation
- Web research stack
- Local/cloud split
- Monitoring
- Deployment architecture
- Security implementation

**Important:** existing Trello cards and previous conversation suggestions are treated as candidates/work items, not decisions.

---

# 3. Requirements Captured So Far

These came from the requirements interview and are therefore stronger than technology suggestions, but they still need to be formalised into the final requirements specification.

## R-01 — Second Mind

The system should become a persistent second mind that can retain a very large amount of useful information about the user's work, projects, conversations, decisions, knowledge and experiences.

The system should not need to place all retained information into every prompt.

## R-02 — Layered Memory

Memory should be layered rather than being one undifferentiated database.

Candidate conceptual layers:

1. Raw historical archive
2. Structured/episodic memories
3. Knowledge
4. Entities/concepts
5. Relationships
6. Human-readable persistent knowledge
7. Retrieval/context selection
8. Review/inbox layer

This is a **requirements concept**, not yet an implementation decision.

## R-03 — Raw Historical Archive

There should be a complete raw historical record available as an absolute backup/reference layer where practical.

The existence of raw history does not mean the entire history should be loaded into normal conversations.

## R-04 — Self-Organising Knowledge

The system should be able to progressively build structured knowledge about subjects it encounters.

Example:

```text
3D Printer
├── Hot End
├── Mainboard
├── Motors
├── PSU
├── Firmware
└── Configuration
```

Individual entities may have their own persistent notes and relationships to other entities.

## R-05 — Human-Readable Knowledge

The user should be able to inspect the underlying knowledge directly rather than relying on an opaque AI-only memory system.

Obsidian is a **candidate/hypothesis** for this role, not a decision.

## R-06 — Confidence and Provenance

Generated knowledge should distinguish between:

- Explicitly confirmed information
- Strong evidence
- Inference
- Uncertain information

Important information should retain provenance where practical:

- Source
- Date
- Confidence
- Verification state
- Relevant conversation/document/event

## R-07 — Memory Inbox

Uncertain or important unconfirmed information should be able to enter an inbox/review state before becoming trusted knowledge.

Candidate workflow:

```text
AI encounters information
        ↓
Confidence / evidence assessment
        ↓
┌───────────────────┬────────────────────┐
│ High confidence   │ Uncertain / important│
↓                   ↓
Trusted knowledge   Inbox
                    ↓
              User review
                    ↓
          Confirm / Correct / Reject
```

This workflow is a **candidate design pattern** based on the requirements interview.

## R-08 — User Authority Over Memory

The user retains ultimate authority over persistent memory.

The system should support:

- Inspect
- Edit
- Correct
- Delete
- Reorganise

Explicit user confirmation can promote uncertain information into trusted knowledge.

User-authored corrections must take precedence over AI assumptions.

## R-09 — Autonomous Knowledge Maintenance

Once information is explicitly confirmed, the AI should eventually be able to organise, link and maintain that knowledge without requiring approval for every trivial change.

The exact confidence/authority mechanism remains to be researched.

## R-10 — Research

The AI should eventually support both:

- Interactive research
- Explicitly authorised autonomous/deep research

Autonomous research must not imply unrestricted control of the user's computer.

Research should be able to:

- Search multiple sources
- Read documentation
- Analyse relevant material
- Compare evidence
- Cross-check claims
- Identify disagreements
- Track sources
- Produce structured findings
- Preserve useful research as knowledge

## R-11 — PC Awareness and Management

The AI should eventually be capable of:

- Inspecting hardware/software
- Maintaining a model of the user's actual PC
- Monitoring CPU/GPU/RAM/storage/temperatures
- Diagnosing performance problems
- Finding duplicate/unnecessary files
- Helping organise files/folders
- Identifying unnecessary applications/services
- Recommending system optimisations
- Installing/updating software when approved
- Troubleshooting interactively
- Eventually performing proactive maintenance

## R-12 — PC Modification Approval

> **Nothing changes on the PC without explicit human approval.**

Inspection, analysis and recommendation are separate from execution.

Candidate authority model:

| Operation | Default |
|---|---|
| Inspect | Allowed |
| Analyse | Allowed |
| Research | Allowed |
| Recommend | Allowed |
| Prepare change | Explain |
| Execute change | Explicit approval |
| Destructive/admin action | Explicit approval + stronger safeguards |
| Protected system areas | Restricted |

The eventual system should explain what will change, why, consequences, and rollback/recovery where practical.

## R-13 — Security Philosophy

The system should use:

- Least privilege
- Narrowly scoped tools
- Permission levels
- Approval gates
- Logging
- Sandboxing where appropriate
- Protected areas
- Recovery mechanisms

Unrestricted machine access is not an acceptable default.

## R-14 — "Know When to Ask, Know When to Act"

The system should eventually determine how interactive or autonomous a task should be based on factors such as:

- Task uncertainty
- Consequence of mistakes
- User preference requirements
- Research depth
- Repetition
- Explicit autonomy granted
- Whether an action is destructive

This is a behavioural requirement, not yet an implementation.

---

# 4. Candidate Concepts — NOT Decisions

The following ideas have appeared in previous discussions but remain hypotheses until researched.

## Architecture hypothesis

Previous conceptual model:

```text
USER
 ↓
INTERFACE
 ↓
BOSS AI
 ↓
ROUTER
 ↓
WORKERS / MODELS
 ↓
TOOLS / MCP
 ↓
MEMORY
 ↓
KNOWLEDGE / OBSIDIAN
 ↓
LOCAL INFRASTRUCTURE
```

**Status: HYPOTHESIS — NOT LOCKED.**

The system may not need every layer, and the components may be services/subsystems rather than a strict pipeline.

## Local runtime candidates

- Ollama
- llama.cpp
- vLLM
- Other viable runtimes discovered during research

**Status: CANDIDATES.**

## Interface candidates

- Open WebUI
- Web interface
- Desktop interface
- Terminal
- Mobile access
- Voice interface
- Future custom interface

**Status: CANDIDATES.**

## Memory candidates

- Obsidian
- Graphify / graph tooling
- Markdown
- SQLite
- PostgreSQL
- Vector stores
- Knowledge graphs
- RAG
- Embeddings
- Other retrieval systems

**Status: CANDIDATES.**

## Agent/tool candidates

- MCP
- Custom Python tools
- Deterministic scripts
- Agents
- Skills
- Browser control
- Computer control
- Automation

**Status: CANDIDATES.**

---

# 5. Research Missions

Research should proceed from the requirements downward rather than starting with favourite technologies.

## M001 — What Are We Building?

**Status:** IN PROGRESS

Objective:

Produce the formal:

> `REQUIREMENTS SPECIFICATION v1.0`

It must define:

- Goals
- Capabilities
- Autonomy
- Privacy
- Performance
- Reliability
- Budget
- Hardware/resource constraints
- Maintainability
- MVP boundary
- Acceptance criteria

Requirements should be classified:

- MUST
- SHOULD
- COULD
- WON'T YET

### Outstanding M001 interview areas

- Exact day-to-day use cases
- Priority of capabilities
- Privacy boundaries
- File/data access boundaries
- Performance expectations
- Reliability expectations
- Budget
- Future/end-state ambitions
- Exact autonomy boundaries

---

## M002 — Security & Autonomy

**Status:** NOT STARTED

Research:

- Permission models
- Sandboxing
- Tool isolation
- Approval systems
- Secrets handling
- Prompt injection
- Local security
- Network isolation
- Recovery
- Logging
- Safe computer control
- Autonomous task boundaries

---

## M003 — Hardware Baseline

**Status:** NOT STARTED

Measure the existing PC rather than relying on generic specifications.

Required baseline:

- CPU
- GPU
- VRAM
- RAM capacity/configuration
- Storage devices
- Free storage
- OS
- Drivers
- Network
- Cooling/thermals
- Power supply
- Relevant utilisation/performance measurements

No hardware upgrade should be proposed without evidence of a real limitation.

---

## M004 — Local Models

**Status:** NOT STARTED

Research model families and roles rather than searching for one mythical model.

Potential roles:

- General/Boss
- Fast worker
- Coding
- Reasoning
- Research
- Vision
- Embedding
- Speech-to-text
- Text-to-speech
- Specialist/safety

Potential families include:

- Qwen
- Llama
- Mistral
- DeepSeek
- Other strong candidates

Selection must be benchmark-driven against the actual hardware and workloads.

---

## M005 — Local AI Runtime

**Status:** NOT STARTED

Compare:

- Ollama
- llama.cpp
- vLLM
- Other viable candidates

Evaluate:

- GPU support
- OS support
- Quantisation
- Model management
- API
- Tool/function calling
- Multimodal support
- Performance
- Resource usage
- Parallel workloads
- Stability
- Maintainability
- Replaceability

---

## M006 — Orchestration / Boss Architecture

**Status:** NOT STARTED

Research:

- Custom Python orchestration
- Existing frameworks
- Model routers
- Planning
- State management
- Tool calling
- Worker models
- Deterministic workflows
- Agent architectures

First question:

> Does the project actually need an orchestration framework?

---

## M007 — Memory & Second Mind

**Status:** NOT STARTED

Research:

- Raw history storage
- Episodic memory
- Semantic knowledge
- Project memory
- Entity extraction
- Relationships
- Knowledge graphs
- Obsidian
- Graphify
- Wikilinks
- Metadata/frontmatter
- Embeddings
- Vector retrieval
- RAG
- Memory consolidation
- Confidence
- Provenance
- User correction
- Retention/forgetting
- Duplicate prevention
- Retrieval/context selection

Core question:

> What should the AI remember, where should it live, how should it be retrieved, when should it be written, and when should it be forgotten?

---

## M008 — Tools / MCP / Agents

**Status:** NOT STARTED

Research:

- MCP
- Custom tools
- Filesystem
- Web
- Git
- Obsidian
- APIs
- Databases
- Computer interaction
- Automation

For every capability:

> Does an agent/MCP layer provide enough benefit to justify its complexity?

If a deterministic script is better, use the deterministic script.

---

## M009 — Interface

**Status:** NOT STARTED

Research:

- Web UI
- Desktop UI
- Terminal
- Mobile
- Voice
- Future custom interface

---

## M010 — Local vs Cloud

**Status:** NOT STARTED

Determine:

- What must remain local
- What may use cloud
- When cloud provides meaningful benefit
- Privacy implications
- Failover
- Cost
- Latency
- Reliability
- Data-leak prevention

---

## M011 — Complete Architecture Comparison

**Status:** NOT STARTED

Only after the preceding research.

Compare complete architectures rather than individual technologies.

Potential comparison classes:

### Minimal

```text
Interface
 ↓
Local Model
 ↓
Simple Tools
 ↓
Human-readable storage
```

### Modular

```text
Interface
 ↓
Boss
 ↓
Routing
 ↓
Models / Workers
 ↓
Tools
 ↓
Memory
```

### Advanced

```text
Interface
 ↓
Orchestrator
 ├── Planner
 ├── Router
 ├── Models
 ├── Agents
 ├── Tools / MCP
 ├── Memory
 ├── RAG
 └── Automation
```

These are comparison frameworks, not proposed final architecture.

---

# 6. Decision State Rules

Every significant project item must have one of these states:

| State | Meaning |
|---|---|
| **REQUIREMENT** | Something the system needs to achieve |
| **HYPOTHESIS** | A proposed idea that may or may not survive research |
| **CANDIDATE** | A technology/approach being considered |
| **RESEARCH NEEDED** | Evidence is insufficient |
| **RESEARCHED** | Evidence has been gathered and recorded |
| **COMPARED** | Alternatives have been evaluated |
| **RECOMMENDATION** | A preferred option has been proposed |
| **DECIDED** | User has explicitly accepted the decision |
| **BUILD READY** | Decision is complete and implementation can begin |
| **BUILT** | Implemented |
| **VERIFIED** | Tested and confirmed |
| **RETIRED** | Replaced or deliberately abandoned |

### Critical rule

**A conversation saying "we should use X" does not make X DECIDED.**

A decision requires:

1. Relevant requirement
2. Research/evidence
3. Comparison where alternatives exist
4. Recommendation
5. Explicit user decision
6. Documentation

---

# 7. Project Records

The permanent project record should eventually contain authoritative documents such as:

```text
01_REQUIREMENTS.md
02_ARCHITECTURE.md
03_MODELS.md
04_MEMORY.md
05_HARDWARE.md
06_SOFTWARE.md
07_AGENTS_MCP.md
08_SECURITY.md
09_EXPERIMENTS.md
10_BUILD.md
11_BUILD_LOG.md
12_DECISION_LOG.md
```

The exact filenames/structure remain subject to project organisation decisions.

**Build Log owns implementation knowledge/documentation.**

There is no requirement for a separate Documentation/Knowledge chat.

---

# 8. Current Gate

```text
┌──────────────────────────────┐
│ PHASE 0                     │
│ REQUIREMENTS & RESEARCH     │
├──────────────────────────────┤
│ Hardware baseline: KNOWN    │
│ Requirements: IN PROGRESS   │
│ Research: NOT COMPLETE      │
│ Decisions: MINIMAL          │
│ Build: BLOCKED              │
└──────────────────────────────┘
```

## Current next action

**Finish Mission M001 — Requirements.**

Do not install Ollama, Open WebUI, Docker, databases, agent frameworks or other major components merely because they appeared in previous planning.

The project is intentionally starting from a clean slate.

---

# 9. Source Cleanup Note

This document is a **distillation of the previous merged conversation export**.

It intentionally removes:

- Conversation chatter
- Repeated setup statements
- Export metadata
- Duplicated architecture diagrams
- Technology shopping lists that were not decisions
- Contradictory/obsolete operational assumptions

It preserves the substantive requirements and clearly marks ideas that remain hypotheses or candidates.

Where the source material did not establish a final answer, this record does **not invent one**.
