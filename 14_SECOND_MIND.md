# AI Masterpiece — Second Mind

## Purpose

The Second Mind is the project's durable, human-readable knowledge system. It is not a dump of chat history and it is not limited to personal memory.

## Layered Model

```text
SECOND MIND
├── RAW ARCHIVE
│   └── Complete historical record
├── ACTIVE KNOWLEDGE
│   ├── Personal memory
│   ├── General knowledge
│   ├── Project knowledge
│   ├── Research conclusions
│   └── Current state
├── ENTITIES / CONCEPTS
├── RELATIONSHIPS
└── RETRIEVAL
    └── Relevant context only
```

Archive != active memory != context.

## Knowledge States

- Confirmed
- Research finding
- Provisional
- Open
- Rejected
- Conflict
- Historical
- Forgotten

## Personal Memory

The system should eventually maintain a comprehensive representation of authorised personal information, while retrieving it selectively.

Learn from authorised conversations, documents, projects, calendar/tasks and eventually other authorised sources. Uncertain personal facts go to review rather than silently becoming facts.

## Authority and Transparency

The user remains the ultimate authority over persistent memory.

The user must be able to inspect, edit, correct, delete, reorganise and approve/reject uncertain information.

Memory records should expose, where applicable:

- Content
- Confidence
- Importance
- Current status
- Source/provenance
- Created date
- Last verified
- Change history
- Related memories
- Why it is stored

## Confidence and Provenance

User-confirmed information is trusted. Research-supported information receives confidence appropriate to its evidence. AI inference is labelled. Uncertain information is routed to review. Forgotten information is excluded from normal retrieval.

Important knowledge preserves source, evidence/context, date, confidence and relevant relationships.

## Time and Freshness

Track freshness selectively for information likely to change. Stale does not mean false. Historical information remains available.

When knowledge changes, retain the previous value and record the new value, date, reason and evidence.

## Forgetting

Forgetting removes information from normal active retrieval and records the historical state where appropriate. Hard deletion is a separate explicit operation for privacy/legal requirements.

## Organisation and Retrieval

Low-risk organisation may be autonomous:

- merge obvious duplicates
- add/update links
- reorganise structure
- improve metadata
- rename notes without changing meaning
- update indexes/navigation

Semantic meaning is protected. Changes to factual claims, confidence, interpretation, important relationships or conclusions go through review.

Retrieval considers relevance, trust, recency, importance and current context.

## Relationships

The Second Mind should use linked documents/entities to represent useful relationships without requiring the whole topic to be placed into model context. A graph database is not yet required; linked human-readable documents are the design direction.

## Raw Archive + Active Knowledge

The historical archive should retain conversations, research, sources, decisions, memory changes, audit history and historical project states as authorised. Active knowledge may evolve without destroying the underlying history.

## Inbox / Review

Use an Inbox for uncertain facts, conflicting evidence, important inferred relationships, uncertain conclusions and semantic changes.

Possible review actions: approve, reject, edit/correct, research further.

## Research Knowledge

Research records should preserve source, date researched, last verified, freshness/volatility, confidence, importance and reverification policy.

Credible sources are evaluated by the actual evidence: authority, evidence quality, first-hand experience, relevance, recency, independence, conflicts, transparency and corroboration.

Conflicting credible sources are preserved and explained rather than arbitrarily collapsed.

When new evidence changes a conclusion, preserve the old conclusion as historical and make the new conclusion current with the change, date, reason and evidence recorded.

## Authorised Learning

The AI may process authorised books, PDFs, videos, papers, GitHub repositories, courses, notes and documents. It should extract useful concepts/entities/relationships, connect them to existing knowledge, preserve provenance and distinguish source fact from inference.

Do not dump whole documents into active memory merely because they were processed.

## Apprentice Behaviour

If the AI does not know, it searches. If research cannot resolve the question, it asks or says it does not know. It must never knowingly guess.

Explicit user corrections outrank AI assumptions. Important corrections should update current knowledge, preserve useful history and trigger checks of related knowledge where necessary.

## Design Rule

**Remember broadly. Retrieve selectively. Preserve history. Protect meaning.**
