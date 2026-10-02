# Plug in a room

This repo is the house: the filing cabinet, the rules, the logs and the way the brain grows its own tools. The other four repos in The Compounding Brain are rooms. Each one is optional. Each one works on its own, in this house or in any other (Obsidian, a Notion export, an existing repo). Add one when a real problem asks for it, not before.

| Room | Add it when | Repo |
|---|---|---|
| **learning-glossary** | Your transcripts keep mangling the same names and terms, and you correct them by hand every time | [github.com/itstauf/learning-glossary](https://github.com/itstauf/learning-glossary) |
| **evidence-ladder** | Patterns keep showing up across sources and you want them promoted on evidence, not on vibes | [github.com/itstauf/evidence-ladder](https://github.com/itstauf/evidence-ladder) |
| **the-critic** | Drafts are leaving the brain and you want an adversarial review before they reach you | [github.com/itstauf/the-critic](https://github.com/itstauf/the-critic) |
| **brain-map** | You keep asking "what cites this?" or "what breaks if I change this?" | [github.com/itstauf/brain-map](https://github.com/itstauf/brain-map) |

## How to add any room

1. **Copy its skills.** Put its skill files in `skills/` and its wrappers in `.claude/skills/`. Read every file before you copy it.
2. **Add its stores to the writer table** in `CLAUDE.md`. Each new file or folder it writes gets exactly one writer.
3. **Add its skills to the catalogue** in `skills/README.md`, with status.
4. **Add its hard rules**, if it has any, to the hard rules section of `CLAUDE.md`.
5. **Run `lint-brain`.** The catalogue check and the path check will tell you what you missed.
6. **Log the install** as a run in `log/runs.jsonl` (`"skill":"install-room"`), so the brain knows when it changed shape.

## What each room touches here

- **learning-glossary** reads `raw/` transcripts and writes a cleaned copy plus its glossary. It never edits the original raw file; the cleaned copy is a new file.
- **evidence-ladder** reads `wiki/` and writes patterns with a tier (watch, then up) and a count of distinct sources. It pairs with the "about three times, promote it" rule in `CLAUDE.md`, and replaces it with something countable.
- **the-critic** reads anything in `drafts/` and appends a critique. It fills step 2 of "When you finish a draft" in `CLAUDE.md`.
- **brain-map** reads every markdown link and backticked path and builds a graph. It makes check 2 of `lint-brain` cheaper and adds orphan detection.

Same ladder, different job: learning-glossary learns words, evidence-ladder learns patterns. the-critic checks output, brain-map checks structure.
