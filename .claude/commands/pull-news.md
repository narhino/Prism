---
description: Stage 1. Invoke the News Scout to pull 10–15 candidate stories from the last 7 days.
argument-hint: "[optional topic filter]"
---

Invoke the News Scout subagent (`.claude/agents/news-scout.md`) to pull candidate news stories.

Procedure:

1. Read every file in `memory/news-scout/` so the subagent inherits the accumulated learning.
2. Read `brand/content-engine.md` so the subagent knows the 20 buckets.
3. Spawn the News Scout via the Task tool with the topic filter `$ARGUMENTS` (or "full sweep" if no argument was given) and inject the memory files into the prompt. **The Scout must use live web search every time** — never rely on cached recall or training data. The user does not pre-curate headlines; the Scout fetches them fresh on each call.
4. When the subagent returns, write its output to `pipeline/current/01-news.md`.
5. Append the headlines pulled to `memory/news-scout/recent-pulls.md` with today's date — but only after showing the user the proposed addition.
6. Update `memory/orchestrator/pipeline-state.md`: stage = 1 complete, next suggested action = `/ideas`.
7. Hand back to the user with a one-line summary of what was pulled. Do not auto-run `/ideas`.
