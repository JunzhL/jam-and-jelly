# 💬 Band Guide — using Jam & Jelly in Slack

Welcome! This is **everything you need to know** to use the band's shared files and
task board. You don't need GitHub, Git, or any app beyond **Slack on your phone or
laptop**.

Everything happens in one channel: **`#all-jam-and-jelly`** in our Slack workspace.

---

## ⚡ The five-minute starter

Once you're in the Slack channel, here's literally everything you'll ever do:

| You want to… | What you do |
|--------------|-------------|
| **Add a music file** (PDF score, audio clip, written part, note) | Drop it into the channel with a short caption |
| **Approve someone's change** so it joins the shared copy | Click the **✅ Approve & Merge** button on their notification |
| **Reject** if a change isn't right | Click **❌ Reject** |
| **Add a task to the board** ("find horn chart for Really Love") | Hover any message → `⋯` → **Create issue in Linear** |
| **Ask the bot anything** | Type `@jar <your question>` |

That's the whole workflow. Everything else below is just detail on each of these.

---

## 📎 Adding a music file

### Step by step

1. In `#all-jam-and-jelly`, click the **`+`** (or paperclip) next to the message box.
2. Pick a file from your computer/phone. **Keep it under 2 MB** — the bot can't
   handle bigger files in Slack. (See the *"What if my file is too big?"* tip below.)
3. In the **caption** box, type a short description, e.g.
   *"bass part for Afro Blue, second verse"*.
4. Send.

### What you'll see back

Within ~5 seconds the bot replies in the channel:

> 🤖 **Jar** — *Got it — `<your filename>` committed to `<folder>/`. PR #N is open for review.*

Followed a second later by the *"new change proposed"* card with buttons. **You don't
need to click anything yourself** — anyone in the band can approve.

### Where files end up automatically

The bot looks at the file type and files it for you:

| File kind | Goes into folder |
|-----------|------------------|
| PDF, PNG, JPG, GIF (sheet music / scans) | `scores/` |
| MP3, WAV, M4A, FLAC, OGG (recordings) | `audio/` |
| `.md`, `.txt` (notes) | `practice-notes/` |
| Everything else | `parts/` |

### What if my file is too big?

The bot will reply telling you it's too large. Use the [laptop guide](BAND-GUIDE.md)
instead — it has no size limit. Most score PDFs and short audio clips fit fine.

---

## ✅ Approving or rejecting changes

When someone (you or another member) proposes a change, the bot posts a card in the
channel:

> 🎵 **New change proposed — PR #5**
> *Add bass part for Afro Blue*
> *Add bass part for Afro Blue, second verse. Uploaded from Slack.*
> Opened by **JunzhL**. Anyone can approve.
> &nbsp;&nbsp;&nbsp; **[ ✅ Approve & Merge ]** &nbsp; **[ ❌ Reject ]** &nbsp; [ View on GitHub ]

### Rules of thumb

- **Anyone in the channel** can click. Both buttons take effect immediately.
- **Approve & Merge** adds the change to the shared copy that everyone sees.
- **Reject** sends it back. The opener can fix and try again.
- If you're not sure, click **View on GitHub** to look at the file first.
- Take your time — **nothing reaches the shared copy until someone approves**.

### What you'll see after clicking

- ✅ Approve → the message updates to *"PR #N merged to main by @you. Everyone can now
  ask the bot to pull the latest."*
- ❌ Reject → the message updates to *"PR #N was rejected by @you and has been closed."*

---

## 📋 Adding a task to the board

Tasks live in **Linear** (free, polished mobile app). Two ways to create one:

### Easiest — from any Slack message

Hover over any message → click **`⋯`** (More actions) → **Create issue in Linear**.
A small form pops up: title, assignee, optional details. Hit *Create* and you're done.
You'll get a confirmation in the channel.

### Or — ask the bot

> `@jar add a task: find the horn chart for Really Love, assign to Sam`

The bot creates the Linear issue and replies with a link.

### Where the tasks live

- Mobile / desktop: **Linear app** (free — install once, log in)
- Web: <https://linear.app>
- Notifications when something happens (created, assigned, completed) → automatically
  posted to `#all-jam-and-jelly`.

---

## 🗨️ Asking `@jar` quick questions

Useful for:

> `@jar what songs do we have scores for?`
> `@jar what changes are waiting for approval?`
> `@jar what's still to do?`
> `@jar tell me about Spanish Joint`

