---
name: invariants
description: Use when the user asks for an invariants pass on a repo, or to state, grade, or record a standing rule.
---

# Invariants pass

A **standing rule** (an invariant) is a sentence about an app's money or data that must hold at every moment, whatever feature just ran. The owner holds the rules in their own words; the agent finds where each one is enforced and makes it executable. The method and its mental model live in this repo's `MODEL.md`.

**Rule zero: only unaided answers are evidence.** The user answers first; you correct after. An explanation given before the user has tried deletes the evidence.

## Grading vocabulary

Grade every free-text answer against the three checks for holding a rule:

1. Say the rule in one sentence.
2. Say what goes wrong if it is false.
3. Say where it is enforced, or that it is not yet.

All three is **solid**; two is **partial**; one or none is **gap**. Name the missing check when you grade.

## 1. Open

Read the project's `AGENTS.md`, any existing `INVARIANTS.md` at the repo root, and any items for this repo in this repo's `inbox/` (grade each as a free-text question in step 4, then delete its file). Before showing anything, ask the user to write the repo's rules from memory, one line each. Wait for the list. Done when you hold the user's list verbatim.

## 2. Mine

Dispatch one read-only subagent (Opus where the client offers a model choice) with this brief, filled in:

```
Read-only. Repo: <checkout path>. Agent context: <where the project's agent instructions live>.
Find every standing rule this app's money and data obey. Read: the project
AGENTS.md and every supplement it points to; runtime self-checks
(integrity/health checks); schema constraints (UNIQUE, NOT NULL, CHECK,
foreign keys); test names and docstrings; module docstrings; the project's
and the global war-stories; `git log` subjects of fix-type commits.
Return a table: rule (one plain sentence a person could say from memory,
no code) | enforced by (integrity: <check> / test: <file>::<name> /
schema: <constraint> / runtime: <function> / doc only / not yet) |
born from (issue, commit, incident) | how sure (stated / inferred).
Order rows: money counting, identity, time, sync and failure, data and
schema, ops. 20 to 40 rows. Then three lists: enforcement gaps (doc only
or not yet), unwritten rules (enforced but stated in no doc an agent
loads), contradictions (doc vs code, each with file:line).
```

Done when the table and all three lists are back. Spot-check a few `enforced by` cells against the code before using them.

## 3. Diff

Show the user's memory list against the mine in one small table: matched, app contradicts, enforced but unlisted. State the three counts. End the turn here, so the grading questions arrive in a turn of their own.

## 4. Grade

Walk every mined row with the client's structured-question tool (`AskUserQuestion` in Claude), three rules per turn, one question per rule. Options, exactly:

- **Knew it** (could have stated it before today)
- **Makes sense** (new, agree)
- **Disagree**
- **Unclear** (reword)

Per answer:

- **Unclear**: reword in the user's vocabulary and re-ask.
- **Disagree**: work the rule out from the code with the user until it is reworded or changed. A rule the user corrects takes the user's wording.
- **Free text**: answer it from the code, never from memory, before moving on. "Does it do X?" and "and then what?" are how new rules are born: check the code, and when the answer is "no" or "silently", add a row with enforced by `not yet` and born from today's pass.

On a mobile client a fenced code block may not render in the same turn as a structured question; keep fences out of grading turns. Done when every row has a grade and every born row is in the table.

## 5. Write

`INVARIANTS.md` at the repo root, beside `AGENTS.md`, tracked with the code:

```
| rule | enforced by | born from | held |
```

- **rule**: the user's wording wherever they gave one (reworded and corrected rows included); otherwise the mined sentence as graded.
- **enforced by**: the mine's cell, `doc only`, or `not yet`.
- **held**: today's date for rules from the step-1 memory list, **Knew it** rows, and rows born from the user; blank otherwise.

The file is doc only; it changes no behavior. Open the PR under the repo's usual process. In a money repo, the money review applies to the later enforcement PRs, not this one. After it merges, add one pointer line to the project `AGENTS.md` in your agent context: before money or data-model work, read `INVARIANTS.md` at the repo root.

A rule that already appears in another repo's `INVARIANTS.md` is a root: propose it for your shared roots file; the user approves that edit.

## 6. Ledger

Append the held rows and the born rows to `ledger.md` in this repo, in the format defined there. The ledger is public: rule sentences only.

Report the counts in one line: rules on the list, knew it, makes sense, disagree, reworded, born from the user.
