---
name: learning-inbox
description: Capture something the user doesn't yet understand into the learning inbox to teach in a later session; capture only, never teach in the moment ("/learning-inbox", "inbox it", "learning item").
---

# Learning Inbox (capture now, learn later)

Mid-session the user hits something they don't understand. Stopping to teach it
derails the task; letting it pass loses it. This skill captures the moment as **one
file per item** in the ledger repo's `inbox/` (your global agent context names the
ledger's path), where future teaching sessions pick it up.

## What to do

1. **The argument is the item.** Whatever follows the invocation is what the user is
   caught up on, in their words. No argument → take the most recent point of confusion
   in the conversation; if that's genuinely ambiguous, ask one short question.
2. **Gather the context while you still have it.** The doc must let a future session
   reconstruct the moment without this session's transcript:
   - **Caught on:** what the user said they don't get, in their words.
   - **The artifact:** the verbatim code/command/error/output that triggered it, in a
     code fence, with file path / project / machine.
   - **What was happening:** one or two sentences on the task underway, and what the
     confusion blocked.
   - **Related ledger rows:** matching 🔶/🔵 concepts in the learning log, if any.
   - *(optional)* Suggested resolution: session type (code-coach / drill / tired-night
     track) or the external lesson that covers it.
   A bare restatement of the user's sentence is a failed capture — the surrounding
   context is the whole reason to write the file now instead of later.
3. **Write one file:** `inbox/YYYY-MM-DD-<slug>.md` (absolute date from `date +%F`,
   short topic slug). `mkdir -p` the folder if needed. **New file only. Never edit
   existing files, and run no git commands** — `inbox/` is gitignored because captures
   quote private code verbatim; the file lives on disk until a teaching session folds
   it (teach → tally → delete the file).
4. **Confirm in one line** — the filename plus a one-phrase restatement — then return
   to the interrupted task.

## Rules

- **Capture, don't teach.** Explanation of the concept waits for the teaching session
  (which also does the tally) unless the user explicitly asks for it right then. The
  learning log stays untouched by this skill; nothing has been taught yet.
- **One item per file.** Two confusions in one sentence → two files.
- Nothing in `inbox/` ever gets ✅ — these are questions, not accomplishments.
