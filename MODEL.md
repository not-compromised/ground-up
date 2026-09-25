# Standing rules: the mental model

Written 2026-09-25 from the first invariants pass, on a personal finance app.
Written for the owner first, agents second.

## What a standing rule is

A standing rule is a sentence about your app's data that must be true
at every moment, no matter which feature just ran. The real name is
*invariant*: a thing that does not vary. Use either word.

The test for whether a sentence is one: **if it were false, would the
app be wrong even though nothing crashed?** If yes, it is a standing
rule. If the sentence is about what the app does for you, it is a
feature, not a rule.

```
feature   I can add a bill
rule      a bill is paid once per cycle
feature   I can move money to savings
rule      no dollar is counted twice
```

Features change every week. Rules stay, and every new feature has to
obey all of them. That is why they are yours to hold: the agent works
on one feature at a time and sees one rule at a time, the one in the
ticket. You are the only one who sees the whole list.

## The three layers

```
3  what it should do for me    you, by using it
2  what must always be true    standing rules
1  how the code does it        the agent
```

You already own layer 3 completely. The agent owns layer 1 and gets
better at it every year. Layer 2 was owned by nobody. Finance had 36
rules in its code and tests, 14 of them written in no document an agent
loads, and you could say 7 of them from memory. That is what "nobody
owns layer 2" looks like with a count on it.

## How to recognize one

Five questions surface rules. Ask them about any number the app shows
and any feature about to ship.

1. **What must be true for this number to be right?** Left-to-spend is
   right only if every unpaid bill was subtracted exactly once.
2. **Can this happen twice?** Two card rows on one account, two payment
   schedules, two auto-detected items for one paycheck. The whole
   double-counting family lives behind this question.
3. **Who else counts this dollar?** A refund, a transfer, a card charge
   and its payment. Every dollar has exactly one home.
4. **What does it look like when this silently did nothing?** An empty
   database is "healthy." A check that did not run is "clean." A
   5-day in-transit leg "drops out on its own." If the answer is
   "the same as success," that is the bug.
5. **And then what?** Follow the data one step past where the feature
   stops. Unlink revokes at Plaid, and then deletes the history.

## The four kinds, with finance examples

| kind | example |
|---|---|
| counting | unproven money is shown but not counted |
| identity | one payment schedule per card |
| time | one place decides what day it is |
| failure | a failed write leaves nothing behind |

Counting rules keep numbers honest. Identity rules stop one real thing
from existing twice. Time rules keep "today" and "paid" from drifting.
Failure rules make a failure leave a clean state and a visible mark.

## Roots and app rules

A handful of rules are true for every app you will ever build: integers
for money, a failed write leaves nothing behind, absence must look
different from success, one place decides the day, a repeated write
changes nothing. Those are the roots. They go in the fleet context once
and every agent loads them.

Every other rule belongs to one app and is born when you add a feature.
"Which charge pays which cycle" did not exist until bills had cycles.
Nobody can write those ahead of time. Someone has to notice the moment
a feature creates a rule, and that someone is you, because the agent is
looking at the ticket.

## How a rule is enforced

A rule written down is a wish. A rule enforced is a fact. Three forms:

| form | when it runs | catches |
|---|---|---|
| schema constraint | every write | the impossible row |
| test | before merge | the regression |
| runtime check | after every sync | what nobody foresaw |

The strongest rules have two. A rule with none is a todo, and the list
shows it as "not yet."

## The list

One file per repo, at the root, beside AGENTS.md. One row per rule.

```
rule, in your words | enforced by | born from | held
```

"Enforced by" names the check, test, or constraint, or says "doc only"
or "not yet." "Born from" is the issue or incident. "Held" is the date
you said it unaided. The file is tracked with the code, and one line in
AGENTS.md makes every agent read it before touching money or the data
model.

## Your job and the agent's

```
you            state the rule, in your words
you            notice a new rule was born
you            correct a rule that reads wrong
agent          find where it is enforced
agent          make it executable
agent          keep the row current
```

## A worked example

Issue 159: one monthly subscription showed as three PAID bills. The fix
that shipped removed the extra rows. The rule underneath: **a bill is
paid once per cycle.** It was not written anywhere, so the same class
had already come back four times under other names. With the rule in
the list, the fix becomes: add the check, then make the fix pass it.
The next agent that touches bills trips the check, not you.

## How you know you hold one

Three checks, no app open:

- You can say the rule in one sentence.
- You can say what goes wrong if it is false.
- You can say where it is enforced, or that it is not yet.

Two out of three is "partial." One is "gap." All three, dated, is a
row you hold.
