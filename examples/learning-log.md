# Learning Log — concept tally (example)

A fabricated ledger showing the format — copy this file to your repo root as
`learning-log.md` and empty the tables. One row per concept taught in any session.

Statuses:
- ✅ **solid** — demonstrated unaided
- 🔶 **refresh** — taught once; re-test before calling it known
- 🔵 **open** — exercise assigned, not yet completed

**Inline tags** append to a row's Hook cell, newest last, and are never rewritten —
the count is `grep -c`, so it cannot drift. Never contains a `|`.

- `[applied:<repo> MMDD]` — concept used unaided in another repo (the transfer test)
- `[skip:MMDD]` — a gate stop declined
- `[revisit:MMDD]` — agent wrote it; flagged to come back

Three tags on one row → the concept has earned a consolidation session; queue it in
the repo's study plan. Counting recipes: `queries.md`.

## Example section — one per learning track
| Concept | Status | Hook |
|---|---|---|
| `function` / parameters / `return` | ✅ solid | A machine: inputs in → output back. Explained unaided 2026-03-02 |
| Promises / `await` | 🔶 refresh | "A receipt for a value that isn't ready yet" — taught 2026-03-05, re-test due |
| SQL JOIN | 🔶 refresh | Rows glued by a shared key; predicted the wrong row count once [skip:0310] |
| Middleware order | 🔵 open | Trace one request through the stack, unaided — assigned 2026-03-08 [revisit:0308] |

## Encountered, not yet studied
Concepts a shipped change touched before they were taught (Gate A verdict `over`):
| Concept | Status | Hook |
|---|---|---|
| Connection pooling | 🔵 open | Saw it in the db module PR; study-plan chunk 3. [revisit:0311] |