Phrase it like you'd ask a person. The bot replies in the thread within ~30 seconds.

> **Note:** these conversational questions need an active Claude paid plan. If the
> band's Claude plan lapses to Free, `@jar` will tell you *"chat is offline"* — see
> the bottom of this guide for the manual alternatives. **Everything else (file
> uploads, approvals, tasks, notifications) keeps working regardless.**

---

## 🔔 What notifications you'll see (and when)

| When this happens… | The channel gets a message |
|---------------------|----------------------------|
| Someone proposes a change (PR opened) | 🎵 *"New change proposed — PR #N"* with Approve / Reject buttons |
| A change is merged into the shared copy | 🤖 *Bot posts a commit announcement* ("JunzhL pushed 1 commit to main: …") |
| A change is **closed without merging** (anywhere — Slack button, GitHub) | 🚫 *"PR #N closed without merging"* |
| A new Linear task is created | 🗒️ *Linear posts the task title + assignee + status* |
| A Linear task changes status (started, completed, etc.) | 🗒️ *Linear posts the update* |
| Someone uploads a file in Slack | 🤖 *"Got it — `<filename>` committed to `<folder>/`."* + the PR notification |
| A new GitHub issue is filed | 🐛 *"Issue opened: …"* |

> If you want fewer notifications, you can mute specific message threads in Slack
> instead of leaving the channel — long-press the message → *Mute thread*.

---

## 🆘 Common questions

**"Can I break something by clicking the wrong button?"**
No. Every change is reversible (we keep history), and the shared copy is protected —
nothing reaches it without an explicit approval click.

**"Can I edit a file someone else just added?"**
Yes — open it on GitHub (the **View on GitHub** link), download it, make changes, and
upload your new version in Slack with a caption like *"updated Afro Blue bass — fixed
typo in bar 12"*. The bot will open a new proposal.

**"What if I want to add a file from my computer's folder, not Slack?"**
That's the *laptop guide* path — see [BAND-GUIDE.md](BAND-GUIDE.md). Best for files
over 2 MB or when you have many files at once.

**"Where do I see all the files?"**
- Web: <https://github.com/JunzhL/jam-and-jelly>
- Folders are at the top — `scores/`, `audio/`, `parts/`, `practice-notes/`.
- Click any file to view it directly in the browser.

**"Where do I see all the tasks?"**
- Mobile: Linear app — the cleanest view.
- Web: <https://linear.app> — same data.

**"The bot didn't reply to me. What now?"**
- Wait ~30 seconds — `@jar` chat sometimes takes a moment.
- If still nothing, see the *Chat is offline* section below.
- For file uploads, you should get a reply in ~5 seconds — if you don't, just try
  uploading again with a slightly different caption.

---

## 🌙 If `@jar` says "chat is offline"

The conversational `@jar` features need an active Claude paid plan. If that's
lapsed to Free, `@jar` will reply with a message like *"My chat brain is offline
right now…"* and a list of alternatives. **Everything else keeps working:**

| Want to… | Do this instead |
|----------|-----------------|
| Add a file | Just attach it in the channel — uploads always work. |
| Approve / reject a change | Use the buttons on the PR notification — always works. |
| Create a task | Hover any message → `⋯` → **Create issue in Linear**. |
| See what's open / what's to do | Open the **Linear app** (tasks) or scroll the channel (PRs and commit notifications are all there). |
| Read / edit a file | Open the **View on GitHub** link from any notification. |
| Anything more complex | Use the [laptop guide](BAND-GUIDE.md). |

The button-driven workflow + native notifications form a complete loop on their own —
the bot is just a nice-to-have layer on top.

---

## ✏️ Tips for caption text

The caption you add when uploading a file becomes the change description that everyone
sees in the approval card and on GitHub. Good captions:

- *"bass part for Afro Blue, second verse"*
- *"Spanish Joint guitar — corrected chord in bar 24"*
- *"rough rehearsal recording from May 28"*

Less helpful:

- *"final"* (final of what?)
- *"updated"* (what changed?)
- *no caption* (everyone wonders what this is)

A short, specific caption saves the band time when reviewing.

---

Welcome aboard! 🎺 If anything in here is unclear, ask in `#all-jam-and-jelly` and
someone (or the bot, when chat is alive) will help.
