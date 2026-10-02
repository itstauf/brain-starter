# First prompt

Two ways in. Pick one. Paste the block into your agent as-is.

## A. You cloned this repo (recommended)

The files are already here, with `<PLACEHOLDERS>` in them. This prompt makes the agent interview you and fill them in.

```
Read CLAUDE.md, instructions.md, skills/README.md and log/README.md.

This is my second brain. Interview me, one question at a time, to fill
in every <PLACEHOLDER> in CLAUDE.md and instructions.md: who I am, what
this brain is for, who else reads it, my voice, phrases I never want to
see, and one or two hard rules of my own. Keep my words; do not polish
them.

Rules while you do it:
- Do not create any folders under wiki/. The material will.
- Do not add skills. extend-toolkit will, when a real gap appears.
- Show me the diff before you write each file.
- When you are done, append one line to log/runs.jsonl with an actor
  field, and explain in five sentences what you set up and why.
```

## B. You are starting from an empty folder

This is the original prompt from the guide, extended to set up the full constitution.

```
Set up an AI second brain in this folder, following Andrej Karpathy's
LLM Wiki pattern.

Create:
- raw/ for source material that is never edited
- wiki/ for the pages you write and maintain, including index.md and log.md
- skills/, log/, decisions/proposed/, decisions/resolved/ and drafts/
- instructions.md for my preferences, edited only from my own feedback
- CLAUDE.md as the governing document

In CLAUDE.md, write your own instructions covering:
- your role as the librarian of this knowledge base
- a load order: what you read, in which order, before any task
- which document wins when two disagree
- three memories: facts (raw/, wiki/, decisions/resolved/) are
  read-only to every task except their one named writer; preferences
  (instructions.md) change only from my feedback; procedures (skills/)
  are authored, not improvised
- the absolute rule that files in raw/ are never modified
- one writer per store, in a table
- the page format: title, one-paragraph summary, key concepts with
  [[wikilinks]], main content, sources referenced
- tagging every claim as either fact or assumption
- that an explicit decision always overrides a standing assumption
- logging every run as one JSON line in log/runs.jsonl, always with an
  actor field
- a finding repeated three runs unchanged becomes a decision memo for me
- if a task cannot be done well with current skills, stop and write the
  missing skill instead of improvising
- skills name the destination, not the path
- updating index.md and appending to log.md after every operation

Do not create topic subfolders yet. We will let those emerge from the
material. Explain what you built when you are done.
```

Then compare what it wrote with the `CLAUDE.md` in this repo and steal any rule yours is missing. It is your constitution. Not its.
