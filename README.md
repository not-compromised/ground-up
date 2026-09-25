# ground-up

I build software by directing AI agents that write the code, and I
can't read most of it. This repo is how I own it anyway: not by
learning to read it, but by holding the rules its money and data must
always obey.

## Three layers

```
3  what it should do for me
   owner: me, by using it
2  what must always be true
   owner: me, as standing rules
1  how the code does it
   owner: the agent
```

Layer 2 is the one nobody owned. A standing rule is a sentence about the
app's data that must be true at every moment, no matter which feature
just ran: "a refund lowers the category it came from and never counts
as income." [MODEL.md](MODEL.md) is the full model.

## The loop

```
use the app
     |
     v
bug found
     |
     v
I state the rule it broke, unaided
     |
     v
agent makes it executable
(check, test, or constraint)
     |
     v
one ledger row
```

Only unaided answers count. If an agent explained the rule first, it
goes on the re-test list, not the ledger.

## What is here

| file | what |
|---|---|
| [MODEL.md](MODEL.md) | what a standing rule is, how to spot one, how to know you hold one |
| [ledger.md](ledger.md) | the rules I can state cold, across my repos |
| [queries.md](queries.md) | counting recipes for the ledger |
| `inbox/` | gitignored, local: questions caught mid-work |
| [skills/](skills/) | the agent skill that runs an invariants pass (lands next) |
| [AGENTS.md](AGENTS.md) | the grammar an agent loads to work the method |

## Use it yourself

1. Copy [MODEL.md](MODEL.md) and read it once.
2. Run an invariants pass on the repo you most want to own. Write your
   rules from memory first. Have an agent mine the code, tests and docs
   for the rest. Grade every row: Knew it / Makes sense / Disagree /
   Unclear. Put the result at the repo root as `INVARIANTS.md`, columns
   `rule | enforced by | born from | held`.
3. Add the diagnosing-bugs tail: every bug ends with you stating the
   rule it broke, before the agent explains anything.
4. Keep a ledger of the rows you can say cold. Point your agent at
   [AGENTS.md](AGENTS.md).

## First pass

A personal finance app, 2026-09-25:

| | |
|---|---|
| rules on the list | 38 |
| could say cold | 7 |
| new and agreed | 29 |
| disagreed | 0 |
| reworded | 6 |
| born from the owner | 2 |

Zero disagreements means the rules were mine; seven says they were never
in my head as rules.

MIT licensed.
