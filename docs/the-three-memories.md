# The three memories

A brain that keeps everything in one pile cannot tell the difference between what is true, what you like, and how a job gets done. So it mixes them up. Your preference for short sentences ends up treated as a fact about your clients. A one-off workaround becomes "how we do things".

This starter keeps three kinds of memory in three places, each with its own rule for who may change it.

| Memory | Question it answers | Lives in | How it changes |
|---|---|---|---|
| **Facts** | What is true, and how do we know? | `raw/`, `wiki/`, `decisions/resolved/` | `raw/` never changes. `wiki/` changes only through `ingest`. `decisions/resolved/` changes only when the owner rules. |
| **Preferences** | How does the owner want it done? | `instructions.md` | Only to record the owner's own feedback, logged word for word in `log/feedback.jsonl`. |
| **Procedures** | How is this specific job done? | `skills/` | Only through `extend-toolkit`, as a draft, finalised by the owner. |

## Why facts are read-only

Every task reads facts. Almost no task should write them. If a drafting task can quietly change a wiki page, the next draft cites the changed page, and in a month nobody can say where a claim came from. Read-only does not mean frozen: it means one named writer per store, so every change has a single, logged cause.

`raw/` is the strictest. It is what was actually said or written, in its original mess. Everything else can be rebuilt from it. Raw is sacred.

## Why preferences are separate

Preferences are opinions, and they belong to a person. Keeping them in `instructions.md`, edited only from that person's own words, means the agent never promotes its own taste to a rule. When a preference changes, `log/feedback.jsonl` shows who said what, and when.

## Why procedures are authored

A procedure that lives only in a chat transcript is gone next session. Writing it down as a skill, with a quality gate, means the next session runs the same job the same way, and fails the same way loudly instead of differently and quietly. That is how a brain grows tools rather than habits.

## The test

When you are not sure where something belongs, ask:

- Could a source prove it wrong? **Fact.**
- Would a different owner want it differently? **Preference.**
- Is it a sequence of steps someone will repeat? **Procedure.**

Credit: the three-memory model is from Answer This, YC Root Access, video 04.
