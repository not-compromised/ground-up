# examples/plan.md — what a study plan looks like

A repo's study plan lives at `plan.md` in that repo's root, gitignored. Its
existence turns the learning gates on; the `ground-up` skill writes the file and
adds `/plan.md` to `.gitignore`. Never commit it. The shape:

```markdown
# <project> — study plan

Why this repo now: <smallest/most-read/highest-leverage — one sentence>.
Milestone when the checklist is done: the user explains <scope>, unaided, end to end.

**Proving commands (phase 2 gate):** <test command, smoke check>
**Hazards:** <live-artifact rules, files agents must not touch, repo-specific gotchas>

## Layer map (reading order = curriculum order)
<layers ordered pedagogically from the user's frontier:
small pure functions → one module → data model → request path → architecture>

## Chunks
A chunk = one study session = one reviewable PR (~5–15 files or one subsystem):
phase 1 comments pass, then phase 2 behavior-preserving simplification where proving
commands cover it.
- [ ] 1. <files>. Concepts: <what this chunk teaches>.
- [ ] 2. ...

## Ops is exempt
Gates fire on chunk PRs and planned feature work only. Incident and ops work runs at
full speed with no stop — anything confusing there goes to `inbox/` for later.

## Consolidation queue
Concepts at the escalation line (three tags, or partial/gap twice) get queued here as
their own sessions.
_(empty)_

## Position
<dated notes: what's done, what's next — one line per session>
```
