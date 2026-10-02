---
name: extend-toolkit
status: published
authored_by: owner
finalised_by: <OWNER_HANDLE>
last_updated: 2026-10-03
---

# extend-toolkit: author the missing skill when the brain hits a gap

## Purpose

This is the fixed point. When the brain meets a task it cannot do well with the skills it has, this skill writes the missing one, so the next session inherits the capability instead of improvising it again.

Without it, the brain is a capable assistant that forgets how it did things. With it, the brain grows its own tools in response to real demand.

## When invoked

- A task arrives and no skill in `skills/README.md` covers it.
- The same kind of request has been improvised twice.
- The owner says "make this a skill", "teach it to do this", "add a skill for".

Do **not** invoke for a one-off task, or to cover a single odd case of an existing skill (see the anti-patterns).

## Procedure

1. **Diagnose the gap.** Write one sentence: what the brain could not do, and what happened instead. If you cannot write the sentence, there is no gap yet.
2. **Check for duplicates.** Read `skills/README.md` and every skill whose name is close. Could an existing skill be tuned with one new step or option? If yes, propose that edit and stop here.
3. **Name it.** Verb-noun, lowercase, dashed.
4. **Draft it from the schema** in `skills/_schema.md`. Set `status: draft` and `authored_by: agent`. Write the quality gate first: what would make this skill's output wrong?
5. **Test it once** on a real input from `raw/` or the task in hand. Write the output to `drafts/`, not to its real destination. Fix the skill file, not the output, until the test passes its own gate.
6. **Log it** to `log/runs.jsonl` with the gap sentence in `notes`.
7. **Add it to the catalogue** in `skills/README.md` with status `draft`. If you work in Claude Code, add a thin wrapper at `.claude/skills/<name>/SKILL.md` pointing to the file. Tell the owner it is waiting for them to finalise.

## Quality gate

Hard fails. The skill is not added.

- No gap sentence, or a gap an existing skill already covers.
- The draft is missing any of the seven schema sections.
- The output destination includes `raw/` or `decisions/resolved/`.
- The draft skips a review step that the rest of the brain requires.
- The test run did not happen, or its result is reported without being run.
- The skill is marked `published` by anyone but the owner.

## Output

- `skills/<name>.md` with `status: draft`.
- One row in `skills/README.md`.
- Optionally `.claude/skills/<name>/SKILL.md`, a wrapper only.
- The test output in `drafts/extend-toolkit/YYYY-MM-DD-<name>-test.md`.

## Log

```json
{"ts":"2026-10-03T10:00:00Z","actor":"claude-session","skill":"extend-toolkit","inputs":{"gap":"no way to turn a week of raw notes into a one-page summary"},"outputs":{"skill":"skills/draft-weekly-note.md","status":"draft","test":"drafts/extend-toolkit/2026-10-03-draft-weekly-note-test.md"},"decision":"drafted","notes":"awaiting owner finalisation"}
```

## Failure modes

Three anti-patterns. Each one has killed a skill folder before.

- **Skill explosion.** Five skills when one will do. Every skill is something to maintain and something the agent must choose between. Fewer, broader skills with options beat a drawer full of near-duplicates.
- **A skill per edge case.** One awkward input arrives and a new skill appears for it. Tune the parent skill instead: add a step, an option or a failure mode.
- **A skill that bypasses review.** A new skill that writes straight to its final destination, skips the hard rules or skips the critic is a hole in the wall. New skills inherit every gate the brain already has.

If this skill is healthy, the system grows with use.
