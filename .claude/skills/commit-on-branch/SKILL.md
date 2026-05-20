---
name: commit-on-branch
description: Save the band member's local file changes (added, modified, or removed music files) onto a new Git branch with a clear commit message. Use whenever someone says they have changed files and want to save or back up their work. Always reports the branch name and commit message in plain language.
---

# Commit on a new branch

Goal: take whatever the person has changed in the folder and safely save it onto a **new
branch**, never onto `main`. Then tell them the branch name and what was saved.

## Steps

1. **See what changed.**
   - Run `git status --short` and `git diff --stat`.
   - If there is nothing to save, tell them plainly ("There are no changes to save right
     now") and stop.

2. **Describe the changes to the person** in plain language — which files, which song,
   added vs edited vs removed. Do not show raw Git output.

3. **Pick a branch name.**
   - Short, lowercase, words joined by hyphens, describing the music change.
   - Examples: `add-afro-blue-bass-part`, `update-really-love-intro`, `remove-old-scan`.
   - Tell the person the name you chose.

4. **Create the branch and stage everything.**
   - If currently on `main`: `git checkout -b <branch-name>`.
   - If already on another branch: ask whether to keep adding to that branch or start a
     fresh one, then act accordingly.
   - `git add -A`

5. **Write a clear commit message** about the music, e.g. `Add bass part for Afro Blue`.
   Keep the first line under ~70 characters; add a short second paragraph only if helpful.
   - `git commit -m "<message>"`

6. **Back it up online.** If a GitHub remote (`origin`) exists:
   `git push -u origin <branch-name>`. If there is no remote yet, say the change is saved
   locally and will sync once the repo is connected to GitHub.

7. **Report to the person**, e.g.:
   > Saved! Your changes are on a branch called **add-afro-blue-bass-part**, with the
   > note *"Add bass part for Afro Blue"*. Next, if you'd like the band to review it,
   > ask me to "create a pull request".

## Rules
- Never commit to `main`.
- Never force-push.
- If files were deleted, confirm with the person before committing the deletion.
