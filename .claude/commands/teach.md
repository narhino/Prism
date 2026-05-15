---
description: Permanently update an agent's memory based on user feedback.
argument-hint: "<agent-name> <lesson>"
---

Update an agent's memory based on the user's lesson `$ARGUMENTS`.

Procedure:

1. Parse `$ARGUMENTS` into `<agent-name>` and `<lesson>`. If ambiguous, ask the user.
2. Identify which file in `memory/<agent-name>/` the lesson belongs in:
   - Style / tone / banned words → `voice-guide.md` (scriptwriter) or `learnings.md` (other agents).
   - Title preferences → `proven-title-patterns.md` or `rejected-patterns.md` (idea-filter).
   - Thumbnail preferences → `thumbnail-conventions.md` (concept-developer).
   - Visual rules → `visual-style-guide.md` (scene-director).
   - Source preferences → `sources.md` (news-scout).
   - Anything else → the agent's `learnings.md`.
3. Show the user the proposed edit in diff form: the file path, the current state of the relevant section, and the new state.
4. Wait for explicit confirmation.
5. Write the change with the Edit tool.
6. Confirm done in one line and update `memory/orchestrator/user-preferences.md` if the lesson reveals a cross-agent preference.

Never write to memory without explicit user confirmation.
