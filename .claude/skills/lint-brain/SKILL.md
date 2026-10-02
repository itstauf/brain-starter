---
name: lint-brain
description: Health check for the brain. Finds drift between files that no single write can see: citations that do not support their claims, broken paths and wikilinks, facts that disagree across pages, log lines without an actor, and a skills catalogue that no longer matches the folder. Triggers on "lint the brain", "health check", "check the wiki", "find broken links", "audit the brain".
---

# lint-brain (wrapper)

This is a thin wrapper. The procedure lives in the brain itself so every agent reads the same file.

1. Read `CLAUDE.md` if you have not this session.
2. Follow `skills/lint-brain.md` exactly. Record every check as PASS, FAIL or NOT RUN. Reporting PASS on a check that did not run is a hard fail.
3. Write the report to `drafts/lint/` and append the run to `log/runs.jsonl` with an `actor` field.

If this wrapper and `skills/lint-brain.md` ever disagree, the skill file wins.
