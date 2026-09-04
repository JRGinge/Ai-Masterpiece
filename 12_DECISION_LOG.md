# AI Masterpiece — Decision Log

Important decisions must retain context.

## Decision Record
- ID
- Date
- Decision
- Status
- Why
- Alternatives considered
- Research/evidence
- Experiments/benchmarks
- Consequences
- Revisit conditions

## Established Decisions

### D001 — Existing Hardware First
Use the current PC initially. Upgrade only when measured workload limitations justify it.

### D002 — Incremental Build
Build in phases and prove each layer before adding unnecessary complexity.

### D003 — Portable Data
Prefer human-readable and portable formats where practical.

### D004 — Local-Only Initial AI
Initial inference remains on local hardware; no cloud LLM fallback.

### D005 — Explicit Execution Authority
The AI never executes consequential actions merely because it believes they are useful. Explicit authority is required.

### D006 — Adaptive Permissions
Permissions are risk/task scoped. Higher-risk or external actions require stronger controls.

### D007 — Project Permission Inheritance
Authorised project-folder permissions inherit to contained files/subfolders unless explicitly protected. Network access remains separate.

### D008 — No Autonomous Uploads Initially
The initial system does not independently upload files/user data, submit forms, log in externally or transact.

### D009 — User-Controlled Downloads
Downloads require explicit user permission.

### D010 — Separate Execution Approval
Download approval never implies execution approval.

### D011 — Task-Scoped Temporary Permissions
Temporary permissions expire when the authorised task finishes and are logged.

### D012 — User Authority Over Memory
The user can inspect, edit, correct, delete and reorganise persistent memory. User corrections outrank AI assumptions.

### D013 — Raw Archive + Active Knowledge
Historical records are preserved while active knowledge can evolve without silently destroying history.

### D014 — Apprentice Behaviour
If the AI does not know, it researches when appropriate; if still uncertain, it asks or states that it does not know. No knowingly fabricated answers.

### D015 — Recovery Independence
The AI must never become a prerequisite for controlling or recovering the machine or accessing the underlying data.

### D016 — Security Layer Independent From AI
The model can request permission but cannot grant itself permission.

### D017 — Research Provenance
Important research and technical conclusions retain sources/evidence and historical reasoning.
