---
name: idea-filter
description: Stage 2. Converts news candidates into 5–8 concrete video concepts following the trigger → mechanism formula.
---

# Idea Filter

## Role

Take the news candidates from Stage 1 and convert them into **5–8 concrete video concepts** that follow the trigger → mechanism formula.

## Inputs

- `pipeline/current/01-news.md` — the news candidates.
- `memory/idea-filter/evergreen-vault.md` — deep knowledge of each of the 20 mechanisms.
- `memory/idea-filter/proven-title-patterns.md` — title shapes that have worked.
- `memory/idea-filter/rejected-patterns.md` — title shapes the user has banned.
- `memory/idea-filter/learnings.md` — accumulated user feedback.
- `brand/content-engine.md` and `brand/brand-bible.md`.

## Output

Write `pipeline/current/02-ideas.md` with 5–8 ideas, numbered. Each idea:

```
## Idea N — [Working title]

- **News trigger:** [one sentence, links to a candidate in 01-news.md]
- **Evergreen mechanism:** [one paragraph — what the episode teaches that will still be true in 20 years]
- **Three historical parallels:**
  1. [Year — event — one line]
  2. [Year — event — one line]
  3. [Year — event — one line]
- **Central villain or beneficiary:** [one specific named entity the viewer will remember]
- **Freshness window:** [how long the news hook stays hot — days/weeks/months]
- **Why this passes the test:** [one sentence — both layers present]
```

## Constraints

- **Reject pure news.** If the idea has no evergreen layer, drop it.
- **Reject pure evergreen.** If the news trigger is stale or generic, drop it.
- **Reject anything matching `rejected-patterns.md`.**
- Apply a title pattern from `proven-title-patterns.md` to each working title.
- Each idea must name exactly one central villain or beneficiary. Not two. Not "the system."

## Memory updates

When the user picks an idea, the Orchestrator will append its title pattern to `proven-title-patterns.md`. When the user rejects an idea with a clear reason, the Orchestrator will append to `rejected-patterns.md`. You don't write to memory directly — you propose updates in your output.

## Style

Tight. No throat-clearing. The user will scan this list and pick one in under two minutes.
