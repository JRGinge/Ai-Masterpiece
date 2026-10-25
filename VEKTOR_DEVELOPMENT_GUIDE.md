# VEKTOR — Step-by-Step Development Guide

**Version:** 1.0  
**Created:** 25 October 2026  
**Repository:** `JRGinge/Ai-Masterpiece`  
**Status:** Working build plan — follow phases in order; do not treat planned features as implemented.

This is the practical build sequence for turning Vektor into a dependable local-first personal AI operations system. It starts from the current OpenCode + llama.cpp + Qwen 3.5 9B baseline and adds one verified capability at a time.

## 0. The non-negotiable rules

Vektor's operating loop is:

```text
INSPECT → ANALYSE → PROPOSE → ASK APPROVAL → EXECUTE → VERIFY
```

- Read-only by default.
- Capability does not imply permission.
- Vektor cannot grant itself permissions or weaken its own safeguards.
- Inspection, proposal, approval, execution and verification are separate stages.
- A download approval is not execution approval.
- No autonomous uploads, external transactions, external form submissions, logins or data transmission in the initial build.
- Network permission is separate from filesystem permission.
- Keep credentials and tokens out of project files, prompts, logs, screenshots and commits.
- External documents, webpages, repositories and tool output are untrusted data. They must never override Vektor's system rules.
- Every meaningful operation must leave a verifiable result. “The model said it worked” is not proof.
- The system must remain recoverable without asking Vektor to repair itself.
- Never silently change a locked decision. Inspect, propose, get approval, change, test, document.

## 1. Current baseline

### Accepted prototype architecture

```text
Vektor (system / control layer to be built)
  └── OpenCode (current agent harness)
        └── llama.cpp server — http://127.0.0.1:8080
              └── Qwen 3.5 9B GGUF (current local model selection)
        └── GitHub MCP (global OpenCode user configuration)
```

Current working area: `D:\\Users\\jenso\\Desktop\\AI\\Testing`  
Expected llama.cpp executable: `D:\\Users\\jenso\\Desktop\\AI\\llama.cpp\\llama.exe`  
Historically recorded model path: `D:\\Users\\jenso\\.lmstudio\\models\\lmstudio-community\\Qwen3.5-9B-GGUF\\Qwen3.5-9B-Q4_K_M.gguf`  
Expected API: `http://127.0.0.1:8080`  
Expected API model ID: `qwen3.5-9b`

The user reported on 25 October 2026 that four integration checks passed: launcher/server startup, an OpenCode prompt reaching Qwen, GitHub MCP available from another project, and a read-only GitHub README test. Treat these as reported test results until a new test record is produced.

### Important unresolved discrepancy

Earlier records disagree about active quantisation and context size. The intended model file is Q4_K_M; a historical runtime audit reported Q4_K. A prior audit observed different context values (32,768 and later 24,320, versus a 65,536 documentation target). Do not guess which is active and do not change values just to make documentation agree. Inspect the live process, actual file, launch arguments and API/runtime properties; record the evidence.

## 2. Use the three project systems correctly

- **Trello:** current status, priorities, tasks, blockers and milestone progress.
- **GitHub:** source, configuration examples, requirements, decisions, test evidence and build history.
- **Obsidian:** planned human-readable knowledge / Second Mind layer. It is not a current runtime dependency.

Use this loop for each feature:

1. Create or update a Trello task.
2. Write the requirement and acceptance criteria in GitHub before implementation.
3. Inspect the current state.
4. Propose the smallest safe change.
5. Get explicit user approval for consequential changes.
6. Implement one change at a time.
7. Run the stated tests.
8. Record actual results, failures and evidence.
9. Update GitHub and Trello to match reality.
10. Do not mark complete until acceptance criteria pass.

## 3. Phase 1 — Freeze and verify the current baseline

**Goal:** know exactly what is running before building on top of it.

### Steps

