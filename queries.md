# queries.md: counting the ledger

Every number comes from [ledger.md](ledger.md) by grep, run from this
repo's root. Each recipe reads table rows only (lines starting `|`). A count is derived on the spot, so it is wrong only if the
ledger is.

```bash
# held rows per repo (only the top table has a date in column 3)
awk -F'|' '$4 ~ /20[0-9][0-9]-/ {gsub(/ /,"",$2); n[$2]++}
  END {for (r in n) print n[r], r}' ledger.md

# rows waiting on a re-test
awk '/^## Partial/{p=1} /^## Born/{p=0} p && /\[(partial|gap):/' ledger.md

# rules used unaided in another repo: count, then the rows
grep '^|' ledger.md | grep -o '\[applied:' | wc -l
grep -E '^\|.*\[applied:' ledger.md

# rules I added that nothing enforces yet
awk -F'|' '/^## Born/{b=1} b && $4 ~ /not yet/' ledger.md
```

Report a zero as a zero; a silent count reads the same as one that never
ran.

## Drift check

The repos are private, so this is a procedure, not a script. For each
repo named in the ledger, open that repo's `INVARIANTS.md`:

1. Every held row here matches a row there, and its `held` date agrees.
2. Every "born from the owner" row here is a row there, and its
   enforced-by cell matches.
3. `root` rows match the roots list in your private context instead.

A row here with no match there is drift: the rule was dropped, reworded,
or never landed. Fix the repo's file or reword the ledger row, then say
which.
