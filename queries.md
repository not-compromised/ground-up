# queries.md — counting the learning ledger

Every number about learning progress comes from `learning-log.md` by grep. There is no
database, no rendered page, and no second copy: a count is derived on the spot, so it
can be wrong only if the ledger is wrong.

Run from the ledger repo root.

## The tags

Tags append to a row's Hook cell and are never rewritten.

```
| `export` | 🔶 refresh | "Let other files use this" [skip:0830] [skip:0907] |
```

| Tag | Meaning |
|---|---|
| `[applied:<repo> MMDD]` | used unaided in another repo — the transfer test |
| `[skip:MMDD]` | a gate stop was declined |
| `[revisit:MMDD]` | the agent wrote it; flagged to come back |

`MMDD` is enough — the ledger's own timeline supplies the year.

## Session-open line

The `ground-up` skill runs these at session start and reports one line. Report it even
when every count is zero; a silent counter reads the same as one that never ran.

```bash
# totals
grep -o '\[skip:'    learning-log.md | wc -l
grep -o '\[revisit:' learning-log.md | wc -l
grep -o '\[applied:' learning-log.md | wc -l

# oldest unresolved tag
grep -oE '\[(skip|revisit):[0-9]+\]' learning-log.md | sort -t: -k2 | head -1
```

## Rows that have earned a session

Three tags of any kind on one row is the escalation line.

```bash
grep -E '(\[(skip|revisit):[0-9]+\][^|]*){3,}' learning-log.md
```

## What is blocking, most-dodged first

```bash
grep -E '\[(skip|revisit):' learning-log.md \
  | awk -F'|' '{n=gsub(/\[(skip|revisit):/,""); print n, $2}' \
  | sort -rn
```

## Drift check

If skips outnumber the open chunks in the repo's `ground-up.md`, the gates are being
declined faster than the work is being done. That is the single signal this counter
exists to surface — say it out loud when it trips.

```bash
skips=$(grep -o '\[skip:' learning-log.md | wc -l)
chunks=$(grep -c '^- \[ \]' plans/<repo>.md)
[ "$skips" -gt "$chunks" ] && echo "DRIFT: $skips skips vs $chunks open chunks"
```

(Point the second grep at wherever the repo's study plan actually lives, if yours
are not in `plans/`.)

## Rules that keep the counts honest

- **Append, never rewrite.** A tally that is edited in place can be dropped to zero or
  double-counted; a row of appended tags cannot.
- **A tag must name a concept row.** A skip that names no concept is not recorded, and
  a stop that could not name one should not have fired.
- **Never count tags out of PRs.** A PR's `revisit after <topics>` note is a message and
  dies with the PR. If the ledger row was not written, the tag did not happen.
- **No `|` inside a tag.** These live in markdown table cells.
