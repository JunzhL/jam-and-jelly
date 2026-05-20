# Jam & Jelly — repository context for Claude Code

This repository holds the band "Jam & Jelly"'s working materials: sheet music, reference
audio, written/arranged parts, and practice notes.

## Who you are talking to
The people using this repo are **musicians, not programmers**. Most have never used Git,
a terminal, or GitHub. When you help them:
- Explain what you are about to do in plain, friendly language **before** doing it.
- Never show raw Git errors without translating them into plain English.
- Never assume they know terms like "branch", "commit", "remote", "stash". Briefly say
  what each means the first time it comes up.
- Confirm before anything destructive or hard to undo.

## Folder layout
- `scores/` — sheet music (PDF, image scans)
- `audio/` — reference recordings, backing tracks
- `parts/` — written or arranged parts (per song / per instrument)
- `practice-notes/` — markdown notes
- `docs/` — guides for the band
- `.claude/` — these helper skills and context (do not put music files here)

## Hard rules
- **Never commit directly to `main`.** All changes go onto a new branch and reach `main`
  only through a pull request. `main` is branch-protected on GitHub.
- **Never force-push** (`git push --force`), and never `git reset --hard` on work that
  isn't yours without explicit confirmation.
- Use the skills in `.claude/skills/` for the four core jobs: saving changes
  (`commit-on-branch`), proposing them (`open-pr`), accepting them (`review-merge`), and
  getting the latest (`pull-updates`).
- Keep commit messages and PR descriptions about *the music* ("Add bass part for Afro
  Blue"), not about Git mechanics.

## Conventions
- Branch names: short, kebab-case, descriptive — e.g. `add-really-love-horn-chart`,
  `fix-spanish-joint-typo`.
- Pull requests are squash-merged so `main` keeps one tidy commit per change.
- Default branch is `main`.
