# The skill schema

Every skill in `skills/` is a markdown file with these seven sections, in this order. A skill is a procedure the brain can run on request. It is written for an agent, but a person should be able to follow it by hand.

Skills name the destination, not the path. Be vague about how. Be exact about what goes in, what comes out, and what fails.

```markdown
---
name: <verb-noun, lowercase, dashed>
status: draft | published | deprecated
authored_by: owner | agent
finalised_by: <owner handle, or null while a draft>
last_updated: YYYY-MM-DD
---

# <name>: <one line on what it does>

## Purpose
Why this skill exists. The job it does and the failure it prevents.

## When invoked
The situations that call for it, and the phrases that trigger it.
Also: when NOT to invoke it.

## Procedure
Numbered steps. Specific about inputs, outputs and checks.
Loose about method. A missing required input stops the run; it is never guessed.

## Quality gate
The conditions that hard-fail the run. Pass or fail, never "mostly".
A failed gate means nothing is written except the log line saying why.

## Output
Exactly which files it writes, and where. Always one of:
wiki/ (ingest only), drafts/, decisions/proposed/, log/.
Never raw/. Never decisions/resolved/.

## Log
The JSON line it appends to log/runs.jsonl. Must include "actor".

## Failure modes
The ways this skill goes wrong in practice, learned from real runs.
This section grows. A skill with no failure modes has not been used yet.
```

## Rules for the schema itself

- **Name:** verb-noun, lowercase, dashed. `ingest`, `lint-brain`, `draft-weekly-note`.
- **Status:** an agent-drafted skill is `draft` until the owner finalises it. A draft is not authoritative; run it only when the owner asks.
- **Catalogue:** every skill appears in `skills/README.md` with its status. `lint-brain` checks this.
- **One job:** if a skill needs the word "and" in its one-line description, it is probably two skills, or one skill with an option.
