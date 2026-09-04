# Research Centre — Branch 02

**Status:** Partial — visible project-context extraction

## Purpose

This branch continued the Research Centre requirements work, refining the AI's security, permissions, memory, learning and operating boundaries.

> This is a consolidated extraction from the project material available in the current context, not a claim to be a complete raw transcript of the branch.

## Key Requirements

### Adaptive permissions

The permission model should adapt to risk and task type rather than granting unrestricted autonomy.

- Low-risk/trusted operations may be permitted within defined scope.
- Higher-risk or external operations require stronger approval.
- Security is a separate control layer.
- The AI cannot grant itself permissions.

### Local-first initial operation

The initial system should operate locally. External connections should be introduced only after the relevant security and permission model has been researched and approved.

### Explicit execution control

The AI must never execute a consequential action merely because it identified that action as useful.

> **No execution without explicit user authority.**

This applies especially to system changes, external actions and other consequential operations.

### Project-folder inheritance

When the user grants the AI authority over a project folder, that authority should inherit to its contents unless something is explicitly protected.

Secrets remain separately controlled.

### File operations

Safe project-file operations can be permitted within the authorised scope. Operations outside that scope require approval.

### Security appraisal

Higher-risk operations and broader external access should pass through an appropriate security appraisal before being enabled.

### Autonomous uploads

The AI should not upload files or user data autonomously at this stage.

### Security assistance

A dedicated security skill/agent may help analyse or configure security controls, but it does not receive authority to change those controls without explicit user permission.

## Apprentice Behaviour

The AI should behave like an apprentice:

> **If it doesn't know, search. If it still doesn't know, ask.**

It should:

- Research when information is readily researchable.
- Never knowingly guess.
- Ask the user when the answer depends on information only they can provide.
- State uncertainty when research cannot establish an answer.
- Learn from explicit corrections.

## Correction Principle

Explicit user corrections should override AI assumptions.

Where a correction is important, the system should preserve the historical mistake and record the corrected current state rather than silently erasing the history.

Related knowledge based on the incorrect assumption should be checked where appropriate.

## Decision History

Important decisions must retain:

- What was decided
- Why
- Alternatives considered
- Research/evidence
- Experiments and benchmark results
- Consequences
- Date/context
- Conditions that would justify revisiting the decision

A previous decision is not permanently correct merely because it was previously made. The system should be able to identify when the assumptions behind a decision have changed and recommend reconsideration.

## Not Inferred

This branch does **not** establish:

- A final operating system
- A final model/runtime
- A final orchestration framework
- A final database/vector store
- A final agent implementation
- Unrestricted computer control
- Autonomous external actions
- Autonomous file uploads

Those remain research/architecture decisions.

## Relationship to Canonical Requirements

The branch reinforces the project's existing requirements around local-first operation, explicit permissions, security appraisal, project-folder inheritance, controlled external access, persistent decision history, source-aware learning and apprentice-style uncertainty handling.
