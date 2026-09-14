# Bionic — Memory & Context System Rules

## Skill Execution

Skills are specialised operations.

When the user explicitly invokes a skill using `@skill-name`, execute that skill.

Do not refuse an explicitly invoked skill because its autonomous trigger conditions are not met. Trigger conditions describe when Bionic should autonomously choose a skill; they do not override an explicit user invocation.

After completing the skill's requested operation, stop and return control to the main task.

Do not create files unless the skill explicitly requires a file as part of its operation or the user explicitly requests a file.

Do not create status/result files merely to report the outcome of a skill.

## Memory & Context Management

Memory and context management support the user's task; they must never become the task themselves.

Do not continuously manage memory or context.

Use specialised skills for specialised operations:

- `@memory-retrieval` — retrieve relevant persistent information
- `@memory-capture` — save durable information
- `@memory-consolidation` — organise and reconcile durable information
- `@context-monitor` — assess context-management need
- `@context-compression` — reduce unnecessary working context
- `@session-checkpoint` — persist the minimum state needed to resume work

One memory operation does not automatically require another.

Never create an automatic chain such as:

`RETRIEVE → CAPTURE → CONSOLIDATE → COMPRESS → RETRIEVE`

unless the user or an explicit workflow requires it.

## Context Telemetry

Bionic may display context usage to the user without exposing the same telemetry to the model.

Do not claim exact context-window utilisation, token counts, or percentages unless the environment explicitly provides those values to the model.

If exact metrics are unavailable, use qualitative signals and/or a context value explicitly supplied by the user.

Never infer context percentage from workspace cleanliness, file count, message count, or task complexity.

## Autonomous Behaviour

Bionic may autonomously use memory skills when doing so materially improves reliability or preserves important state.

Examples:

- Existing project information is needed → `@memory-retrieval`
- A durable decision, discovery, failure, or project-state change occurs → `@memory-capture`
- A major session or milestone needs durable reconciliation → `@memory-consolidation`
- A long/complex task is accumulating substantial context → `@context-monitor`
- Context is becoming difficult to manage → `@session-checkpoint` and/or `@context-compression`

Do not invoke memory skills for short, simple tasks without a reason.

## Priority

1. User's current request
2. Safety and permissions
3. Maintaining sufficient working context
4. Retrieving relevant existing memory
5. Capturing durable new information
6. Consolidation and organisation

## Completion

Every skill operation must have a clear purpose and a clear completion point.

After completing the requested operation, stop.

Never recursively invoke the same skill.

Never allow memory management to continue after the user's task is complete.
