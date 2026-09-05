# Learning Log — concept tally

Single source of truth for all learning state — no rendered surface, read it here.
Every concept taught in any session gets a row. Statuses:
- ✅ **solid** — demonstrated unaided
- 🔶 **refresh** — taught once; re-test before calling it known
- 🔵 **open** — exercise assigned, not yet completed

**Inline tags** append to a row's Hook cell, newest last, and are never rewritten —
the count is `grep -c`, so it cannot drift or double-increment. Never contains a `|`.

- `[applied:<repo> MMDD]` — concept used unaided in another repo (the transfer test)
- `[skip:MMDD]` — a gate stop declined
- `[revisit:MMDD]` — agent wrote it; flagged to come back

Three tags on one row → that concept has earned a consolidation session; queue it in
the repo's study plan. Counting recipes: [queries.md](queries.md).

Session detail and anything job-search-flavored is private and lives outside this repo.

_Last updated: 2026-07-14_


## Code (JS/TS — own repos)
| Concept | Status | Hook |
|---|---|---|
| Comments (`//`) | 🔶 refresh | Notes for humans; computer ignores |
| `function` / parameters / `return` | 🔶 refresh | A machine: inputs in → output back |
| `export` | 🔶 refresh | "Let other files use this" |
| TypeScript type annotations (`: number`) | 🔶 refresh | A promise about what kind of value |
| Operator precedence / parentheses | 🔶 refresh | Inner parens first, like math class |
| `Math.round` | ✅ solid | Answered 64.935→65 unaided (2026-07-06) |
| Integer money math (cents + basis points) | 🔶 refresh | Computers are bad at decimals (0.1+0.2≠0.3) — so store whole cents; needed re-grounding once |
| Basis points (finance origin) | 🔶 refresh | 1bp = 0.01%; bond-trader word, borrowed by code to avoid decimals |
| **The sanity check** | 🔶 refresh | Convert back to real world ("$40 tax on $50? no") — same muscle as checking AI commands |
| applyTax exercise | ✅ done | Completed 2026-07-06: 400¢ and 65¢ — first production code read + predicted |

## Networking & my own server
| Concept | Status | Hook |
|---|---|---|
| DNS diagnosis (ping-by-IP works, name fails) | ✅ solid | Demonstrated unaided 2026-07-06 |
| The four network settings (IP, subnet mask, gateway, DNS) | ✅ solid | Listed all four unaided 2026-07-08; gateway = "the door — internal traffic skips it, off-street traffic needs it" |
| Subnet mask (street name vs house number) | ✅ solid | Mask says which part of the IP is the street; same street → direct, different → gateway. Answered both /24 vs /16 checks unaided (2026-07-08) |
| DHCP / APIPA `169.254.x.x` | ✅ solid | Lease = ALL four settings; auto-renews at half-life. 169.254 + neighbors fine → broken path (cable/jack/switch port/NIC); many at once → the server (2026-07-08) |
| Windows net toolbelt (`ipconfig /release` `/renew` `/flushdns`, ping, nslookup, tracert) | 🔶 refresh | ~8 commands total, flags are English verbs of the story; typed release→renew unaided 2026-07-08 after one miss (said "ifconfig") |
| DNS cache / `ipconfig /flushdns` | 🔶 refresh | 2026-07-08: understood cached lookups get cleared; avoid calling it routing |
| 8.8.8.8 = Google · 1.1.1.1 = Cloudflare | 🔶 refresh | Got them backwards once — re-test |
| My own cert chain | 🔶 refresh | Who issues the cert for my domain and which process serves it. Must know my own claims cold. |
| Public hostname vs home IP | 🔶 refresh | The name people type is not the machine's home address |

## Web landscape (concepts, not tools yet)
| Concept | Status | Hook |
|---|---|---|
| CMS (WordPress / Squarespace / headless) | 🔶 refresh | Admin panel so non-coders edit content; local shops run on these. NOT for the learning workflow now — "learn in a weekend when a customer needs it." AI eats the low end (site generation); durable value = maintain/customize/fix (2026-07-14) |

## Dashboard backend (Python / FastAPI / ops) — encountered, not yet studied
Frontier concepts touched by shipped changes ahead of studying them. Gate A
verdict `over` (agent wrote it), so these are flagged to revisit; each maps to a
study-plan chunk. 🔵 = seen in a PR, never taught.
| Concept | Status | Hook |
|---|---|---|
| Host collectors (file-as-interface, "didn't run" vs "empty") | 🔵 open | A root timer writes data/*.json; the read-only app only reads it. Must distinguish no-findings from didn't-run. ground-up chunk 8. [revisit:0830] [revisit:0901] |
| FastAPI read-only request path | 🔵 open | route → `Depends(require_auth)` → read a file → return JSON. ground-up chunk 4. [revisit:0830] [revisit:0901] |
| The action broker (app→host privileged path) | 🔵 open | App has no sudo; a separate host process runs a fixed command list. ground-up chunk 5. [revisit:0830] |
| admin-v3 view wiring (showView / load / render) | 🔵 open | nav `data-view` → showView → per-view loader → render from the endpoint. ground-up chunk 11. [revisit:0830] [revisit:0901] |
| DOM keyboard events (keydown listener + key lookup table) | 🔵 open | One `document.addEventListener('keydown')` catches every keypress after it bubbles; a `{key: view}` table maps it. Odin JS item 6; ground-up chunk 11. PR dashboard#113. [revisit:0904] |
| event.target guards (don't fire while typing) | 🔵 open | The event says where the keystroke landed; if it's an input/textarea, the binding stands down. ground-up chunk 11. PR dashboard#113. [revisit:0904] |
| `element.click()` reuses the real click path | 🔵 open | Synthetic click fires the same handlers/target=_blank as a mouse click — why key 1–9 inherits each Priority link's settings free. ground-up chunk 11. PR dashboard#113. [revisit:0904] |
| Cross-origin fetch + CORS allowlist | 🔵 open | The browser blocks a response unless the OTHER server's `access-control-allow-origin` names this page's origin; nothing on the calling side can grant it. tokdash drop-in for the dashboard Limits panel. ground-up chunk 11. PR dashboard#114. [revisit:0905] |
| Grid/flex `min-width:auto` (content widens a 1fr track) | 🔵 open | An item is never narrower than its content by default, so one unwrappable string grew a column; `min-width:0` opts out. ground-up chunk 11. PR dashboard#114. [revisit:0905] |
| Function contracts (`ago()` wanted a timestamp) | 🔵 open | Handed a duration instead → "20701d ago". Read the parameter's meaning from the signature, don't guess. ground-up chunk 11. PR dashboard#114. [revisit:0905] |

## Not yet started (queue)
CLI drills (daily reps — none logged yet) · Odin Foundations (not started;
start immediately)
