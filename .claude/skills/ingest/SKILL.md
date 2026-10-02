---
name: ingest
description: File new material from raw/ into structured, linked, sourced wiki pages without ever editing the raw file. Updates wiki/index.md and wiki/log.md and logs the run. Triggers on "ingest", "file this", "read everything new in raw/", "update the wiki", "I've added new files", "process raw".
---

# ingest (wrapper)

This is a thin wrapper. The procedure lives in the brain itself so every agent reads the same file.

1. Read `CLAUDE.md` and `instructions.md` if you have not this session.
2. Follow `skills/ingest.md` exactly, including its quality gate.
3. Append the run to `log/runs.jsonl` with an `actor` field.

If this wrapper and `skills/ingest.md` ever disagree, the skill file wins.
