---
name: ingest
status: published
authored_by: owner
finalised_by: <OWNER_HANDLE>
last_updated: 2026-10-03
---

# ingest: file new raw material into the wiki

## Purpose

Turn whatever is new in `raw/` into structured, linked, sourced pages in `wiki/`, without touching the raw file. This is the librarian's main job. It is also the only skill that writes to `wiki/`.

## When invoked

- The owner has dropped one or more files into `raw/`.
- Phrases: "ingest", "file this", "read everything new in raw/", "update the wiki".

Do not invoke to rewrite a page for style. Do not invoke on files outside `raw/`; ask the owner to put them there first.

## Procedure

1. **Find what is new.** Compare `raw/` against the sources already listed in `wiki/log.md` and `log/runs.jsonl`. Only new or unlisted files are in scope. Read each one in full.
2. **Decide where each piece of knowledge belongs.** Prefer updating an existing page over creating a new one. Create a folder under `wiki/` only when the material needs one, and say why in the run report.
3. **Write or update pages** in the page format from `CLAUDE.md`. Tag every claim **fact** (a source says so) or **assumption** (inferred, or said once without confirmation). Every page lists its sources as paths into `raw/`.
4. **Check against decisions.** If a claim conflicts with anything in `decisions/resolved/`, the decision wins. Note the conflict on the page.
5. **Flag contradictions** between sources on the page itself, both versions quoted, neither silently dropped.
6. **Link.** Add [[wikilinks]] between related pages, in both directions.
7. **Promotion check.** If an assumption has now appeared about three times from different sources, propose promoting it to fact in the run report. List the sources. Do not promote it silently.
8. **Update** `wiki/index.md` (one line per page) and append one entry to `wiki/log.md`.
9. **Log** the run to `log/runs.jsonl`.

## Quality gate

Hard fails. Stop, write nothing to `wiki/`, log the failure.

- Any file in `raw/` was changed, renamed or deleted.
- A claim on a page has no source, or a quote does not match its raw file word for word.
- A name, number or quote appears that is not in the raw source.
- `wiki/index.md` or `wiki/log.md` was not updated.
- A contradiction was resolved by deleting one side.

## Output

- New or updated pages under `wiki/`.
- `wiki/index.md` and `wiki/log.md` updated.
- A short run report to the owner: files read, pages created, pages updated, folders created and why, contradictions found, promotions proposed.

## Log

```json
{"ts":"2026-10-03T09:00:00Z","actor":"claude-session","skill":"ingest","inputs":{"files":["raw/2026-10-03-call-with-juno-freight.md"]},"outputs":{"pages_created":["wiki/projects/juno-freight.md"],"pages_updated":["wiki/index.md"],"contradictions":0,"promotions_proposed":0},"decision":"filed","notes":""}
```

## Failure modes

- **Folder sprawl.** A new folder for every file. Two pages is not a theme. Wait for the third.
- **Summary drift.** The page says what the source probably meant. Quote when the exact words matter.
- **Assumption laundering.** An assumption copied from one page to another loses its tag and becomes a fact by repetition. Tags travel with the claim.
- **The silent skip.** A long raw file is half read. If a file was not fully read, say so in the report and the log.
