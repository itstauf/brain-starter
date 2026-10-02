# Folder structure

What a healthy brain looks like after a few weeks of real material:

```
my-second-brain/
├── CLAUDE.md            the constitution (the brain's rulebook)
├── instructions.md      the owner's preferences, from their own feedback
├── raw/                 everything captured, never edited
├── wiki/                the brain: synthesised, interlinked pages
│   ├── index.md         one line per page (the table of contents)
│   ├── log.md           append-only history of every operation, for humans
│   ├── concepts/        (created by the material, not by you)
│   ├── people/
│   ├── projects/
│   └── research/
├── skills/              the brain's verbs, one file per skill
├── log/                 runs.jsonl, decisions.jsonl, feedback.jsonl
├── decisions/
│   ├── proposed/        questions waiting for the owner
│   └── resolved/        rulings, with dissent kept word for word
└── drafts/              work in progress, never authoritative
```

This repo ships the backbone only. The subfolders under `wiki/` are deliberately absent. Let your material create them, not you.

`wiki/log.md` and `log/runs.jsonl` both record operations. The first is a sentence a person reads. The second is a line a machine can count. `ingest` writes both.

Name raw files with a date so they sort themselves:

```
raw/2026-07-19-call-with-a-new-client.md
```
