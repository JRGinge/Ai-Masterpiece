# Context Monitor

## Purpose

Assess the current working context and determine whether context-management intervention is appropriate.

This skill does not directly measure token usage unless the environment provides that information.

## Decision

Return exactly one:

- NORMAL — continue normally.
- ELEVATED — continue, but avoid unnecessary context growth.
- HIGH — context management should be performed soon.
- CRITICAL — preserve important state and reduce context before continuing substantial work.

## If exact context information is available

Use it.

Do not invent token counts or percentages.

## If exact context information is unavailable

Assess qualitatively using:
- Length and complexity of the current task
- Amount of accumulated tool output
- Number of major task stages completed
- Amount of outdated or repetitive conversation
- Whether important state is becoming difficult to track

Do not use workspace cleanliness, file count, or task existence as a substitute for context usage.

## Important

This is an assessment skill only.

Do NOT:
- Create files
- Modify Obsidian
- Capture memory
- Consolidate memory
- Compress context
- Retrieve memory
- Invoke another skill

Return the decision and a short reason, then stop.
