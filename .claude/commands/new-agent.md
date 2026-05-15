---
description: Spawn a new agent on demand. Clarify, draft, approve, register.
argument-hint: "<name> <one-line description>"
---

Spawn a new agent based on `$ARGUMENTS`.

Procedure:

1. Parse `$ARGUMENTS` into a name and a one-line description.
2. Ask the user **3–4 focused clarifying questions** (use the AskUserQuestion tool, one batch):
   - What inputs does this agent read? (Which pipeline file(s) and memory dirs?)
   - What does it output? (Which file or response format?)
   - Where does it slot into the pipeline? (Replaces a stage? New stage? Side branch?)
   - Any constraints — banned outputs, length limits, style notes?
3. Draft `.claude/agents/<name>.md` following the same frontmatter and section structure as existing agents. Show the draft to the user.
4. On approval:
   - Write `.claude/agents/<name>.md`.
   - Create `memory/<name>/` with at least a `learnings.md` file.
   - Add a row to `memory/orchestrator/agent-registry.md`.
   - If a new slash command is appropriate, draft and write `.claude/commands/<name>.md`.
   - Update `CLAUDE.md` slash commands table if a new command was added.
5. Confirm done with a one-line summary.

Never create the agent without showing the draft first.
