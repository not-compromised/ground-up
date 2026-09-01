# AGENTS.md — the ground-up learning system

Agent context for this ledger repo. The human here is closing the gap between
directing AI to build software and reading/owning code unaided; their own repos are
the course material. [SYSTEM.md](SYSTEM.md) is the full map; this file is the
grammar an agent needs loaded while working the system.

**Rule zero: only unaided answers are evidence.** Assisted performance inflates what a
learner appears to know. Nothing enters the ledger because the agent explained it or
the user watched it happen — the user answers first, the agent corrects after. An
explanation given before the user has guessed deletes the lesson.

**A public ledger makes every commit a publication.** Learning evidence belongs here;
employer detail, job material, and verbatim private code stay out (`inbox/` is
gitignored for exactly that reason). When in doubt, it stays out.

## The ledger grammar

**Statuses** — one row per concept in [learning-log.md](learning-log.md):
✅ **solid** (demonstrated unaided) · 🔶 **refresh** (taught once; re-test before
calling it known) · 🔵 **open** (exercise assigned, unfinished).

**Grades** — every answer the user gives: `solid` (correct unaided → eligible for ✅)
· `partial` (core idea present, a meaningful piece missing → 🔶) · `gap` (mental model
wrong or absent → 🔶 with the missing foundation named in the row's hook).

**Tags** append to a row's Hook cell, newest last, and are never rewritten — a count
is `grep -c`, so it cannot drift or double-increment. A tag never contains `|` (these
live in table cells), and a tag must name a concept row: if the row wasn't written,
the tag didn't happen (a note in a PR dies with the PR).

| Tag | Written when |
|---|---|
| `[applied:<repo> MMDD]` | a logged concept used unaided in another repo — the transfer test |
| `[skip:MMDD]` | a gate stop declined |
| `[revisit:MMDD]` | the agent wrote the change at full speed; flagged to come back |

**Escalation:** three tags of any kind on one row, or a concept graded partial/gap
twice, means it has earned a consolidation session on evidence, not mood — queue the
matching external lesson in that repo's study plan. Lessons are a mine, not a march:
prescribed per stuck concept, never walked linearly.

## The files

| File | Role |
|---|---|
| [learning-log.md](learning-log.md) | The evidence ledger, all repos — single source of learning state |
| [syllabus.md](syllabus.md) | Concept frontier per track; read when judging distance from the frontier |
| [queries.md](queries.md) | Counting recipes for the tags — read it rather than composing greps |
| `plans/<project>.md` | A repo's study plan: layer map, chunk checklist, position. Its existence turns the gates on for that repo (format: `examples/plan.md`) |
| `inbox/` (gitignored) | Captured confusion, one file per item — questions pending teaching, never completed concepts |

## Working in a governed repo

A repo is governed when it has a study plan. Sessions there run the two learning
gates — full mechanics in [skills/ground-up/SKILL.md](skills/ground-up/SKILL.md). The
spine: **design freezes before the ledger is read** (the learner's level never sways
design); Gate A judges the frozen design's distance from the frontier and decides who
writes it; Gate B asks prediction questions at ship time, answered unaided before any
explanation. Every stop is skippable — a skip becomes a tag, never a failure.

## Bookkeeping

- Teaching anything, in any session type: new concepts → 🔶, unaided demos → ✅,
  unfinished exercises → 🔵. Study sessions re-test 🔶/🔵 before new material;
  everyday gates grade only what the change touches.
- Ledger commits go directly on the default branch (`git pull --rebase` first);
  structural changes to the system get a branch and review.
- Confusion surfacing mid-task → capture to `inbox/` and keep moving
  ([skills/learning-inbox/SKILL.md](skills/learning-inbox/SKILL.md)); teaching happens
  in a later session, which also does the tally.
