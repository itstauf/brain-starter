# decisions/: what was decided, who disagreed, and in their words

The owner decides. Everyone whose work the decision touches gets a stance block, and any dissent is kept word for word. Dissent that turns out to be right is the strongest learning signal a brain can get, so it is never smoothed away.

## Lifecycle

1. **Proposed.** A memo is written from `_template.md` into `proposed/DM-NN-<slug>.md`. Any skill may do this, including the escalation rule (a finding repeated three runs unchanged).
2. **Stances captured.** Each person in the stance list either gives a stance or stays `not yet captured`.
3. **The owner rules.** Their stance stays `pending` until they do.
4. **Resolved.** The owner moves the memo to `resolved/YYYY-MM-DD-DM-NN-<slug>.md`, fills in the ruling, and appends a line to `log/decisions.jsonl`.

## Naming

- Proposed: `DM-NN-<slug>.md`
- Resolved: `YYYY-MM-DD-DM-NN-<slug>.md`
- Take the next number from the filesystem (highest across both folders, plus one), never from a note.

## The four stance forms

There are exactly four. There is no fifth.

1. **A verbatim quote**, with `attributed_to`, date and source path.
2. **A verbatim quote labelled as an open question**, when the person raised the question without answering it.
3. **`deferred to <owner>`**, only when the person actually said so, with the source. Never inferred from silence.
4. **`not yet captured`.**

Not a paraphrase. Not "she would probably favour B". An invented stance is fabricated evidence inside the one record built to preserve disagreement.

## Hard rules

- Every required stance block appears, even if it says `not yet captured`.
- Dissent is never softened or summarised when a memo moves to `resolved/`.
- No decision by default. A memo that sits unanswered is still unanswered.
- A resolved memo is never edited to change its ruling. A new memo cites it and supersedes it.

See `_template.md` and the worked example in `../examples/decision-memo-example.md`.
