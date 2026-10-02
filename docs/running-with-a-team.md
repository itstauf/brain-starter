# Running it with a team

One brain, many doors. Several people can read the brain and act on it. Very few should be able to change what it believes.

## Read and act, versus write

Split the team in two, by what they do, not by seniority.

| Door | Who | Can |
|---|---|---|
| **Read and act** | Most people. Most agents. | Read everything. Run skills that write to `drafts/` and `decisions/proposed/`. Drop new files into `raw/` through a pull request. Give feedback. |
| **Write** | The owner, plus anyone the owner names | Approve changes to `CLAUDE.md`, `instructions.md`, `skills/`, `wiki/` and `decisions/resolved/`. |

Stances are how the read-and-act group shapes decisions without writing them: every decision memo carries a block for each person it touches, kept word for word. See `decisions/README.md`.

## CODEOWNERS

Put this in `.github/CODEOWNERS` (or the equivalent on your host). Replace the placeholder handles.

```
# Default: the owner reviews everything
*                       @<owner-handle>

# The constitution and preferences: owner only
/CLAUDE.md              @<owner-handle>
/instructions.md        @<owner-handle>

# Procedures: owner, plus a named second reviewer
/skills/                @<owner-handle> @<second-reviewer-handle>
/.claude/skills/        @<owner-handle> @<second-reviewer-handle>

# Facts the owner has ruled on
/decisions/resolved/    @<owner-handle>

# The wiki: whoever runs ingest day to day
/wiki/                  @<librarian-handle>
```

## Protected branches

- Protect `main`. No direct pushes, for people or agents.
- Require a pull request with at least one approval from a code owner.
- Require the `lint-brain` report to be attached to any pull request that touches `wiki/` or `skills/`. If you automate it, make it a required status check.
- Agents work on their own branches and open pull requests. An agent never merges its own pull request.

## Review gates

- **Drafts** go through review before anyone outside the brain sees them. If you install the-critic, its critique is attached to the draft.
- **New skills** arrive as `status: draft` and become `published` only on the owner's approval.
- **Decisions** move to `resolved/` only by the owner, with every required stance present and dissent unchanged.

## When groups must not see each other

Git does not hide part of a repo from someone who can read it. If two groups must stay separate (two clients, two ventures), run two brains. Share only methods between them, after removing anything that identifies either side, and log every transfer.

## Agents as team members

Give each agent a name and put it in the `actor` field of every log line. Give it the narrowest access that lets it do its job: usually read the repo, write to a branch, open a pull request. No agent holds a token wider than the one repo it works on.

More on this in the guide chapter: [One brain, many doors](https://itstauf.com/resources/second-brain/doors?utm_source=github&utm_medium=readme&utm_campaign=compounding-brain&utm_content=brain-starter).
