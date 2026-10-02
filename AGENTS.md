# AGENTS.md

For Cursor, Codex, and any agent that reads this file. Claude Code reads `CLAUDE.md` directly; this file points every other agent at the same rules so there is one constitution, not two.

## Read first, in this order

1. `CLAUDE.md`: the constitution. Load order, which document wins, the three memories, the write rule, one writer per store, hard rules, logging, the fixed point.
2. `instructions.md`: the owner's preferences and banned phrases.
3. `wiki/index.md`: what the brain already knows.
4. The skill file for the task in `skills/`. The schema is `skills/_schema.md`; the catalogue is `skills/README.md`.

## Skills

| Task | Skill |
|---|---|
| File new material from `raw/` into the wiki | `skills/ingest.md` |
| Health check across files | `skills/lint-brain.md` |
| The task has no skill | `skills/extend-toolkit.md` |
| Something needs deciding | `decisions/_template.md` |

## Rules that bind every agent

- Never edit, rename or delete anything in `raw/`.
- Write only where `CLAUDE.md` says your skill may write.
- Append one line to `log/runs.jsonl` per run, with `"actor"` set to your agent's name.
- Never invent a quote, number, name or result.
- Never mark a check PASS if it did not run.
- If a task cannot be done well with current skills, stop and run `skills/extend-toolkit.md`.
- Work on a branch and open a pull request. Never merge your own.

If this file and `CLAUDE.md` disagree, `CLAUDE.md` wins.
