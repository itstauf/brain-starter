# log/: the legibility trail

If a run was not logged, it did not happen as far as the brain is concerned. Three append-only files, one JSON object per line. Never edit or delete a line; correct a mistake by appending a new line that says so.

| File | What one line records | Who appends |
|---|---|---|
| `runs.jsonl` | One run of one skill | Every skill, every run |
| `decisions.jsonl` | One ruling by the owner | The owner (or an agent transcribing the owner's ruling, word for word) |
| `feedback.jsonl` | One piece of the owner's feedback, and what it changed | Whoever records it, word for word |

The three files ship empty. The lines below are synthetic examples; do not paste them into your logs.

## runs.jsonl

| Field | Required | Meaning |
|---|---|---|
| `ts` | yes | UTC timestamp, ISO 8601 |
| `actor` | **yes** | Who ran it: the owner's handle, `claude-session`, or another agent's name. A line without it is a hard-rule violation. |
| `skill` | yes | Skill name, matching a file in `skills/` |
| `inputs` | yes | What it was given (paths, not contents) |
| `outputs` | yes | What it wrote (paths and counts) |
| `decision` | yes | One word: `filed`, `drafted`, `linted`, `refused`, `failed`... |
| `notes` | no | Anything a future reader needs. Gaps, skips, NOT RUN reasons. |

Two synthetic examples:

```json
{"ts":"2026-10-03T09:12:00Z","actor":"mira","skill":"ingest","inputs":{"files":["raw/2026-10-02-call-with-juno-freight.md"]},"outputs":{"pages_created":["wiki/projects/juno-freight.md"],"pages_updated":["wiki/index.md","wiki/log.md"],"contradictions":0,"promotions_proposed":0},"decision":"filed","notes":""}
{"ts":"2026-10-03T17:40:00Z","actor":"claude-session","skill":"lint-brain","inputs":{"scope":"full"},"outputs":{"checks_run":8,"checks_not_run":1,"defects_found":2,"fixed":1,"filed":1,"report":"drafts/lint/2026-10-03-lint.md"},"decision":"linted","notes":"check 1 NOT RUN: wiki has fewer than three pages with sources"}
```

## decisions.jsonl

One line per ruling. Written when a memo moves from `decisions/proposed/` to `decisions/resolved/`.

| Field | Required | Meaning |
|---|---|---|
| `ts`, `actor` | yes | As above. `actor` is whoever wrote the line. |
| `decision_id` | yes | The memo number, e.g. `DM-03` |
| `ruling` | yes | The option chosen, in a few words |
| `attributed_to` | yes | Who actually made the ruling. Differs from `actor` when someone transcribes it. |
| `verbatim` | yes | The ruling in the decider's own words |
| `memo` | yes | Path to the resolved memo |
| `dissent_recorded` | yes | `true` or `false` |

```json
{"ts":"2026-10-04T08:30:00Z","actor":"claude-session","decision_id":"DM-01","ruling":"option B, weekly digest","attributed_to":"mira","verbatim":"Go with the weekly digest. If nobody reads it by November we kill it.","memo":"decisions/resolved/2026-10-04-DM-01-how-should-the-team-hear-about-new-pages.md","dissent_recorded":true}
```

## feedback.jsonl

One line per piece of the owner's feedback. Every edit to `instructions.md` points back to one of these.

| Field | Required | Meaning |
|---|---|---|
| `ts`, `actor` | yes | As above |
| `attributed_to` | yes | Who said it |
| `verbatim` | yes | Their exact words. Not a summary. |
| `about` | yes | The file or draft it was about |
| `changed` | yes | What changed because of it (`instructions.md: added ban`, or `nothing yet`) |

```json
{"ts":"2026-10-03T11:05:00Z","actor":"claude-session","attributed_to":"mira","verbatim":"Stop putting client calls under research. They are projects.","about":"wiki/research/juno-freight.md","changed":"instructions.md: routing rule added; page moved to wiki/projects/"}
```
