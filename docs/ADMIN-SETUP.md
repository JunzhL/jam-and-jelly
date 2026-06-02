# 🔧 Admin Setup Guide

One-time setup for the band organiser. Connects GitHub, Slack, Linear, and the bot.
Everything here uses **free tiers** — total ongoing cost is $0 beyond a Claude Code
subscription. Work through it top to bottom; later steps reuse values from earlier ones.

Keep a scratch note as you go — you'll collect ~9 secret values. **Never commit them to
Git.** They go into Cloudflare Worker secrets only.

---

## Part 1 — GitHub

### 1.1 Repository
Already done: <https://github.com/JunzhL/jam-and-jelly> (public, `main` branch).

### 1.2 Branch protection (`main`)
Go to **Settings → Branches → Add branch ruleset** (or classic rule).
- Target branch: `main`
- Enable **Require a pull request before merging**
- Required approvals: **0** (the approval gate is the Slack button, not GitHub reviews)
- Save.

This blocks anyone from pushing straight to `main`; all changes go through a PR.

### 1.3 Fine-grained Personal Access Token (for the bot)
**Settings → Developer settings → Personal access tokens → Fine-grained tokens →
Generate new token.**
- Name: `jam-and-jelly-bot`
- Resource owner: your account
- Repository access: **Only select repositories → `jam-and-jelly`**
- Repository permissions:
  - **Contents** → Read and write
  - **Pull requests** → Read and write
- Generate, copy the token. ➜ save as **`GITHUB_TOKEN`**

### 1.4 GitHub → Slack notifications (native, no code)
Do this *after* Slack exists (Part 2). In the Slack channel, run:
```
/github subscribe JunzhL/jam-and-jelly issues commits
```
(We deliberately leave `pulls` to our own bot, which posts PRs *with* Approve buttons —
see Part 5. Subscribing to `pulls` here too would just double the notifications.)

---

## Part 2 — Slack

### 2.1 Workspace & channel
- Create a free Slack workspace (or use an existing one) at <https://slack.com/get-started>.
- Use the workspace-wide channel Slack auto-creates: `#all-<workspace-name>`
  (for "Jam & Jelly" → `#all-jam-and-jelly`). Invite the band to the workspace; they're
  added to this channel automatically. (Or create a dedicated channel and use that
  instead — the bot only cares about the channel ID, not the name.)

### 2.2 Create the bot's Slack app
Go to <https://api.slack.com/apps> → **Create New App → From scratch**.
- Name: `jar`, pick the workspace.
- **OAuth & Permissions → Bot Token Scopes**, add:
  `chat:write`, `app_mentions:read`, `files:read`, `channels:history`,
  `channels:read`, `commands`
- **Install to Workspace.** Copy the **Bot User OAuth Token** (`xoxb-…`).
  ➜ save as **`SLACK_BOT_TOKEN`**
- **Basic Information → App Credentials:** copy the **Signing Secret**.
  ➜ save as **`SLACK_SIGNING_SECRET`**
- Invite the bot to the channel: in `#all-jam-and-jelly`, type `/invite @jar`.
- Get the channel ID: open the channel → click its name → bottom of the dialog shows an
  ID like `C0123ABCD`. ➜ save as **`SLACK_CHANNEL_ID`**

> The Event and Interactivity **Request URLs** are filled in later (Part 4.3), once the
> Worker is deployed and has a URL.

---

## Part 3 — Linear

- Create a free workspace at <https://linear.app>.
- Create one team, e.g. `Jam & Jelly` (key `JAM`).
- Invite the band (free tier = unlimited members).
- **Settings → Integrations → Slack → Connect.** Choose `#all-jam-and-jelly` for
  notifications. This is free and needs no code; it also enables "Create issue in Linear"
  from any Slack message (hover a message → `⋯` → *Create issue*).
- Settings → API → **Personal API key** → create one. ➜ save as **`LINEAR_API_KEY`**
  (used later by the Claude Routine for the task digest).

> Free tier caps at **250 active issues** — archive finished tasks periodically.

---

## Part 4 — Cloudflare Worker (the bot)

The bot source lives in the `jam-and-jelly-bot` folder/repo. It is a thin dispatcher —
no AI runs in it.

