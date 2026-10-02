# DM-01: How should the team hear about new wiki pages?

> Synthetic example. Halden & Co, Mira Okafor and her team are invented.
> This is what a memo looks like after the owner has ruled and it has moved to `decisions/resolved/2026-10-04-DM-01-how-should-the-team-hear-about-new-pages.md`.

**Status:** resolved · **Raised:** 2026-10-01 · **Source:** drafts/lint/2026-10-01-lint.md
**Decides:** Mira Okafor · **Stance blocks required:** Tomas Reyes-Lind, Priya Vale
**Gated by:** nothing (flagged in the run report as low priority)

## Context

- The lint report has listed "pages created with no reader" three runs in a row, unchanged. Under the escalation rule that makes it a decision. (drafts/lint/2026-09-17-lint.md, drafts/lint/2026-09-24-lint.md, drafts/lint/2026-10-01-lint.md)
- Eleven pages were created in September. None was opened by anyone but Mira, per her own note. (raw/2026-10-01-mira-note-on-wiki-use.md)

## Options

| Option | What it costs | What it buys |
|---|---|---|
| A. A message to the team chat for every new page | Noise. Eleven messages a month at current pace, more later. | Nobody misses a page. |
| B. A weekly digest, drafted by the agent into `drafts/digest/` and sent by Mira | Ten minutes of Mira's week. A page can sit unseen for up to seven days. | One message people might actually read. Mira stays the sender. |
| C. Do nothing | Pages keep going unread. | No new work. |

## Recommendation

B. It keeps sending in the owner's hands (the brain drafts, it never sends) and it is cheap to stop.

## Stances

### Tomas Reyes-Lind
> "Honestly I'd rather get them one at a time. A digest is just another email I won't open."
> attributed_to: Tomas Reyes-Lind · date: 2026-10-02 · source: raw/2026-10-02-team-standup-notes.md

### Priya Vale
> "Does the digest include pages that changed, or only new ones?"
> attributed_to: Priya Vale · date: 2026-10-02 · source: raw/2026-10-02-team-standup-notes.md
> Labelled: open question, not a position.

### Mira Okafor (decides)
Ruled B. See Ruling.

## Dissent

Tomas Reyes-Lind, verbatim: "Honestly I'd rather get them one at a time. A digest is just another email I won't open."

## Reversibility

Easy. Stopping the digest means not sending it. Switching to option A later means one new skill. Nobody outside the team would notice either change.

## Falsification

Proposed by this memo, not an existing standard: if by 2026-11-30 the digest has been sent four times and fewer than two of the team have opened a linked page, B was the wrong call. Check the team chat history on that date.

## On resolution

- `extend-toolkit` drafts a `draft-weekly-digest` skill (status: draft).
- `instructions.md` gains a routing line: digests go to `drafts/digest/`.
- One line appended to `log/decisions.jsonl`.
- Priya's open question goes into the new skill's Procedure as an explicit choice: new pages only, for now.

## Ruling

> "Go with the weekly digest. If nobody reads it by November we kill it."
> attributed_to: Mira Okafor · date: 2026-10-04 · source: log/decisions.jsonl
