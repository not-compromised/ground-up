# Ledger

One row is one standing rule I stated cold: unaided, no app open, passing
all three checks in [MODEL.md](MODEL.md) (one sentence, what breaks if
false, where it is enforced or that it is not yet). Rule zero: only
unaided answers are evidence; a rule I could say only after an agent
explained it goes under re-test, not here. `held` is the date I first
stated it unaided. Tags append to the tags cell, newest last, never
rewritten: `[applied:<repo> MMDD]` when I used the rule unaided in
another repo, `[partial:MMDD]` and `[gap:MMDD]` for a re-test that fell
short. Counting recipes: [queries.md](queries.md). `root` rows are the
general truths every app obeys; the rest belong to one repo and match a
row in its `INVARIANTS.md`.

Seven rows start here from the first pass. The failed-write rule, which
came right only after teaching, waits under re-test.

| repo | rule | held | tags |
|---|---|---|---|
| finance | A bill is paid once per cycle. | 2026-09-25 | |
| finance | Cash on hand is your checking and savings balances plus money moving between your own accounts, and nothing else. | 2026-09-25 | |
| finance | Card and loan balances are debts: they subtract from net worth and never count as spendable cash. | 2026-09-25 | |
| finance | Transfers between your own accounts never count as spending or income. | 2026-09-25 | |
| finance | A refund lowers spending in the category it came from and never counts as income. | 2026-09-25 | |
| finance | Moving money between two of your own spendable accounts isn't spending, but paying a card always counts as money leaving. | 2026-09-25 | |
| root | Money is stored as integers and divided only at display. The finance app does not comply yet. | 2026-09-25 | |

## Partial and gap, re-test

A row here moves to the table above, tags and all, on the day I pass it
unaided.

| repo | rule | held | tags | note |
|---|---|---|---|---|
| root | A failed write leaves nothing behind. | | [partial:0925] | Reasoned to a resume-from-140 model before the all-or-nothing picture; answered the follow-up correctly after teaching, so not yet unaided. |
| finance | A pending charge is never proof a bill was paid. | | [partial:0925] | Had the visible behavior, not the rule. |
| finance | Recognizing a repeated bug as a class rather than a new bug. | | [gap:0925] | Did not recognize a second same-merchant posting in one cycle as the recurring class. |

## Born from the owner

Rules I added that no code or doc held before I said them.

| repo | rule | enforced by | date |
|---|---|---|---|
| finance | An in-transit amount that never lands within its window is flagged, not silently dropped. | not yet | 2026-09-25 |
| finance | Unlinking a bank never destroys its transaction history. | not yet, issue filed | 2026-09-25 |
