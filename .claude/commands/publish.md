---
description: Stage 6. Invoke the Publishing Optimizer to author title, description, hashtags, and (if a thumbnail file is supplied) a thumbnail review.
argument-hint: "[optional path to thumbnail image]"
---

Invoke the Publishing Optimizer subagent (`.claude/agents/publishing-optimizer.md`).

Procedure:

1. Check that `pipeline/current/03-concept.md` and `pipeline/current/04-script.md` exist. If not, prompt the user to run prior stages.
2. Read every file in `memory/publishing-optimizer/` so the subagent inherits the accumulated learning.
3. Read `brand/brand-bible.md`.
4. Spawn the Publishing Optimizer via the Task tool. Pass `$ARGUMENTS` (the optional thumbnail file path) and inject all memory files into the prompt. Tell the subagent to use WebSearch to verify current best practices before authoring.
5. When the subagent returns, write its output to `pipeline/current/06-publishing.md`.
6. Update `memory/orchestrator/pipeline-state.md`: stage = 6 complete, next suggested action = post the video (or rerun `/publish <thumbnail-path>` if no thumbnail was reviewed yet).
7. Hand back to the user with the title verdict, a short description preview, and any thumbnail-review notes. Surface the file via `SendUserFile`.
