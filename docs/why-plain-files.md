# Why plain files

I tried databases, note apps and vector stores first. I came back to a folder of markdown files in git. Here is why, and where it falls short.

## What plain files give you

- **Versioning.** Every change has a date, an author and a message. You can see what the brain believed last Tuesday, and roll back to it.
- **Diffs.** When the agent edits a page, you see the exact lines it changed. You review the change, not the whole page. This is the single biggest reason: it makes an agent's work checkable by a tired human in a minute.
- **Provenance.** Every wiki claim points at a path in `raw/`. A path is something you can open. Combined with git history, you can trace any sentence back to the file it came from and the run that wrote it.
- **No lock-in.** Markdown opens in every editor, every agent, Obsidian, GitHub, a phone. If a better tool arrives next year, you point it at the folder. Nothing to export.
- **Any agent can read it.** Claude Code, Cursor, Codex, a Claude or ChatGPT project, a person with a text editor. The constitution is a file, not a vendor setting.

## Honest limits

- **No retrieval index.** The agent finds things by reading `wiki/index.md` and searching files. That works well into the hundreds of pages. At many thousands it gets slow and starts missing things. If you get there, add a search index on top. Keep the files as the source of truth.
- **Coarse permissions.** Git permissions work per repository and, with CODEOWNERS and branch rules, per path for review. They do not hide one paragraph from one person. If two groups must never see each other's material, use two repos. See `running-with-a-team.md`.
- **No live operational state.** Files are good at "what we know". They are bad at "what is happening this second": a queue, a live dashboard, a counter many people update at once. Keep those in the tool built for them and bring summaries into `raw/`.
- **Merge conflicts.** Two agents writing the same page at once will conflict. The single-writer rule in `CLAUDE.md` exists mostly to stop this.
- **Discipline is on you.** Nothing stops a person from editing `raw/` by hand. The rules are rules, not locks. `lint-brain` catches some drift after the fact; branch protection catches more.
