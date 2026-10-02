# Next prompts

Paste them as-is. In Claude Code you can also just say the skill's name.

## After you have put one real file into raw/

```
Read everything new in raw/ and update the wiki. Follow the rules in
CLAUDE.md and skills/ingest.md. Create whatever folders the material
actually needs, and tell me why you chose them.
```

## Every time the brain irritates you

```
That page went into the wrong folder. Update CLAUDE.md so it does not
happen again.
```

If the irritation is about taste (a word, a tone, a format), it belongs in `instructions.md`, not `CLAUDE.md`:

```
Record this as my feedback, word for word, in log/feedback.jsonl, then
update instructions.md to match. Show me the diff: "<your exact words>"
```

## When you catch yourself asking for the same thing twice

```
We have done this by hand twice now. Run skills/extend-toolkit.md and
draft a skill for it. Test it once on a real file. Leave it as a draft
for me to approve.
```

## Weekly, or every ten ingests

```
Run skills/lint-brain.md. Report every check as PASS, FAIL or NOT RUN.
Fix only mechanical references outside raw/, wiki/ and
decisions/resolved/. File everything else for me.
```

## When something needs deciding

```
Draft a decision memo from decisions/_template.md for this question:
"<the question>". Required stances: <names>. Use only stances people
actually gave, word for word, with sources. Everyone else is
"not yet captured". My stance stays "pending".
```