### 4.1 Cloudflare account
- Sign up free at <https://dash.cloudflare.com/sign-up>.
- Install the CLI and log in (in the `jam-and-jelly-bot` folder):
  ```
  npm install
  npx wrangler login
  ```

### 4.2 Deploy
```
npx wrangler deploy
```
This prints the Worker URL, e.g. `https://jam-and-jelly-bot.<subdomain>.workers.dev`.
➜ note it as **`WORKER_URL`**.

### 4.3 Point Slack at the Worker
Back in the Slack app config (<https://api.slack.com/apps>):
- **Event Subscriptions** → enable → Request URL: `WORKER_URL/slack/events`
  (Slack verifies it instantly; the Worker answers the challenge.)
  Under **Subscribe to bot events** add: `app_mention`, `file_shared`.
- **Interactivity & Shortcuts** → enable → Request URL: `WORKER_URL/slack/interactivity`
- Save. Reinstall the app if Slack asks.

### 4.4 Set the Worker secrets
Run each command and paste the value when prompted:
```
npx wrangler secret put SLACK_SIGNING_SECRET
npx wrangler secret put SLACK_BOT_TOKEN
npx wrangler secret put GITHUB_TOKEN
npx wrangler secret put GITHUB_WEBHOOK_SECRET   # invent any random string; reuse in 4.5
npx wrangler secret put ROUTINE_URL             # from Part 6
npx wrangler secret put ROUTINE_TOKEN           # from Part 6
```
Non-secret config (`GITHUB_OWNER`, `GITHUB_REPO`, `SLACK_CHANNEL_ID`) is already in
`wrangler.jsonc` — confirm `SLACK_CHANNEL_ID` there matches Part 2.2.

### 4.5 GitHub webhook → Worker (PR notifications with buttons)
In the `jam-and-jelly` repo: **Settings → Webhooks → Add webhook.**
- Payload URL: `WORKER_URL/github/webhook`
- Content type: `application/json`
- Secret: the same random string you used for `GITHUB_WEBHOOK_SECRET` in 4.4
- Events: **Let me select individual events → Pull requests** only
- Add webhook.

Now whenever a PR opens, the Worker posts it to Slack with **Approve / Reject** buttons.

---

## Part 5 — How the pieces talk

```
PR opened ─▶ GitHub webhook ─▶ Worker ─▶ Slack message + [Approve][Reject]
Approve clicked ─▶ Worker ─▶ GitHub merge API ─▶ Slack message replaced with ✅
Reject clicked ─▶ Worker ─▶ GitHub close API ─▶ Slack message replaced with ❌
PR closed (no merge) on GitHub web ─▶ webhook ─▶ Worker ─▶ Slack 🚫 notification
PR merged ─▶ webhook + commits subscription ─▶ GitHub Slack app announces the commit
File uploaded in Slack ─▶ Worker (no Routine!) ─▶ GitHub commit + PR ─▶ Slack
@jar message ─▶ Worker ─▶ Claude Routine ─▶ replies in Slack thread
                              └ on 401/403 ─▶ Worker posts "chat is offline" fallback
Linear issue created / changed ─▶ Linear's native Slack integration
GitHub issue opened / closed ─▶ GitHub's native Slack app
```

### Notification matrix (which path delivers each notification)

| Event | Delivered by | Survives Claude Free? |
|-------|--------------|------------------------|
| PR opened (with action buttons) | Worker | ✅ |
| PR merged → commit announced on main | GitHub Slack app (`/github subscribe ... commits`) | ✅ |
| PR closed via Slack button | Worker (replaces the original PR message) | ✅ |
| PR closed-without-merge on GitHub web | Worker (`pull_request.closed` handler) | ✅ |
| File-upload confirmation | Worker | ✅ |
| GitHub issue opened/closed/labeled | GitHub Slack app (`/github subscribe ... issues`) | ✅ |
| Linear issue created / status change / assigned | Linear's native Slack integration | ✅ |
| `@jar` chat reply | Claude Routine | ❌ (Worker posts polite "chat is offline" fallback) |

**Only `@jar` chat depends on Claude.** Everything else is delivered by the Worker or
by free native integrations that keep working on any plan.

---

## Part 6 — Claude Code Routines (the "brain", free on your subscription)

Create at <https://claude.ai/code/routines> (or run `/schedule` in Claude Code).

### 6.1 Request-handler routine
- **Trigger:** API (gives you a URL + bearer token).
  ➜ save the URL as **`ROUTINE_URL`** and the token as **`ROUTINE_TOKEN`** (used in 4.4).
- **Connected tools (MCP):** GitHub, Slack, Linear.
- **Instructions (paste this in):**
  > You receive a JSON payload from the Jam & Jelly Slack bot. Fields: `type`
  > (`"chat"` or `"file"`), `channel`, `thread_ts`, `user`, and either `text` or
  > `file_url` + `file_name` + `caption`.
  > - If `type` is `"file"`: download the file, commit it to a new branch in the
  >   `JunzhL/jam-and-jelly` repo under the right folder (`scores/`, `audio/`,
  >   `parts/`, `practice-notes/`), open a pull request describing it, and reply in the
  >   Slack thread with the PR link.
  > - If `type` is `"chat"`: interpret the band member's request (pull status, create a
  >   Linear task, summarise open work, etc.), do it via the connected tools, and reply
  >   in the Slack thread in plain, friendly language.
  > Never commit directly to `main`. Keep replies short and jargon-free.

