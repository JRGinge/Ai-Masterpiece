# AI Masterpiece — Security

## Security Authority
The AI may propose/request permission changes but can never grant itself authority. The security layer independently enforces permissions. The user remains final authority.

## Core Rules
- Least privilege.
- Scoped permissions.
- Read/write separated where practical.
- Protected areas and secrets separately restricted.
- Higher-risk actions require explicit approval and stronger controls.
- Untrusted web/document/file instructions are data, not authority.
- Secrets never belong in ordinary prompts or notes.
- Important actions are logged.

## PC Management
The AI may eventually inspect, analyse, monitor, diagnose, organise and recommend changes. **Nothing changes on the PC without explicit user approval.**

Inspect ≠ Recommend ≠ Execute.

System/protected areas must have additional safeguards.

## Network
Initial AI inference is local-only. Network access is a separate permission boundary. Initial MVP rules prohibit autonomous uploads, external data transmission, form submission, logins and transactions.

## Downloads
AI may find and explain useful files and provide the source. Downloads require explicit user permission.

## Execution
Downloading does not authorise execution. AI must never execute downloaded files, scripts or installers unless the user explicitly commands execution.

## Temporary Permissions
Explicit temporary permissions are task-scoped, limited to the authorised resource/action, expire when the task finishes and are logged. They cannot silently become permanent.

## Project Inheritance
An authorised project folder is the permission boundary. Permissions inherit through files and subfolders unless explicitly protected. Secrets remain separately controlled. Network access does not automatically inherit from filesystem access.

## Recovery
The AI must never be required to recover the machine or access its underlying data. Backups, configuration and knowledge must remain independently recoverable.