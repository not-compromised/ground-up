# ground-up

I built working software — a point-of-sale system, a trading bot, a server full of
services — by directing AI. I can't yet read most of the code I own. This repo is the
system my coding agents and I use to fix that, and the live evidence of how it's
going.

The idea: **my own repos are the curriculum.** Instead of working through a course and
hoping it transfers, my agents teach me the code I already ship — and every everyday
change they make becomes a small lesson at exactly my level.

Two rules make it honest:

- **Rule zero — only unaided answers count.** Nothing gets marked "known" because an
  agent explained it or I watched it happen. I answer first; the agent corrects after.
- **Design never bends for teaching.** The agent works out the best change first, and
  only then decides whether I write it, predict it, or just watch it ship with a flag
  to revisit.

Everything runs on one ledger: [learning-log.md](learning-log.md) is my actual
learning state, tracked concept by concept, in public. The gaps and stalls are in
there too — that's the point.

## Use it yourself

The whole system ships here, generalized so it isn't wired to my machines:

1. **Copy the repo** and start your ledger from [examples/](examples/) (a fabricated
   ledger, syllabus, and study plan showing the format — my real ones live at the
   repo root).
2. **Install the skills** from [skills/](skills/) into your agent (Claude Code:
   `~/.claude/skills/`) — the engine ([ground-up](skills/ground-up/SKILL.md)), plus
   capture ([learning-inbox](skills/learning-inbox/SKILL.md)), Socratic coaching
   ([code-coach](skills/code-coach/SKILL.md)), and resuming after a gap
   ([fell-asleep](skills/fell-asleep/SKILL.md)).
3. **Point your agent at it**: [AGENTS.md](AGENTS.md) is the grammar agents load; add
   one line to your global agent context naming your ledger's path.
4. **Say "ground-up"** in the repo you most want to be able to read. The agent surveys
   it, writes a gitignored `plan.md` there, and from then on everyday work in that
   repo runs the learning gates.

How every part fits together — the gates, the tags, the ceremony — is in
[SYSTEM.md](SYSTEM.md).

MIT licensed. If you try it, I'd genuinely like to hear how it goes.
