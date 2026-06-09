---
name: rockaway-qbrain
description: Use the Rockaway Q / QAQ brain to answer questions, look up customers, people, projects, workflows, meetings, blockers, initiatives, or enrich CSV rows. Trigger when the user says Rockaway brain, QBrain, Q brain, QAQ brain, look this up in the brain, search what we know, or asks for Q / QAQ brain context.
---

# Rockaway QBrain

Use this when the user wants to ask the Rockaway Q / QAQ brain a question.

## Keep It Simple For The User

Do not make the user say tool names. Do not explain MCP, QMD, tokens, headers, or setup unless they ask.

Good user prompts include:

- "Use the Rockaway brain to answer this..."
- "Use the Rockaway brain to look up this project."
- "Use the Rockaway brain to enrich this CSV."
- "What do we know about this customer?"

## Hidden Agent Instructions

Use the `rockaway-q-qmd` MCP first for broad semantic recall. Use only collection `rockaway-q`.

Then use the `rockaway-q` MCP for canonical page expansion, links, backlinks, stats, and GBrain fallback lookup. Stay inside the Rockaway Q / QAQ brain unless the user explicitly asks for cross-brain context.

Default retrieval order:

1. Call `rockaway-q-qmd.status` if connection/index state is uncertain.
2. Call `rockaway-q-qmd.query` with `collections: ["rockaway-q"]`; use both exact keywords and natural-language intent when useful.
3. Call `rockaway-q-qmd.get` for the best source before answering factual questions.
4. Call `rockaway-q.get_page` for the strongest matching canonical slugs when full detail is useful.
5. Use `rockaway-q.get_links` and `rockaway-q.get_backlinks` only when ownership, relationship, or graph context matters.
6. Use `rockaway-q.memory_lookup` only as a GBrain fallback if native QMD is unavailable or weak.

Never write to the brain. Never print or store bearer tokens.

## Answer Style

Give a plain-language answer. Mention confidence when useful. Keep sources short: page titles or slugs are enough unless the user asks for a fuller source trail.

For CSVs, return simple columns:

```text
row, match, confidence, summary, next step, sources
```

If the request is vague, search first. Ask a follow-up only if the results are too broad or ambiguous.
