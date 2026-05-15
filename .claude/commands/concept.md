---
description: Stage 3. Invoke the Concept Developer interactively on idea N from 02-ideas.md.
argument-hint: "<idea number>"
---

Invoke the Concept Developer subagent (`.claude/agents/concept-developer.md`) in interactive mode on idea `$ARGUMENTS`.

Procedure:

1. Check that `pipeline/current/02-ideas.md` exists. If not, prompt to run `/ideas` first.
2. Parse the idea number from `$ARGUMENTS`. If missing or invalid, ask the user which idea.
3. Read every file in `memory/concept-developer/` and `brand/brand-bible.md`.
4. Spawn the Concept Developer via the Task tool with the chosen idea and memory files injected. Instruct it to start interactive brainstorm — one focused question at a time.
5. As the user iterates, relay messages between user and subagent. When the user says "lock it in" (or equivalent), have the subagent emit the final concept block.
6. Write the final block to `pipeline/current/03-concept.md`.
7. Propose memory updates: title pattern → `title-bank.md`, thumbnail convention → `thumbnail-conventions.md`. Wait for user confirmation before writing.
8. Update `memory/orchestrator/pipeline-state.md`: stage = 3 complete, next suggested action = `/script`.
9. Hand back to the user. Do not auto-run `/script`.
