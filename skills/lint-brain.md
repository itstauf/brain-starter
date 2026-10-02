---
name: lint-brain
status: published
authored_by: owner
finalised_by: <OWNER_HANDLE>
last_updated: 2026-10-03
---

# lint-brain: find the drift between files that no single write can see

## Purpose

Every write is checked when it happens. Drift between files is not. A page moves and three links keep the old path. A number changes in one page and stays stale in another. A skill is added and the catalogue never hears about it. This skill is the periodic sweep that catches what accumulates across sessions.

It reports. It fixes only mechanical references outside the facts stores. It never edits a fact to make a check pass.

## When invoked

- After any session that wrote to three or more files.
- Before anything leaves the brain for another reader.
- About every ten ingests, or weekly.
- Phrases: "lint the brain", "health check", "check the wiki".

## Procedure

Run every check. For each one, record PASS, FAIL (with the defects) or NOT RUN (with the reason).

1. **Citations.** Every claim tagged fact on a sample of wiki pages points at a file in `raw/` that exists. For a few, open the source and confirm it actually says what the page claims. Existence is cheap; support is what matters. Rotate the sample each run.
2. **Paths.** Every backticked path and every markdown link in `CLAUDE.md`, `skills/`, `docs/`, `wiki/index.md` and the wiki pages resolves to a file that exists. Every [[wikilink]] resolves to a page.
3. **Cross-document agreement.** Facts that appear in more than one page (a date, a count, a name, a status) agree everywhere they are stated as current. Historical mentions (a change history, a log entry, a quote of a past version) are the record. Do not "fix" them.
4. **Logs.** Every line of every `log/*.jsonl` file parses as JSON and carries an `actor` field. Every line of `log/decisions.jsonl` and `log/feedback.jsonl` carries `attributed_to` and a `verbatim` field.
5. **Catalogue currency.** `skills/README.md` lists every file in `skills/` (except `_schema.md` and `README.md`) with its current status, and lists nothing that does not exist. Every wrapper in `.claude/skills/` points at a skill that exists.
6. **Single writer.** Every store in the `CLAUDE.md` writer table has one writer, and no log line shows a different skill writing to it.
7. **Escalation.** Compare this report with the last two lint reports in `drafts/lint/`. Any defect present, unchanged, in all three becomes a memo in `decisions/proposed/` from `decisions/_template.md`.
8. **Fix or file.** Mechanical defects in non-fact files (a broken path in a doc, a missing catalogue row) are fixed in the run. Anything inside `raw/`, `wiki/` or `decisions/resolved/`, and every judgement call, is filed in the report for the owner or for `ingest`.
9. **Log** the run with counts per check.

## Quality gate

Hard fails.

- **Reporting PASS on a check that did not run.** NOT RUN is an honest result. A false PASS is the worst thing this skill can produce.
- Editing a file in `raw/`, `wiki/` or `decisions/resolved/` to make a check pass. The lint fixes references to facts, never facts.
- "Fixing" a historical mention.

## Output

- `drafts/lint/YYYY-MM-DD-lint.md`: one row per check, its result, its defects, and what was fixed or filed.
- Mechanical fixes applied in place, outside the facts stores, each listed in the report.
- Any escalation memo in `decisions/proposed/`.

## Log

```json
{"ts":"2026-10-03T17:00:00Z","actor":"claude-session","skill":"lint-brain","inputs":{"scope":"full"},"outputs":{"checks_run":9,"checks_not_run":0,"defects_found":3,"fixed":2,"filed":1,"escalated":0,"report":"drafts/lint/2026-10-03-lint.md"},"decision":"linted","notes":""}
```

## Failure modes

- **Over-eager fixing.** A stale-looking number inside a change history is correct. Leave it.
- **Existence without support.** A citation that points at a real file which says something else. Only reading the source catches this.
- **Lint theatre.** Running the easy checks and skipping the slow ones. The slow ones are where defects live. If a check was skipped, say NOT RUN.
- **Trusting the top of the file.** A fact stated in the header and again at the foot drifts at the foot. Read to the end.