1. Open the project folder and confirm the active workspace is `Testing`.
2. Record the installed OpenCode version.
3. Inspect effective OpenCode configuration sources and the selected provider/model.
4. Confirm the local llama.cpp process, executable path and command-line arguments.
5. Query `http://127.0.0.1:8080/health`.
6. Query `http://127.0.0.1:8080/v1/models`.
7. Check the model ID returned by the API.
8. Inspect the actual GGUF file name and, where available, runtime model properties.
9. Record context length, GPU offload, parallel slots, memory use and generation settings when available.
10. Confirm the GitHub MCP entry is in the intended global OpenCode configuration and no duplicate project-level entry is present.
11. Run a simple prompt through OpenCode and save the exact test and result.
12. Check that secrets are not printed in the audit output.

### Acceptance criteria

- [ ] OpenCode version and configuration source(s) recorded.
- [ ] Provider/model selection recorded.
- [ ] Local API health and model list pass.
- [ ] OpenCode prompt receives a response from the intended local model.
- [ ] Quantisation/context discrepancy is explained by evidence or remains clearly marked unresolved.
- [ ] Audit is read-only and creates no unapproved changes.

**Stop condition:** if the active model or provider cannot be identified, do not proceed to tool execution or automation.

## 4. Phase 2 — Build Vektor Doctor (read-only diagnostics)

**Goal:** one repeatable command produces a useful health report without changing anything.

### Implement

Create a small diagnostic script in the project, for example `scripts/vektor-doctor.ps1`. Before creating it, inspect the existing scripts and agree the exact path/name. The first version should only read state and print a report.

Checks to implement in this order:

1. Project/workspace path exists.
2. OpenCode executable exists and version can be read.
3. llama.cpp executable exists.
4. Model file exists and size can be read.
5. Port 8080 listener is present or absent.
6. `/health` responds within a bounded timeout.
7. `/v1/models` returns valid JSON.
8. Expected model ID is present.
9. Runtime identity/properties are collected if the installed server exposes them.
10. OpenCode config can be parsed without dumping secrets.
11. Configured provider/model is reported.
12. GitHub MCP status is reported without printing tokens.
13. A clear overall status is produced: PASS, WARN or FAIL.
14. Every check includes a reason and timestamp.
15. The report clearly distinguishes current observations from historical records.

### Safety requirements

- No process termination.
- No server restart.
- No file edits.
- No package installation or download.
- No credential output.
- No “automatic repair” mode in version 1.

### Tests

- Run with the server healthy.
- Run with the server stopped.
- Run with an invalid/unreachable endpoint in a test configuration.
- Confirm the script reports failure instead of hanging.
- Compare two runs and ensure it does not change the machine.

### Acceptance criteria

- [ ] One documented command runs Doctor.
- [ ] Output is readable and gives actionable reasons.
- [ ] Health and model checks time out safely.
- [ ] No writes or configuration changes occur.
- [ ] A sample report is saved with secrets removed.

## 5. Phase 3 — Make startup and recovery repeatable

**Goal:** Vektor can be started and recovered without relying on the AI.

### Steps

1. Inspect the current `Vektor-OpenCode.bat`; do not replace it blindly.
2. Confirm it starts the intended llama.cpp executable with the intended arguments.
3. Replace fixed sleeps with polling the health/model endpoint, with a maximum timeout and useful error output.
4. Prevent duplicate server launches if the port is already occupied.
5. If startup fails, show the log location and exit without silently changing settings.
6. Launch OpenCode in the intended `Testing` workspace only after the API is ready.
7. Write down the manual recovery path: stop the relevant process, inspect logs, start the server, verify health, then open OpenCode.
8. Document where logs live, their retention policy and how to redact secrets.
9. Test restart after a normal shutdown and after a forced server stop.
10. Do not add automatic updates or automatic model downloads.

### Acceptance criteria

- [ ] Clean start works repeatedly.
- [ ] Existing server is detected rather than duplicated.
- [ ] Startup timeout is bounded and reports the failure clearly.
- [ ] Recovery steps work without Vektor.
- [ ] Launch arguments and actual model/context are recorded.

