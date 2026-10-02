---
name: extend-toolkit
description: Author a missing skill when the brain hits a task its current skills cannot do well. Diagnoses the gap, checks for duplicates, drafts from the skill schema, tests once, logs, and adds it to the catalogue as a draft. Triggers on "make this a skill", "add a skill for", "teach it to do this", "we keep doing this by hand", "extend the toolkit", or any capability gap.
---

# extend-toolkit (wrapper)

This is a thin wrapper. The procedure lives in the brain itself so every agent reads the same file.

1. Read `CLAUDE.md` and `instructions.md` if you have not this session.
2. Read `skills/_schema.md`.
3. Follow `skills/extend-toolkit.md` exactly, all seven steps and its quality gate.
4. Append the run to `log/runs.jsonl` with an `actor` field.

If this wrapper and `skills/extend-toolkit.md` ever disagree, the skill file wins.
