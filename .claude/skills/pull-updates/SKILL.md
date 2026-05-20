---
name: pull-updates
description: Fetch the latest version of the music files from GitHub — either the shared main copy or a specific branch someone is working on. Use when a band member wants to get up to date or look at someone else's in-progress work. Safely handles unsaved local changes first.
---

# Pull the latest

This skill brings the person's local folder up to date with GitHub.

## Steps

1. **Check for unsaved local changes.**
   - Run `git status --short`.
   - If there are uncommitted changes, do **not** pull yet. Explain plainly and offer a
     choice:
     - Save them first with the `commit-on-branch` skill (recommended), or
     - Set them aside temporarily with `git stash` (offer to bring them back after).
   - Only continue once the working folder is clean.

2. **Decide what to pull.**
   - Default: the shared `main` copy.
   - If the person named a specific branch (e.g. "get Sam's horn-chart branch"), use that.

3. **Pull it.**
   - For `main`: `git checkout main` then `git pull origin main`.
   - For another branch: `git fetch origin` then
     `git checkout <branch>` and `git pull origin <branch>`.

4. **Tell the person what arrived.** Summarise the recent changes in plain language —
   `git log --oneline -5` and the files touched — focused on songs and parts, not Git.

5. If you stashed changes in step 1, offer to restore them with `git stash pop` and help
   resolve anything that conflicts.

## Rules
- Never discard the person's unsaved work without explicit confirmation.
- If a pull reports a conflict, explain it calmly in plain language and walk them through
  it one file at a time.