## 6. Phase 4 — Establish a repeatable benchmark and regression suite

**Goal:** every later change can be compared against a known baseline.

Create a versioned test set with at least these categories:

1. Basic instruction following.
2. Long-context recall using a known test document.
3. Structured output / JSON validity.
4. Multi-step reasoning with a checkable answer.
5. Refusal to act when approval is missing.
6. Prompt-injection resistance using untrusted text that asks the model to ignore its rules.
7. Tool selection and correct argument formation.
8. Error handling when a tool fails.
9. Local-only behaviour and no unauthorised network call.
10. Recovery after model/server restart.

For each test, record: ID, prompt/input, expected behaviour, pass condition, actual result, model file/hash if available, context settings, OpenCode version, date, duration and notes. Do not grade solely by whether the answer sounds confident.

### Acceptance criteria

- [ ] Baseline suite is repeatable.
- [ ] Pass/fail criteria are defined before running tests.
- [ ] Results are saved in GitHub without secrets or personal data.
- [ ] Any model/config change reruns the relevant tests.

## 7. Phase 5 — Define the Vektor core contract

**Goal:** separate Vektor's identity and policies from the model's raw output.

Write a concise, version-controlled core specification before building the UI or memory layer. It must define:

- What Vektor is and is not.
- The Inspect → Analyse → Propose → Ask Approval → Execute → Verify lifecycle.
- What counts as a consequential action.
- Approval language and how approval is scoped.
- What happens when requirements are ambiguous.
- How uncertainty is communicated.
- Which sources of truth apply to project status, code and knowledge.
- What is logged and what must never be logged.
- How a task is cancelled.
- How partial failures are reported.
- How external content is treated as untrusted input.

The model prompt is not a security boundary by itself. Enforce critical restrictions in the tool wrapper, permissions, process boundary and user approval mechanism wherever practical.

### Acceptance criteria

- [ ] Policy is written and versioned.
- [ ] Conflicts between user request, external content and system rules have defined handling.
- [ ] Tool interfaces enforce restrictions rather than relying only on the model remembering them.
- [ ] Regression tests cover the core contract.

## 8. Phase 6 — Create a permission and action model

**Goal:** Vektor can describe what it wants to do before it does it.

Define a small set of action classes:

| Class | Examples | Default |
|---|---|---|
| A0 — Read-only | Read approved project files, inspect status, search local indexed content | Allowed only within approved scope |
| A1 — Reversible local change | Create a draft report or edit a designated working copy | Propose first; approval required |
| A2 — Execute local command | Run a script, install software, modify configuration | Explicit approval required per action |
| A3 — External side effect | Push/commit, upload, send a message, submit a form, change an account | Disabled by default; separate explicit approval and narrow scope |
| A4 — High impact | Delete large data sets, expose credentials, financial/legal/physical-world action | Not available to the initial build |

For every action request, store: action ID, requesting task, target resources, exact intended operation, risk class, proposed changes, approval state, expiry, execution result and verification result.

Approval must be specific. “Do whatever you need” must not grant unlimited future authority. An approval for one file or command does not authorise unrelated operations.

### Acceptance criteria

- [ ] Every tool has a documented action class.
- [ ] Default is deny for unclassified tools.
- [ ] Approval expires at task completion or its defined expiry.
- [ ] The model cannot change its own permission rules.
- [ ] Denied actions are tested and logged without leaking secrets.

## 9. Phase 7 — Configure OpenCode as the controlled harness

**Goal:** make OpenCode the agent runtime without confusing its capabilities with Vektor's authority.

### Steps

