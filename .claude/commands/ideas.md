---
description: Stage 2. Invoke the Idea Filter to convert news candidates into 5–8 video concepts.
---

Invoke the Idea Filter subagent (`.claude/agents/idea-filter.md`).

Procedure:

1. Check that `pipeline/current/01-news.md` exists. If it doesn't, ask the user whether to run `/pull-news` first. Do not auto-run it.
2. Read every file in `memory/idea-filter/` so the subagent inherits the accumulated learning.
3. Read `brand/content-engine.md` and `brand/brand-bible.md`.
4. Spawn the Idea Filter via the Task tool with `01-news.md` and the memory files injected.
5. When the subagent returns, write its output to `pipeline/current/02-ideas.md`.
6. Update `memory/orchestrator/pipeline-state.md`: stage = 2 complete, next suggested action = `/concept <n>`.
7. Hand back to the user with a numbered list of the idea titles and ask which one to develop. Do not auto-run `/concept`.
