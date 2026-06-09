---
name: rockaway-qbrain-memory-lookup
description: Fast read-only Rockaway Q / QAQ memory lookup through the QBrain MCP. Use for customer, person, project, workflow, meeting, blocker, initiative, or CSV-row lookup when the user wants quick context from the Q / QAQ brain.
---

# Rockaway QBrain Memory Lookup

Use only the Rockaway Q / QAQ brain MCP:

```text
rockaway-q
http://100.102.180.108:8788/rockaway-q/mcp
```

Never query Rockaway Ventures unless the user explicitly asks for cross-brain context. Never print or store bearer tokens.

## First Call

Call `memory_lookup` first for normal retrieval. It is the front door for this brain.
On the Mac mini, `memory_lookup` uses the endpoint-scoped sanitized QMD index first, then falls back to GBrain if QMD is unavailable or weak. The user does not need QMD installed locally.

Use:

```text
memory_lookup({ query: "...", limit: 8, detail: "medium" })
```

Use `detail: "low"` for quick exact/CSV passes and `detail: "high"` only when the user asks for deeper retrieval.

## Follow-Up Calls

- Use `get_page` only for the strongest high/medium confidence slug hits.
- Use `get_links` and `get_backlinks` only when relationship, ownership, or graph context matters.
- Use lower-level `search`, `query`, and `qmd_*` tools only when `memory_lookup` is not enough.
- Do not use any mutation/write tools.

## CSV Recipe

For each row:

1. Extract customer/company, person, topic, date, project, workflow, or blocker fields.
2. Build one concise query like `customer=Acme person=Jane Example topic=onboarding workflow date=2026-06-09`.
3. Call `memory_lookup`.
4. If confidence is medium/high, call `get_page` for the top 1-3 slug hits.
5. Return columns: `row_id`, `query`, `matched_pages`, `confidence`, `summary`, `recommended_next_step`, `source_slugs`.

Keep output compact and private by default.
