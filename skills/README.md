# skills/: the brain's verbs

Each skill is a procedure the brain can run. Every skill follows `_schema.md`. New skills arrive only through `extend-toolkit.md`, start as `draft`, and become `published` when the owner says so.

## Catalogue

`lint-brain` checks that this table matches the folder. Update it in the same change as the skill.

| Skill | What it does | Writes to | Status |
|---|---|---|---|
| `extend-toolkit.md` | Authors the missing skill when the brain hits a gap | `skills/`, `drafts/extend-toolkit/` | published |
| `ingest.md` | Files new material from `raw/` into linked, sourced wiki pages | `wiki/` | published |
| `lint-brain.md` | Finds drift between files: citations, paths, agreement, logs, catalogue | `drafts/lint/` | published |

## Rooms you can add

These are separate repos. Each brings its own skills; add them to this table when you install them. See `docs/plug-in-a-room.md`.

| Room | Adds |
|---|---|
| learning-glossary | A glossary that learns your words from transcripts |
| evidence-ladder | Evidence-counted promotion of patterns |
| the-critic | An adversarial reviewer for drafts |
| brain-map | A link graph and "what does this ripple into?" queries |
