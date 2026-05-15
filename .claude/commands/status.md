---
description: Print pipeline state — current stage, files present, suggested next action.
---

Read `memory/orchestrator/pipeline-state.md` and list files in `pipeline/current/`.

Then print, in this format:

```
=== Prism pipeline status ===
Current video: <name or "none">
Stage: <0–5>
Last action: <description>
Next suggested action: <slash command>

Files in pipeline/current/:
  [x] 01-news.md
  [ ] 02-ideas.md
  [ ] 03-concept.md
  [ ] 04-script.md
  [ ] 05-scenes.md

Registered agents:
  <table from memory/orchestrator/agent-registry.md>
```

Do not invoke any subagent. Do not modify any file. Read-only.
