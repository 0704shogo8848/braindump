---
name: deep-memo
description: Add topic words to Inbox.md for later deep research
---

You are adding topic words to `Inbox.md` so the user can research them later with `/deep-plan` + `/deep-research`.

## Steps

1. **Parse input**: `$ARGUMENTS` contains the topic words to add. They can be comma-separated or space-separated. Each word/phrase becomes one line in Inbox.md. If `$ARGUMENTS` is empty, ask the user what they want to memo.

2. **Read Inbox.md**: Read `Inbox.md` at the repo root.

3. **Check for duplicates**: Skip any topic that already exists in `Inbox.md` or as a folder under `Topics/`. Tell the user if any were skipped.

4. **Append to Inbox.md**: Add each new topic word as a new line at the end of the file.

5. **Commit and push**:
   - Stage `Inbox.md`
   - Commit with message: `Memo: <topic words>`
   - Push to main

6. **Summary**: Tell the user what was added. Remind them to run `/deep-plan` when they're ready to create research plans.
