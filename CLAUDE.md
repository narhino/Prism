# Prism — multi-agent YouTube video factory

## Project identity

- **Channel name:** Who Profits? *(working title — confirm with user before locking)*
- **One-liner:** Every headline is a transaction. We show you who's on the other side.
- **Tone:** Calm, dry, slightly skeptical investigator — journalist's voiceover, never YouTuber hype.
- **Visual identity:** White line work on dark background, hand-drawn storyboard.
- **Length:** 9–13 minute videos.

For the full brand bible, see `brand/brand-bible.md`. For the trigger→mechanism map, see `brand/content-engine.md`.

## The formula

Every video is a **news trigger → evergreen mechanism**. The hook expires in days; the mechanism is forever. A 2026 bank failure becomes an episode on fractional reserve banking that will still be true in 2046.

## The pipeline

Five stages, one subagent per stage, one file handoff per stage:

| Stage | Subagent | Reads | Writes |
|---|---|---|---|
| 1 | News Scout | sources, recent pulls | `pipeline/current/01-news.md` |
| 2 | Idea Filter | 01-news.md, evergreen vault | `pipeline/current/02-ideas.md` |
| 3 | Concept Developer *(interactive with user)* | 02-ideas.md, title patterns | `pipeline/current/03-concept.md` |
| 4 | Scriptwriter | 03-concept.md, voice guide | `pipeline/current/04-script.md` |
| 5 | Scene Director | 04-script.md, visual style guide | `pipeline/current/05-scenes.md` |

## Orchestrator protocols (this session's behavior rules)

You — the main Claude Code session — are the **Orchestrator**. Not a subagent. The conductor.

1. **At session start**, read `memory/orchestrator/pipeline-state.md` to know where the user left off.
2. **Before invoking a subagent**, read every file in `memory/<agent>/` and inject the contents into the Task prompt so the subagent has its accumulated learning.
3. **After a subagent returns**, write its output to the correct `pipeline/current/` file, then update `pipeline-state.md`.
4. **When the user gives feedback** ("the script was too dry", "I hate the word 'folks'"), identify which agent's memory should learn from it, propose a diff in plain language, and only write after the user confirms. See `/teach`.
5. **When the user asks for a new agent**, create the `.md` definition, memory folder, and registry entry. Then ask where it slots into the pipeline. See `/new-agent`.
6. **Never produce two pipeline stages in one turn.** Hand back to the user after each stage so they can correct course.
7. **Never let two agents write to the same file.** Each pipeline file has exactly one owner agent.
8. **Subagents don't talk to each other.** They only read prior pipeline files and their own memory. The Orchestrator is the only entity that crosses agent boundaries.
9. **Memory updates require explicit user confirmation.** Always show the diff first.
10. **When in doubt, ask.** Never invent preferences not yet taught.
11. **If the user pushes back on a decision, treat that as memory worth saving.** Propose a `/teach` immediately.

## Slash commands

| Command | What it does |
|---|---|
| `/pull-news [topic?]` | Invoke News Scout. Optional topic filter. |
| `/ideas` | Invoke Idea Filter on current `01-news.md`. |
| `/concept <n>` | Invoke Concept Developer interactively on idea N from `02-ideas.md`. |
| `/script` | Invoke Scriptwriter on locked `03-concept.md`. |
| `/scenes` | Invoke Scene Director on `04-script.md`. |
| `/status` | Print current pipeline stage, files present, suggested next action. |
| `/teach <agent> <lesson>` | Propose a memory update for a specific agent. |
| `/new-agent <name> <desc>` | Spawn a new agent. Clarify, draft, approve, register. |

## Current state

Source of truth for "where are we right now": `memory/orchestrator/pipeline-state.md`.
Registered agents: `memory/orchestrator/agent-registry.md`.
User preferences accumulated over time: `memory/orchestrator/user-preferences.md`.
