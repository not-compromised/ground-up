# ground-up — the learning system

The whole system in one place, for the user's head and for agents. This repo is the
**ledger half** of the system: all evidence of what the user actually knows, what comes
next, and the on-ramps for using it. The **plan half** (per-repo study plans) lives in
tools context; the **engine** (the rules agents run) is the `ground-up` skill.

**The goal:** close the gap between directing AI to build software and reading/owning
code unaided. The user's own production repos are the course material. **Rule zero:
only unaided answers are evidence** — nothing enters the ledger because an agent
explained it or the user watched it happen.

**This repo is PUBLIC.** The privacy line: this repo holds the *system* and the
*learning evidence*; personal and career material, workplace detail, infra plumbing,
and anything quoting private code live in the private life-HQ repo and never enter
this one. `inbox/` is gitignored for exactly that reason — captures quote private
code verbatim. When in doubt, it goes to the private side.

## The system in one picture

```
        everyday change (any repo
        with a ground-up.md)
                 |
        design frozen FIRST
                 |
   Gate A: who writes it?
   (reads learning-log + syllabus
    only AFTER design is frozen)
    self-written / near / over
                 |
   Gate B: rides the Ship gate
   coach review / predictions / tag
                 |
                 v
   +---------------------------+
   | THIS REPO (the ledger)    |
   |  learning-log.md  <-- evidence
   |  syllabus.md      <-- frontier
   |  inbox/           <-- confusion
   |  queries.md       <-- counting
   +---------------------------+
                 ^
                 |
        study session ("ground-up")
        works chunks from the repo's
        ground-up.md (tools context),
        drains inbox/, re-tests 🔶/🔵
```

## The parts

| Part | Where | Role |
|---|---|---|
| `learning-log.md` | this repo | **The evidence ledger, all repos.** One row per concept: ✅ solid (unaided demo) / 🔶 refresh / 🔵 open. Inline tags (`[applied:]` `[skip:]` `[revisit:]`) append-only in the Hook cell — counts are `grep -c`, so they cannot drift. |
| `syllabus.md` | this repo | **Concept frontier** per track (JS/Odin, Python reading, web layers) plus a beyond-my-stack shelf. Read at Gate A and when planning study sessions. |
| `queries.md` | this repo | **Counting recipes** for the ledger tags: session-open line, escalation (3 tags = earned a session), drift check (skips > open chunks). |
| `inbox/` | this checkout, **gitignored** | **Captured confusion**, one file per item, dropped mid-session by the `learning-inbox` skill. Questions only, never completed concepts; drained by study sessions, deleted when folded. Local-only: captures quote private code, so they never enter this public repo's history. |
| `evening-path.md` | this repo | **Tired-brain on-ramp**: zero-decision tracks A–D for after work. |
| `ground-up.md` (per repo) | `plan.md` in the governed repo | That repo's **study plan**: layer map, chunk checklist, current position. Its existence turns the gates on for that repo. Only dashboard has one so far; finance and firepos follow. |
| `ground-up` skill | `skills/ground-up/` | **The engine.** Everyday gates A/B, study-session mechanics, calibration, tag rules, persistence ceremony. |
| `learning-inbox` skill | `skills/learning-inbox/` | Capture-only writer for `inbox/`. Never teaches, never touches the ledger. |
| `code-coach` skill | `skills/code-coach/` | Socratic coaching on the user's own repos; graded outcomes land in the ledger. |
| `fell-asleep` skill | `skills/fell-asleep/` | Resume after a gap: quiz on what was covered (spaced review), grade per calibration, continue. |
| tutor charter | not shipped | Teaching rules for tutor-mode sessions (never write code before the user tries, one concept at a time, …). |
| wins | private life-HQ repo | Accomplishments stay there — wins are life-HQ records, not learning evidence. |

## The two modes

- **Everyday gates** — any work session in a repo that has a `ground-up.md`. Design
  freezes first (the log is deliberately not read until Gate A, so the user's level
  can't sway design). Gate A judges distance from the frontier: *self-written* (user
  writes it, agent coaches) / *near* (agent writes, prediction questions at Gate B) /
  *over* (agent writes at full speed, PR gets a `revisit after <topics>` note and each
  topic gets a `[revisit:]` tag here). Every stop is skippable — a skip becomes a
  `[skip:]` tag, never a failure.
- **Study sessions** — invoked with "ground-up" in a repo. Work the next chunk from
  that repo's `ground-up.md` as a cleanup PR; open by reporting the queries.md
  session-open line, draining relevant `inbox/` items and `revisit` tags, and
  re-testing 🔶/🔵 concepts the chunk touches.

## Evidence rules (the short version)

- ✅ solid only after an unaided demonstration. No fake checkoffs, no refusing real ones.
- Grades: `solid` / `partial` (→ 🔶) / `gap` (→ 🔶 with the missing foundation named).
- Cross-repo unaided use of a logged concept → `[applied:<repo> MMDD]` — the transfer test.
- Three tags of any kind on one row, or partial/gap twice → that concept has earned a
  consolidation session; the matching Odin lesson gets queued in the repo's
  `ground-up.md`. **Odin is a mine, not a march** — never walked linearly.
- Tags live only in ledger rows, never in PRs; if the row wasn't written, the tag
  didn't happen.

## Routing & ceremony

- **This repo is not a live artifact** — no cron writes it, nothing serves from it.
  Ledger updates commit directly on `main` in this repo
  (`git pull --rebase` first). The automation exception (agents commit + push without
  asking) covers diffs touching only `learning-log.md` and `syllabus.md`. Anything
  else in the diff = normal ceremony — and because the repo is public, every commit
  is also a publication: nothing job-search, workplace, private-infra, or
  private-code flavored, ever.
- **Per-repo `ground-up.md` plans** stay in tools context → capture exemption
  (direct commit to tools master + push).
- **No rendered surface.** Earlier HTML mirrors (a dashboard Learn tab, a reference
  page) are retired — mirrors went stale; this README and the ledger are the only
  sources of truth.

## History

Extracted from the private life-HQ repo's `learning/` 2026-08-31 and made public the
same day (personal material split back out; pre-extraction git history stays private).
Before that: a standalone `learn` repo, folded into the life HQ 2026-08-05; the drip
system retired 2026-08-25, replaced by the ground-up system.
