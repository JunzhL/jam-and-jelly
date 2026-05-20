---
name: review-merge
description: Review open pull requests and merge an approved one into the main branch. Use when someone wants to see what changes are waiting, or to approve and finalise a proposed change. Shows each PR in plain language before merging.
---

# Review and merge a pull request

This skill lets a person see what changes are waiting and finalise (merge) an approved one
into the shared `main` copy.

## Steps

1. **Confirm `gh` is ready.** Run `gh auth status`. If not installed/logged in, explain
   plainly and stop.

2. **List what's waiting.**
   - Run `gh pr list --state open`.
   - For each open PR, show the person a plain summary: number, title, who opened it, and
     the first lines of the description (`gh pr view <num>`).
   - If there are none, say so and stop.

3. **Let the person choose** which PR to act on, or confirm the one they named.

4. **Optionally show the details** of that PR's changes: `gh pr diff <num> --stat`.

5. **Merge when approved.** Confirm with the person first ("This will add the change to
   the shared copy that everyone uses — go ahead?"), then:
   `gh pr merge <num> --squash --delete-branch`

6. **Report the result**, e.g.:
   > Merged! *"Add bass part for Afro Blue"* is now part of the shared copy. Everyone can
   > get it by asking me to "pull the latest".

## Notes
- Squash-merge keeps `main` tidy (one commit per change).
- `--delete-branch` cleans up the finished branch automatically.
- In the Slack workflow, merge approval happens via the Approve button in the chat; this
  local skill is for you (the repo owner) doing it from your laptop.
- To reject instead of merge: `gh pr close <num>` and explain why to the opener.
