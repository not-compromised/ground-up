# AGENTS.md: the invariants method

Agent grammar for this repo and for any repo that runs the method. The
user owns layer 2, the standing rules (invariants) an app's money and
data must always obey, in their own words. [MODEL.md](MODEL.md) is the
model; this file is what an agent does with it.

## Rule zero

Only unaided answers are evidence. The user answers first; the agent
corrects after. An explanation given before the user has guessed deletes
the lesson. A rule enters the ledger because the user stated it cold,
never because the agent explained it or the user watched it happen.

## Three layers

| layer | what | owner |
|---|---|---|
| 3 | what it should do for me | the user, by using the app |
| 2 | what must always be true | the user states the rules; the agent keeps them executable |
| 1 | how the code does it | the agent |

## The row in a repo's INVARIANTS.md

One file per repo, tracked at the root, one row per rule:
`rule | enforced by | born from | held`.

- **rule**: the user's words. Reword only with the user.
- **enforced by**: name the check, test or constraint, and its form:
  `integrity/runtime check`, `test`, `schema constraint`, `doc only`,
  `not yet`. `doc only` and `not yet` are todos.
- **born from**: the issue or incident; `owner` when the user added it.
- **held**: the date the user stated it unaided; blank until then.

The agent finds where each rule is enforced, makes it executable, and
keeps the row current. One line in the repo's `AGENTS.md` sends every
agent to the file before money or data-model work.

## The ledger row here

[ledger.md](ledger.md): `repo | rule | held | tags`. `held` is
`YYYY-MM-DD`; `repo` is `root` for a truth every app obeys. Tags append
to the tags cell, newest last, never rewritten, never containing `|`:
`[applied:<repo> MMDD]` (used unaided in another repo), `[partial:MMDD]`,
`[gap:MMDD]`. A partial or gap row waits in the re-test table and moves
up, tags and all, on the day of an unaided pass. If the row was not
written, the tag did not happen. Counts: [queries.md](queries.md).

## Holding a rule

Three checks, no app open:

1. Say the rule in one sentence.
2. Say what breaks if it is false.
3. Say where it is enforced, or that it is not yet.

Three is held (a dated ledger row), two is partial, one is gap.

## Three moves

- **Invariants pass**: user writes rules from memory first; agent mines code, tests and docs; user grades each row Knew it / Makes sense / Disagree / Unclear; land `INVARIANTS.md` and ledger rows.
- **Diagnosing-bugs tail**: after the diagnosis, ask the user for the rule the bug broke before explaining; grade it, name the class, add or mark the row, and give the fix an enforcement point.
- **Ship gate**: ask which rule this change touches and whether it created one; new rows land in `INVARIANTS.md` in the same PR.

## Public repo

Every commit here is a publication. Write rule sentences only: what the
user's own app must do. Private file paths, amounts, balances, tokens,
employer or job material, and verbatim private code stay in private
context or in `inbox/`, which is gitignored. When in doubt, it stays out.
