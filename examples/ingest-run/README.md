# An ingest run, before and after

**Before.** The brain holds one file: `before/raw/2026-10-02-call-with-juno-freight.md`. Rough call notes, typed live, never cleaned.

**The prompt.** "Read everything new in raw/ and update the wiki. Follow the rules in CLAUDE.md. Create whatever folders the material actually needs, and tell me why you chose them."

**After.** See `after/`:

- `wiki/projects/juno-freight.md`: one page, every claim tagged fact or assumption, the deadline quoted word for word, and the disagreement between Ade and Bo kept as a contradiction instead of being resolved by guesswork.
- `wiki/index.md` and `wiki/log.md`: updated, as the rules require.
- `log/runs.jsonl`: one line, with an actor.

What to notice:

1. The raw file is untouched. It is still rough. That is the point.
2. Only one folder was created, and the log says why.
3. Bo's "last month" statement is not in `raw/`, so the page says so. The brain does not invent the missing source.
4. Two wikilinks point at pages that do not exist yet. That is deliberate (one mention is not a page) and `lint-brain` will report it honestly until it changes.
