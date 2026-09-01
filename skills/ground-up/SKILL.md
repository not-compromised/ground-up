---
name: ground-up
description: The learning system's engine — study a repo from the ground up through cleanup PRs, and run the two learning gates on everyday changes in any repo that has a study plan; use for "ground-up", continuing a repo's study, or resuming the cleanup.
---

# ground-up — the repo is the curriculum

The user is closing the gap between directing AI and reading/owning code, using their
own production repos as the course material. Two jobs live here: **study sessions**
(dedicated, invoked with "ground-up") and **everyday gates** (any work session in a
governed repo — one whose study plan exists).

The ledger repo holds all evidence and defines the grammar (statuses, grades, tags,
escalation) in its `AGENTS.md` — read that first if it isn't already loaded. Your
global agent context names the ledger's path; study plans live in the ledger's
`plans/<project>.md`, one per governed repo. **Rule zero: only unaided answers are
evidence** — the user answers first, the agent corrects after.

## Everyday gates (any session in a governed repo)

1. **Session start:** read the repo's study plan. Defer the learning log — deferred on
   purpose, so the user's level cannot sway design.
2. **Design freezes first.** Work out the best solution to the ask, full stop. The
   design never bends for teaching; if the best answer is beyond the user, that is
   what gates are for.
3. **Gate A — who writes it?** Only now read the learning log and syllabus. Judge the
   frozen design's distance from the user's frontier:
   - **self-written** — within reach: the user writes the change; the agent coaches
     (hints, not code) and reviews.
   - **near** — the agent writes it; prediction questions come at Gate B.
   - **over** — the agent writes it at full speed; the change's description gets a
     `ground-up: revisit after <topics>` note for a future study session.
4. **Gate B — rides the pre-ship review:**
   - self-written → review the user's change the way a senior would, concretely.
   - near → 2–3 prediction questions ("does hunk 2 change behavior?", "what does
     this return for X?") answered unaided before any explanation; grade per the
     ledger grammar; then ship.
   - over → ship with the tag. No lesson forced.
   Every stop is skippable — a skip becomes a tag, never a failure. Name the concept
   before offering the skip, so the tag has a row to land on. Same for `over` — the
   `revisit after <topics>` topics ARE concept rows, and each gets a `[revisit:...]`.
5. **Bookkeeping:** graded answers → the learning log; position → the study plan.
   A concept at the escalation line (grammar: three tags, or partial/gap twice) →
   queue its consolidation lesson in the study plan.

## Study sessions ("ground-up" in a repo)

**START** (no study plan yet): read the project's contribution rules (how changes are
proven and shipped there). Survey the codebase — layers, worst files, comment noise.
Read the user's current state (log + syllabus). Then write `plans/<project>.md`: the
app's layer map ordered pedagogically from the user's frontier (small pure functions →
one module → data model → request path → architecture), a chunk checklist (a chunk =
one reviewable PR, ~5–15 files or one subsystem), and per-chunk notes where proving
commands are missing. File one tracking issue in the repo linking the plan.

**CONTINUE:** read the study plan, reconcile with reality (merged PRs, `git log`),
state the next chunk in one line, work it. Study sessions open by draining relevant
`inbox/` items and `revisit` tags, and by re-testing 🔶/🔵 concepts the chunk touches.

**Session-open line (both modes, before anything else).** Run the totals from the
ledger's `queries.md` and report in ONE line: skip/revisit counts, the oldest
unresolved tag, and any row at three. Say it even when everything is zero — a silent
counter is indistinguishable from one that never ran. If `skip` exceeds the number of
open chunks, say so plainly; that is the drift signal the counter exists to catch.

**Working a chunk:** its own branch, named per the repo's convention. Phase 1 — a
comments-only pass (before deleting any comment, check it for a fact recorded nowhere
else — rewrite that one, delete the rest). Phase 2 — behavior-preserving
simplification only, proving commands before AND after; no proving commands →
trivially-verifiable steps or propose tests first; any trade-off is the user's
decision. The PR description teaches: what was cut, why it's safe, and which hunks are
worth reading closely — keep the diff readable on a phone. Gate B applies to every
chunk PR; merging is always the user's call.

## First-contact encoding (both modes)

When work touches a new at-frontier concept, the stop is a *generation prompt*, never
a delivery: ask the user to predict, place, or relate it ("what do you think this
middleware does?", "where would this break if the DB call failed?") — two to five
minutes, then work resumes. Full consolidation belongs to study sessions, not
mid-task. Tired user → skip and tag, no ceremony.
