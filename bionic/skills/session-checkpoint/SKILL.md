# Session Checkpoint

## Purpose

Persist the minimum information required to resume the current task later.

## Invocation

When explicitly invoked by the user, perform the checkpoint operation.

When invoked autonomously, use it for long-running work, major milestones, or when context management requires a durable recovery point.

## Save

Record only:
- Objective
- Current state
- Decisions
- Important discoveries
- Unresolved problems
- Next action
- Relevant files/resources

## Workflow

1. Identify the minimum durable continuation state.
2. Update an existing project/session note when possible.
3. Create a new note only when necessary.
4. Verify the checkpoint was written successfully.
5. Stop.

## Rules

Do not save the entire conversation.

Do not reorganise the vault.

Do not perform unrelated cleanup.

Do not automatically invoke another memory skill.