### 6.2 Daily task digest routine (optional)
- **Trigger:** Schedule — daily, e.g. 09:00.
- **Connected tools:** Linear, Slack.
- **Instructions:**
  > List the open (non-done) issues in the Linear `Jam & Jelly` team. Post a short
  > "🎵 Still to do" summary to the `#all-jam-and-jelly` Slack channel with a link to Linear.
  > If nothing is open, post a cheerful "all caught up" note.

---

## Secrets checklist

| Value | From | Used in |
|-------|------|---------|
| `GITHUB_TOKEN` | Part 1.3 | Worker secret |
| `SLACK_SIGNING_SECRET` | Part 2.2 | Worker secret |
| `SLACK_BOT_TOKEN` | Part 2.2 | Worker secret |
| `SLACK_CHANNEL_ID` | Part 2.2 | `wrangler.jsonc` |
| `GITHUB_WEBHOOK_SECRET` | invented, Part 4.4 | Worker secret + GitHub webhook |
| `ROUTINE_URL` / `ROUTINE_TOKEN` | Part 6.1 | Worker secret |
| `LINEAR_API_KEY` | Part 3 | Linear routine (stored in Claude, not the Worker) |

---

## Part 7 — First-run test checklist

Run these once after setup. Use `npx wrangler tail` in the bot folder to watch the Worker
live while testing.

- [ ] **Worker is up:** open `WORKER_URL/health` in a browser → shows `jam-and-jelly-bot: ok`.
- [ ] **Slack URLs verified:** the Event and Interactivity Request URLs in the Slack app
      config show a green "Verified".
- [ ] **PR notification:** open a test PR in the `jam-and-jelly` repo (any small change on
      a branch) → within seconds a message with **Approve / Reject** buttons appears in
      `#all-jam-and-jelly`.
- [ ] **Approve works:** click **Approve & Merge** → the PR squash-merges on GitHub and the
      Slack message updates to "✅ merged".
- [ ] **Reject works:** open another test PR → click **Reject** → the PR closes on GitHub
      and the message updates to "❌ rejected".
- [ ] **File upload:** drop a small PDF into `#all-jam-and-jelly` with a caption → the Routine
      commits it and replies with a PR link.
- [ ] **Free-form chat:** `@jar what files do we have?` → a sensible reply.
- [ ] **Task creation:** `@jar add a task: test task` → a new Linear issue,
      and a Slack notification from the Linear integration.
- [ ] **Digest (if enabled):** run the digest routine once from `claude.ai/code/routines`
      → a "🎵 Still to do" summary posts.

If a step fails, `wrangler tail` shows the Worker's logs; signature errors mean a secret
is wrong or a Request URL points to the wrong path.

Done — hand the band [`CHAT-GUIDE.md`](CHAT-GUIDE.md) and you're live. 🎶
