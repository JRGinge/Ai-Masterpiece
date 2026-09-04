# AI Masterpiece — Memory & Second Mind

## Core Principle

> Remember broadly. Retrieve selectively. Preserve history. Protect meaning.

The system requires a persistent second mind with selective retrieval rather than dumping complete history into model context.

## Layers

- **Raw Archive:** authorised historical conversations, research, sources, decisions, memory changes, audit history and historical project states.
- **Active Knowledge:** current useful knowledge that can evolve without destroying history.
- **Personal Memory:** authorised facts, preferences, interests, projects, working habits and useful personal context.
- **General Knowledge:** research and concepts, clearly distinguished from personal memory.
- **Project Knowledge:** architecture, requirements, decisions, tests and build history.
- **Entities / Concepts:** structured knowledge units.
- **Relationships:** links between entities, projects, concepts, decisions and research.
- **Inbox:** uncertain or semantically important items awaiting review.
- **Retrieval:** relevant context only.

Archive != active knowledge != model context.

## Memory Authority

The user retains ultimate authority over persistent memory.

The user must be able to:

- Inspect
- Edit
- Correct
- Delete
- Reorganise
- Approve/reject uncertain information

User-authored corrections outrank AI-generated assumptions.

## Confidence and Provenance

Useful states include:

- User confirmed → trusted
- Strongly supported / research verified → appropriately trusted
- Uncertain → Inbox / needs confirmation
- AI inference → explicitly labelled
- Forgotten → excluded from normal retrieval

Important knowledge should retain source/evidence, date, confidence, related conversation/document/research, related decisions and experiments where practical.

The system should be able to answer **“Why do you think this?”** with supporting evidence or context.

## Importance

The AI may assess importance using factors such as frequency, dependencies, impact on decisions, active projects, importance to the user, usefulness to the Second Mind and retrieval/reference frequency.

**Importance != confidence.** An important uncertain item remains uncertain.

## Freshness

Track freshness selectively for information likely to change: current hardware, project status, software recommendations and changing technical information. Stable information need not receive active freshness tracking.

**Stale != false.** Historical information remains available.

## Time-Aware History

When information changes:

1. Keep the previous value.
2. Record the new value.
3. Record when it changed.
4. Record why it changed.
5. Record its source/evidence.
6. Mark the current active value.
7. Preserve the historical state.

The system must not silently rewrite history.

## Forgetting

When the user says to forget something, remove it from normal retrieval and mark it Forgotten/Deleted. Preserve historical/audit information where appropriate. Hard deletion is a separate explicit operation when required for privacy or legal reasons.

## Knowledge Organisation

The AI may autonomously perform low-risk organisational work on trusted knowledge:

- create/update notes
- add links
- update relationships
- reorganise structure
- improve metadata
- rename notes without changing meaning
- consolidate redundant information
- maintain indexes/navigation

Organisation may be autonomous. **Meaning is protected.** Changes to factual claims, confidence, interpretation, important relationships or important conclusions should go through Inbox/review.

## Contextual Retrieval

Retrieval should consider:

- Relevance
- Trust
- Recency
- Importance
- Current context

Interlinked documents/entities should allow the system to follow useful relationships instead of injecting large unrelated amounts of information into context.

## Deduplication

Duplicate knowledge should generally be consolidated while preserving provenance. Genuinely different claims must remain separate. Never merge away meaningful nuance.

## Research Knowledge

Research records should preserve:

- Original research/findings
- Sources/links
- Date researched
- Last verified
- Freshness/volatility
- Current confidence
- Importance
- Reverification policy
- Related decisions/experiments

Evaluate evidence rather than treating source categories as automatically equal. When credible sources disagree, compare claim definitions, methodology, dates, conditions and evidence; research further where useful; preserve the disagreement when unresolved.

When new evidence changes a conclusion, preserve the old conclusion as historical and make the new conclusion current while recording what changed, when, why and the supporting evidence.

## Authorised Learning

The AI may process authorised books, PDFs, videos, papers, GitHub repositories, courses, notes and documents. It should extract useful information, concepts, entities and relationships; connect them to existing knowledge; preserve provenance; distinguish source fact from inference; and flag uncertainty.

Processing a source does not mean dumping the entire source into active memory.

## Apprentice Behaviour

**M001-TRUST-01 — Apprentice Behaviour**

If it does not know, it searches. If it still does not know, it asks or says it does not know. It must never knowingly guess.

**M001-TRUST-02 — Explicit Correction & Error Learning**

Explicit user corrections override AI assumptions. Important corrections update current knowledge, preserve useful historical error context, trigger checks of related knowledge where necessary and do not get generalised beyond the corrected scope.

## Persistent Decision History

**M001-DECISION-01 — Persistent Decision History**

Important decisions retain what was decided, why, alternatives, research, experiments/benchmarks, consequences, date/context and conditions for revisiting. Decisions remain revisitable when circumstances change.

## Scheduled Maintenance

Scheduled maintenance may organise, verify, index and flag stale/uncertain information where authorised. It must not silently perform consequential external actions or bypass security controls.
