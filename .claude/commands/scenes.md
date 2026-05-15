---
description: Stage 5. Invoke the Scene Director to break the script into 30–50 visual scenes.
---

Invoke the Scene Director subagent (`.claude/agents/scene-director.md`).

Procedure:

1. Check that `pipeline/current/04-script.md` exists. If not, prompt to run `/script` first.
2. Read every file in `memory/scene-director/`.
3. Spawn the Scene Director via the Task tool with `04-script.md` and the memory files injected. Instruct it to describe only WHAT is on screen, never HOW to animate.
4. When the subagent returns, write its output to `pipeline/current/05-scenes.md`.
5. Update `memory/orchestrator/pipeline-state.md`: stage = 5 complete, next suggested action = archive episode and start a new pipeline.
6. Hand back to the user with the scene count and offer to spot-check any scene.
