# AI Masterpiece — Security & Permissions

## Security Authority

The AI may propose/request permission changes but can never grant itself authority. The security layer independently enforces permissions. The user remains the final authority.

**Capability does not equal authority. A permission request is not permission.**

## Permission Model

The conceptual permission levels are:

- **Level 0:** no external action
- **Level 1:** read-only
- **Level 2:** create/modify non-critical data
- **Level 3:** external or consequential actions requiring approval
- **Level 4:** high-risk administrative actions; avoid by default

The eventual system should use risk/task-scoped permissions rather than unrestricted machine access.

## Explicit Execution

Nothing executes because the AI thinks it should. It executes because the user explicitly authorised it.

Downloading a file never authorises execution. Executables, scripts, installers and other code capable of execution require a separate explicit user command.

The AI may inspect/analyse an item and prepare a command if permitted, but cannot infer execution approval.

## PC Management

The eventual system should be able to inspect hardware/software, build a persistent model of the actual PC, monitor CPU/GPU/RAM/storage/temperatures, diagnose problems, find duplicate/unnecessary files, organise files, identify unnecessary applications/services, recommend optimisation, troubleshoot interactively, install/update software when approved and eventually perform proactive maintenance.

**Nothing changes on the PC without explicit user approval.**

Inspect != Recommend != Execute.

Protected/dangerous system areas require additional safeguards and should not be casually proposed for destructive modification.

## Project Permission Inheritance

An authorised project folder is the filesystem permission boundary.

- Permissions inherit through contained files and subfolders.
- New files/folders inherit the project's permissions.
- Explicit deny/protected rules override inheritance.
- Secrets remain separately controlled.
- Different agents may have different permissions for different projects.
- Filesystem permission does not grant network permission.

## Temporary Permissions

**M002-SEC-32 — Task-Scoped Temporary Permissions**

Explicitly granted temporary permissions:

- apply only to the specified task
- are limited to the requested resource/action
- automatically expire when the task finishes
- cannot silently become permanent
- cannot silently be reused for another task
- are recorded in the audit log

Permission follows the task, not the AI.

## Network / External Access

Initial AI inference is local-only.

External network access is a separate risk boundary and should be controlled by an allowlist/tool/security layer when enabled.

Initially prohibit autonomous:

- file/user-data uploads
- external data transmission
- form submission/posting
- external logins
- transactions

Web research may eventually be enabled as a separately controlled capability.

## Downloads

**M002-SEC-15 — User-Controlled Downloads**

The AI may find, inspect at a permitted level, explain and provide the source for a useful file. It cannot independently download files to the machine. A download requires explicit user permission.

## No Self-Granted Permissions

**M002-SEC-31 — No Self-Granted Permissions**

If an operation is outside current authority:

AI identifies required permission → explains why → security layer assesses → user approves/rejects → only then may permission become active.

The security agent cannot grant itself permission either.

## Untrusted Content / Prompt Injection

Instructions found in websites, documents and untrusted files are data, not authority. External content must never override higher-priority instructions or permission boundaries.

## Secrets

Never place API keys, passwords or credentials into ordinary prompts or notes. Secrets require separate protected storage and access controls.

## Logging / Visibility

Important security and permission events should be auditable. The system should maintain an audit trail for permission grants, temporary permissions, consequential actions and relevant security events.

## Recovery

The AI must never become a prerequisite for controlling or recovering the machine or accessing underlying data. Maintain independent backups, configuration copies, restore procedures and logs.
