---
name: open-pr
description: Create a GitHub pull request for the current branch so the band can review a change before it goes into the shared main copy. Generates a plain-language title and description and lets the person edit them before submitting. Use after changes have been committed on a branch.
---

# Open a pull request

A pull request ("PR") is how a change gets proposed for the shared `main` copy. This skill
creates one for the branch the person is currently on.

## Steps

1. **Check the branch.**
   - Run `git branch --show-current`. If it is `main`, stop and explain: changes must be
     on their own branch first — offer to run the `commit-on-branch` skill.
   - Make sure the branch is pushed: `git push -u origin <branch>` if needed.

2. **Confirm `gh` is ready.** Run `gh auth status`. If `gh` is not installed or not
   logged in, tell the person plainly and stop (this is a one-time setup step).

3. **Draft the PR.**
   - Title: short, about the music — e.g. `Add bass part for Afro Blue`.
   - Description: a few friendly bullet points — what changed, which song(s), which files,
     and anything the band should check. Look at `git diff main...<branch> --stat` to be
     accurate.

4. **Show the draft to the person and let them edit** the title or description before
   anything is submitted.

5. **Create the PR:**
   `gh pr create --base main --head <branch> --title "<title>" --body "<description>"`

6. **Report the result** with the PR link, e.g.:
   > Done — your change is now proposed as Pull Request #4. The band will get a
   > notification and can approve it. Here's the link: <url>

## Rules
- Always target `main` as the base branch.
- Never merge here — that is the `review-merge` skill's job.