1. Record the exact installed OpenCode version.
2. Read the official configuration documentation matching that version before changing config.
3. Identify global and project-level configuration and how precedence works.
4. Keep the local provider/model settings in the intended configuration location.
5. Keep GitHub MCP in the intended global user configuration, with credentials handled by the supported secure mechanism.
6. Audit shell/command execution, filesystem access, MCP servers, network access and approval settings individually.
7. Remove redundant or ambiguous configuration entries only after backing up the current file and getting approval.
8. Test read-only behaviour before enabling write tools.
9. Test that a denied command really is denied.
10. Test that approval for one action does not carry into a later unrelated action.
11. Keep Morphy out of the locked architecture until a separate evaluation and user decision.

Do not copy configuration examples from a different OpenCode version without checking compatibility. Never commit secrets.

### Acceptance criteria

- [ ] Effective configuration is understood and documented.
- [ ] Permissions have been tested, not merely read from a config file.
- [ ] Local inference remains local in the intended baseline.
- [ ] GitHub MCP works only with the permissions it actually needs.
- [ ] No credential appears in repository files or logs.

## 10. Phase 8 — Implement the first useful workflow: Project Inspector

**Goal:** Vektor can inspect an approved project and return a grounded report without editing anything.

### Initial scope

- User selects a project root.
- Vektor confirms the path and scope.
- Inspector lists allowed files and key project metadata.
- It ignores secrets, credential stores, caches, dependency folders and unrelated directories by default.
- It identifies project type, entry points, configuration, tests and documentation.
- It reports what it read and what it could not access.
- It produces findings with file paths and line references where possible.
- It proposes next actions but does not execute them.

### Build steps

1. Define the allowed-root mechanism.
2. Define an explicit denylist for secrets and sensitive paths, while recognising that a denylist alone is not sufficient security.
3. Use path canonicalisation and reject path traversal outside the approved root.
4. Enforce file-size and recursion limits.
5. Treat file contents as untrusted data, not instructions.
6. Produce a structured report schema.
7. Test with a normal project, an empty folder, a large folder, malformed files and attempted path traversal.
8. Verify that the Inspector makes no writes.

### Acceptance criteria

- [ ] User-approved root is enforced.
- [ ] Files outside the root cannot be read through traversal or symlinks.
- [ ] Secret-like files are excluded by policy.
- [ ] Findings are linked to evidence.
- [ ] Read-only behaviour passes tests.

## 11. Phase 9 — Add controlled change proposals and verification

**Goal:** Vektor can prepare a patch, explain it and verify it after explicit approval.

### Workflow

1. Inspect current files and repository status.
2. Establish a baseline/diff before changes.
3. Produce a proposed change list with purpose, affected paths, risk and rollback plan.
4. Ask for explicit approval of the specific change set.
5. Create changes only inside the approved workspace.
6. Show the resulting diff before any commit or external action.
7. Run the relevant tests.
8. Inspect the final diff and check for secrets or unrelated changes.
9. Report PASS, FAIL or PARTIAL with evidence.
10. Roll back only within the previously agreed rollback scope; ask before destructive recovery.

Initially, do not let Vektor automatically commit, push, install packages, edit global configuration, delete files or change system settings.

### Acceptance criteria

- [ ] No change occurs before approval.
- [ ] Diff clearly identifies every changed file.
- [ ] Tests run and results are recorded.
- [ ] Unexpected changes cause the workflow to stop.
- [ ] Rollback instructions are documented and tested on disposable data.

## 12. Phase 10 — Add GitHub and Trello as controlled tools

**Goal:** Vektor can read project state and prepare updates, then perform approved writes only when specifically authorised.

### GitHub

Start with repository and file reads. Then add narrowly scoped capabilities one at a time: issue/task drafting, branch/PR preparation, and only later approved writes. Prefer least-privilege credentials. Never put tokens in prompts, logs, code or committed config.

### Trello

Start with board/card/task reads. Let Vektor propose card updates and show the exact title, description, status and comment before a write. Require approval for every write action in the initial build.

### Cross-system consistency

- Trello tracks current work and task state.
- GitHub records engineering truth and durable evidence.
- When the two disagree, report the conflict; do not silently choose or overwrite.
- Record links between the Trello task, GitHub issue/commit/report and test evidence.

