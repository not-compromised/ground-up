---
name: fell-asleep
description: Resume after the user vanished mid-session — reconstruct where things stood, quiz them on what was covered (the gap doubles as spaced review), then continue the work; use when the user says "/fell-asleep", "I passed out", or returns after hours or days away.
---

# fell-asleep — the gap becomes the review

The user falls asleep at the computer or gets pulled away, and comes back to an open
thread hours or days later. The interruption is not a loss: a delay before recalling
material is exactly when retrieval practice pays. This skill turns the resumption into
a short review, then puts the work back in motion. Never punish the gap — no ceremony,
no guilt, and the whole refresh is skippable ("just continue" honors it instantly).

## Steps

1. **Reconstruct.** From the open conversation — or, if context was lost to
   summarization or a fresh session, from `git log` on the repos touched, open PRs,
   and any ledger/tracking files the session maintained — establish: what was being
   built, what was decided, what was taught or graded, and what was mid-flight. Say
   plainly what could not be recovered rather than guessing.
2. **Scale the refresh to the gap.**
   - A few hours: one or two re-anchor questions on the most load-bearing thing from
     the session.
   - A day or more: a retrieval pass over each concept the session touched, hardest
     first.
3. **Quiz generation-first.** Ask; the user answers unaided; correct after. Never
   open with a recap lecture — a recap before they've tried recalling deletes the
   retrieval benefit. Grade per the ledger grammar (the ledger repo's `AGENTS.md`:
   `solid` / `partial` / `gap`) and update its `learning-log.md` accordingly — unaided
   answers only. A concept already graded partial/gap in a prior session that misses
   again here counts toward the stuck-twice consolidation trigger.
4. **Re-anchor the work.** One short block: done / mid-flight / next. Diagrams over
   prose if the state has structure.
5. **Continue** the interrupted task exactly where it stood.

## Boundaries

- Refresh questions come from what THIS session covered, not the whole log — the
  broad re-test lives in ground-up study sessions.
- If the user opens with new work instead of "/fell-asleep", follow them; offer the
  refresh once, drop it if declined.
- Keep the whole refresh under ~5 minutes unless the user leans in.
