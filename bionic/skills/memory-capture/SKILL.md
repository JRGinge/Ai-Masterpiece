# Memory Capture

## Purpose

Identify and persist durable information from the current work.

## Invocation

When explicitly invoked by the user, perform the capture operation.

Do not refuse an explicit invocation merely because context pressure is NORMAL or because a milestone has not been detected.

When invoked autonomously by Bionic, use the memory-quality rules below to determine what should be captured.

## What to capture

Prioritise:
- Important decisions
- Project state changes
- Stable requirements
- Stable user preferences relevant to future work
- Reusable solutions
- Important discoveries
- Significant failures and their lessons
- Current state required to resume a project

## What not to capture

Avoid:
- Routine conversation
- Temporary reasoning
- Repeated information
- Trivial tool output
- Information with no likely future value
- Secrets, passwords, API keys, tokens, or credentials

## Workflow

1. Review the relevant current work.
2. Identify durable information.
3. Search for an appropriate existing note if necessary.
4. Update an existing memory when possible.
5. Create a new memory only when appropriate.
6. Keep the saved information concise.
7. Verify the result.
8. Stop.

## Important

Do not use context pressure as a requirement for memory capture.

Memory capture and context compression are separate operations.

Do not automatically invoke another memory skill.

Do not perform broad vault cleanup.

Do not create unnecessary files.