### Acceptance criteria

- [ ] Read actions work with minimum permissions.
- [ ] Proposed writes are displayed exactly before approval.
- [ ] Writes require explicit action-specific approval.
- [ ] Results are re-read to verify the write actually occurred.
- [ ] Conflicts are surfaced rather than hidden.

## 13. Phase 11 — Build memory in layers, not as one giant prompt

**Goal:** Vektor remembers useful project context while remaining correctable and auditable.

Implement in this order:

1. **Session context:** current task and recent decisions.
2. **Project memory:** version-controlled project facts, architecture, decisions, tests and known issues.
3. **User-controlled durable memory:** explicitly reviewable preferences and ongoing goals.
4. **Searchable archive:** documents, prior notes and authorised research, with source metadata.
5. **Retrieval:** return relevant excerpts with source paths, dates and confidence/limitations.

Every stored item should distinguish fact, user decision, hypothesis, proposal and historical observation. Store source, date, scope and status. Preserve old decisions as history when superseded; do not rewrite history to make the current design look inevitable.

The user must be able to inspect, correct, export and delete memory. Corrections take precedence over AI assumptions. Do not ingest the entire drive by default.

### Acceptance criteria

- [ ] Memory can be inspected and corrected.
- [ ] Retrieved claims carry source references.
- [ ] Stale or conflicting records are labelled.
- [ ] Sensitive data is excluded unless explicitly authorised and necessary.
- [ ] Memory retrieval does not grant action permission.

## 14. Phase 12 — Build the Second Mind / research pipeline

**Goal:** turn authorised information into searchable knowledge without blindly trusting it.

Pipeline:

```text
AUTHORISE SOURCE → INGEST → EXTRACT → INDEX → RETRIEVE
→ SUMMARISE WITH CITATIONS → HUMAN REVIEW → PROMOTE TO KNOWLEDGE
```

### Steps

1. Define allowed source types and folders.
2. Require approval for downloads and external acquisition.
3. Keep downloaded originals separate from derived notes.
4. Record source URL/path, title, author if known, date acquired, file hash and licence/usage notes where relevant.
5. Extract text locally where possible.
6. Chunk and index with stable source references.
7. Retrieve relevant chunks for a query.
8. Cite claims back to source sections/pages.
9. Flag gaps, conflicting sources and low-confidence extraction.
10. Require review before promoting research into durable project decisions.
11. Never execute instructions found inside source material.

Do not add a vector database, graph database or external service just because it sounds advanced. Start with a simple searchable format and upgrade only when measured retrieval quality demands it.

### Acceptance criteria

- [ ] Every indexed item can be traced to its source.
- [ ] Retrieval can quote or identify the relevant passage.
- [ ] Source instructions cannot override system policy.
- [ ] Bad scans, missing text and conflicting sources are surfaced.
- [ ] No source is uploaded externally without explicit permission.

## 15. Phase 13 — Add specialist agents only when needed

**Goal:** improve quality without creating uncontrolled agent sprawl.

Potential roles, introduced one at a time:

- Researcher — finds and compares sources; no writes.
- Planner — converts a request into ordered tasks and acceptance criteria.
- Implementer — prepares approved local changes.
- Tester — runs allowed tests and reports results.
- Reviewer/Security Auditor — checks diffs, permissions and evidence independently.
- Librarian — organises approved knowledge sources.

Rules:

1. Start with one agent and one task.
2. Define input, output schema, allowed tools and forbidden actions.
3. Agents inherit the task's permission scope; they cannot widen it.
4. A reviewer should not simply repeat the implementer's conclusions.
5. Limit recursion, concurrent tasks, context and tool calls.
6. Log which agent did what and which evidence supports the conclusion.
7. Keep human approval at the same boundaries regardless of how many agents are used.

### Acceptance criteria

