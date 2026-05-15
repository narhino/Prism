---
description: Stage 4. Invoke the Scriptwriter on the locked concept.
---

Invoke the Scriptwriter subagent (`.claude/agents/scriptwriter.md`).

Procedure:

1. Check that `pipeline/current/03-concept.md` exists and is locked. If not, prompt to run `/concept <n>` first.
2. Read every file in `memory/scriptwriter/` and `brand/brand-bible.md`.
3. Spawn the Scriptwriter via the Task tool with `03-concept.md` and the memory files injected. Instruct it to follow the 5-beat template and respect voice constraints.
4. When the subagent returns, write its output to `pipeline/current/04-script.md`.
5. Update `memory/orchestrator/pipeline-state.md`: stage = 4 complete, next suggested action = `/scenes`.
6. Hand back to the user with the runtime estimate and offer to read it back beat-by-beat. Do not auto-run `/scenes`.