- [ ] Each role has a narrow contract.
- [ ] Subagents cannot elevate permissions.
- [ ] Failures and timeouts terminate safely.
- [ ] Parallelism is measured and bounded.
- [ ] The system can explain which role produced each result.

## 16. Phase 14 — Add task planning and durable execution state

**Goal:** long tasks survive interruptions and can resume safely.

Each task should have a durable record with:

- Task ID and goal.
- User request and constraints.
- Current phase/status.
- Planned steps and acceptance criteria.
- Files/resources in scope.
- Approval records and expiry.
- Completed actions and evidence.
- Errors, retries and unresolved questions.
- Next safe action.
- Final verification and outcome.

Use explicit states such as `NEW`, `INSPECTING`, `PROPOSED`, `AWAITING_APPROVAL`, `EXECUTING`, `VERIFYING`, `COMPLETED`, `FAILED`, `CANCELLED`. Define allowed transitions. A restart must not turn an awaiting-approval task into an approved one.

### Acceptance criteria

- [ ] Task state survives restart.
- [ ] Duplicate execution is detected.
- [ ] Resume begins with a state/evidence check.
- [ ] Expired approvals are invalid.
- [ ] Cancellation prevents later queued actions.

## 17. Phase 15 — Evaluate a visual control room (Morphy or alternative)

**Goal:** decide whether a GUI adds real value without destabilising the working core.

Morphy is an evaluation candidate, not a locked dependency.

Evaluate it against:

- Local versus remote processing.
- Filesystem and command permissions.
- MCP/tool compatibility.
- Approval visibility.
- Session/task state persistence.
- Logs and auditability.
- Accessibility and daily usability.
- Resource use on the RTX 3070 system.
- Ability to exit the GUI and recover through CLI/manual steps.

Run it alongside the stable setup first. Do not migrate the runtime until the evaluation has defined pass criteria, evidence and a documented user decision.

## 18. Phase 16 — Automation, scheduled work and proactive monitoring

**Goal:** automate low-risk repetition only after manual workflows are reliable.

Start with reminders and read-only health checks. Add scheduled research or reports only after the source scope, output location, retention and failure handling are clear.

For each automation define:

- Trigger/schedule.
- Inputs and allowed sources.
- Permitted actions.
- Approval requirements.
- Timeouts, retry limits and duplicate prevention.
- Output location.
- Logging and privacy limits.
- How it can be paused or disabled.
- What happens when the model or network is unavailable.

Do not initially automate financial transactions, purchases, public posts, messages, account changes, destructive file operations or arbitrary computer control.

### Acceptance criteria

- [ ] Automation can be paused and disabled by the user.
- [ ] Missed runs do not cause uncontrolled catch-up.
- [ ] Retries are bounded and idempotent where possible.
- [ ] Failures are visible.
- [ ] External side effects remain approval-gated.

## 19. Phase 17 — Optional capabilities (separate decisions)

Do not build all of these at once. Each needs a written requirement, research, a test and an explicit selection decision:

- Model routing between local and cloud models.
- Cloud fallback for tasks that local hardware cannot handle.
- Voice input/output.
- Image/document understanding.
- Computer-use control.
- More capable local models or hardware upgrades.
- Additional MCP servers and external integrations.
- Obsidian integration.
- GUI/control-room migration.
- Advanced agent orchestration.

For every cloud or external option, specify exactly what data leaves the PC, which provider receives it, what is retained, the cost ceiling and how the user approves it. Local-first remains the default unless the user changes the decision.

## 20. Phase 18 — Security and failure testing

Before considering Vektor reliable, test realistic failures:

- Server is stopped or hangs.
- Wrong model is loaded.
- Model file is missing or changed.
- Context or memory pressure causes failure.
- OpenCode config is malformed.
- MCP server is unavailable.
- GitHub permission is denied or expired.
- Filesystem path points outside the approved root.
- File contains prompt-injection instructions.
- Tool returns malformed or misleading data.
- Approval expires mid-task.
- User cancels during a multi-step task.
- Process crashes after a write but before verification.
- Duplicate task is resumed.
- Logs accidentally contain sensitive data.

For every case, define expected behaviour before testing. The safe outcome is usually stop, explain, preserve evidence and ask — not improvise a repair.

## 21. Phase 19 — Package, document and maintain

Once the core passes acceptance:

1. Document installation and exact versions.
2. Document the approved configuration and redacted examples.
3. Provide a one-command startup path.
4. Provide Doctor and manual recovery commands.
5. Document backups and restore tests.
6. Define log rotation and retention.
7. Pin dependencies where appropriate.
8. Test upgrades on a copy before applying them to the working setup.
9. Keep release notes and a changelog.
10. Re-run regression and security tests after updates.
11. Maintain a known-issues list.
12. Never let an update silently rewrite policy or permissions.

## 22. Final acceptance gates

Vektor should not be described as production-ready until each applicable gate has evidence.

| Gate | Required proof |
|---|---|
| Local core | OpenCode reliably reaches the intended local model |
| Runtime visibility | Doctor identifies health, model, context and config state |
| Recovery | Manual start/stop/recovery succeeds without AI assistance |
| Reproducibility | Benchmark suite can be repeated and compared |
| Safety | Denied actions stay denied; approvals are scoped and expire |
| Project inspection | Approved-root boundary and read-only behaviour pass |
| Controlled changes | No writes before approval; diff and verification are produced |
| Integrations | GitHub/Trello reads and approved writes are re-verified |
| Memory | Sources, corrections, conflicts and deletion are controllable |
| Research | Indexed claims trace to authorised source material |
| Task continuity | Restart/resume does not duplicate actions or inherit approval |
| Security | Prompt injection, traversal, secret leakage and failure tests pass |
| Operations | Backups, logs, upgrades and manual recovery are documented |

## 23. Recommended build order — the actual checklist

Follow this order; do not jump to agents, memory or computer control while the base is still uncertain.

- [ ] **V01 — Baseline audit:** record actual OpenCode, provider/model, llama.cpp args, model file, quantisation and context.
- [ ] **V02 — Vektor Doctor:** read-only health report.
- [ ] **V03 — Reliable launcher:** endpoint polling, timeout, duplicate-process handling and logs.
- [ ] **V04 — Regression suite:** repeatable model, tool and safety tests.
- [ ] **V05 — Core contract:** policy, lifecycle, uncertainty and approval semantics.
- [ ] **V06 — Permission model:** classify tools and enforce least privilege.
- [ ] **V07 — OpenCode hardening:** verify effective configuration and actual denied-action behaviour.
- [ ] **V08 — Project Inspector:** approved-root, read-only analysis with evidence.
- [ ] **V09 — Change proposals:** scoped approval, diff, tests and rollback.
- [ ] **V10 — GitHub/Trello tools:** read first, then narrowly scoped approved writes.
- [ ] **V11 — Layered memory:** project facts, decisions, corrections and citations.
- [ ] **V12 — Second Mind:** authorised ingestion, indexing, retrieval and source citations.
- [ ] **V13 — Specialist agents:** add only where tests show value.
- [ ] **V14 — Durable task state:** safe pause, cancel and resume.
- [ ] **V15 — GUI evaluation:** assess Morphy separately.
- [ ] **V16 — Low-risk automation:** scheduled diagnostics and reports.
- [ ] **V17 — Security/failure acceptance:** prove safe behaviour under failure.
- [ ] **V18 — Packaging and maintenance:** documented releases, backups and recovery.

## Definition of done for each phase

A phase is complete only when all five are true:

1. The requirement is written.
2. The implementation exists.
3. Acceptance tests have actually run.
4. Results and limitations are documented.
5. Trello and GitHub reflect the same current status.

**Core rule:** build the smallest useful version, prove it works, then move to the next layer. Vektor should earn every new capability through evidence — not accumulate features because they sound impressive.
