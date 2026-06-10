# 🎶 Jam & Jelly — Full Band Guide

Welcome! This single document covers **everything you need to know** to contribute to
the band's shared music and tasks. It assumes you've never used Git, GitHub, Slack,
or Linear before. Pick whichever path fits how you like to work — they all feed into
the same shared copy.

> If you only ever read one section, read [§ 4 — The 5-minute starter](#-4--the-5-minute-starter).
> Everything else is just detail.

---

## Table of contents

1. [What this system is, and why](#-1--what-this-system-is-and-why)
2. [One-time setup](#-2--one-time-setup-5-10-minutes)
3. [The three paths to contribute](#-3--the-three-paths-to-contribute)
4. [The 5-minute starter](#-4--the-5-minute-starter)
5. [Path A — using Slack](#-5--path-a--using-slack-easiest-no-install)
6. [Path B — laptop with Claude Code](#-6--path-b--laptop-with-claude-code-plain-english)
7. [Path C — laptop with terminal `git`](#-7--path-c--laptop-with-terminal-git-most-control)
8. [Day-to-day workflow](#-8--day-to-day-workflow-examples)
9. [How Slack should be used](#-9--how-slack-should-be-used)
10. [How Linear should be used](#-10--how-linear-should-be-used)
11. [Common scenarios — step by step](#-11--common-scenarios--step-by-step)
12. [Notifications you'll see](#-12--what-notifications-youll-see)
13. [Troubleshooting & common questions](#-13--troubleshooting--common-questions)
14. [If `@jar` says "chat is offline"](#-14--if-jar-says-chat-is-offline)
15. [Quick reference card](#-15--quick-reference-card)

---

## 🪕 1 — What this system is, and why

We use four tools together to keep the band organised. None of them require
day-to-day technical skill. Here's what each does and why we use it.

| Tool | What it is | Why we use it |
|------|-----------|---------------|
| **GitHub** | A free service where the actual files live (PDFs, audio, written parts, notes). Think of it as a shared Dropbox **with a complete history of every change**. | So nothing is ever lost. Every version is recoverable forever. |
| **Slack** | A chat app on your phone and computer. | One place for all coordination — files, notifications, decisions, questions. |
| **Linear** | A free task board app on your phone and computer. | So we know who's doing what (find a chart, learn a part, bring gear). |
| **Jar** | The band's bot. Lives in Slack. | Does the heavy lifting — turning your file drops into proper changes, posting notifications, answering quick questions. |

**The key idea:** GitHub keeps the music safe and versioned. Slack is where you and
the band actually do things. Linear tracks tasks. Jar is the glue between them.

You'll mostly only touch Slack. The rest is invisible until you need it.

---

## 🛠️ 2 — One-time setup (5–10 minutes)

You only do these once. After this, you never touch them again until a new device.

### 2a. Join Slack *(required)*
1. The band organiser sends you a Slack invite link by email or text.
2. Click it, sign up with your email (free, no payment).
3. Install **Slack** on your phone (iOS / Android) and/or computer.
4. Open the channel **`#all-jam-and-jelly`** — this is where everything happens.

### 2b. Join Linear *(required if you'll do any task tracking)*
1. Band organiser sends you a Linear invite link.
2. Sign up (free).
3. Install the **Linear app** on your phone or use <https://linear.app> in a browser.

### 2c. Get a GitHub account *(optional — only for paths B and C below)*
1. Sign up free at <https://github.com>.
2. Send your GitHub username to the band organiser. They'll add you as a
   collaborator on `jam-and-jelly`.
3. You'll get a notification email — click **Accept invitation**.

### 2d. Install Claude Code *(optional — only for path B)*
1. Go to <https://claude.com/claude-code> and install for your operating system.
2. Sign in with your Claude account (Claude Free is enough for occasional use).

### 2e. Install Git + GitHub CLI *(optional — only for path C)*
- **Mac:** open Terminal and type `git --version`. If a popup asks to install
  developer tools, accept. Then `brew install gh`.
- **Windows:** download Git from <https://git-scm.com/download/win>, then install
  GitHub CLI from <https://cli.github.com>.
- **Linux:** `sudo apt install git gh` (or your distro's equivalent).

That's all the setup. Now to the actual workflow.

---

## 🛣️ 3 — The three paths to contribute

You can use **any combination** of these — pick what fits the task. All three end
up doing the same thing (proposing a change which the band then approves), they just
differ in *how* you make the change.

| Path | Install | Best for | How you "save" |
|------|---------|----------|-----------------|
| **A — Slack** | Nothing extra | Quick file drops, approving, tasks, questions | Drop file in channel |
| **B — Laptop + Claude Code** | Claude Code (free version OK) | Multi-file changes, when you want plain-English help | *"Claude, save my changes"* |
| **C — Laptop + terminal `git`** | Git + (recommended) `gh` CLI | If you already know git, or want full control | Real `git` commands |

Mix freely. You can drop one file in Slack today, work from your laptop tomorrow.

---

## ⚡ 4 — The 5-minute starter

Whatever path you choose, these five actions cover ~95% of what you'll ever do.

| You want to… | What you do |
|--------------|-------------|
| 1. **Add a music file** | Drop it into `#all-jam-and-jelly` in Slack with a caption *(or use path B/C — see §6 / §7)* |
| 2. **Approve a proposed change** | Click ✅ **Approve & Merge** on the bot's card |
| 3. **Reject a proposed change** | Click ❌ **Reject** on the card |
| 4. **Add a task** ("find horn chart for Really Love") | Hover any Slack message → `⋯` → **Create issue in Linear** *(or `@jar add a task: …`)* |
| 5. **Ask the bot something** | Type `@jar <question>` in the channel |

That's the whole loop. The rest of this guide is detail on each.

---

## 💬 5 — Path A — using Slack *(easiest, no install)*

Best for ~80% of band activity. Everything below happens entirely inside the
`#all-jam-and-jelly` channel.

### 5a. Adding a music file

1. In `#all-jam-and-jelly`, click the **`+`** / paperclip beside the message box.
2. Pick a file. **Important:** keep it under **2 MB** (PDFs and short clips are
   usually well under). Bigger? See § 6 or § 7.
3. In the **caption / message** field, write a short description.
   - Good: *"bass part for Afro Blue, second verse"*
   - Good: *"Spanish Joint guitar — corrected chord in bar 24"*
   - Bad: *"final"*, *"updated"*, or no caption (everyone wonders what it is).
4. Send.

#### What you'll see back

Within ~5 seconds, the bot replies in the channel:

> 🤖 **Jar** — *Got it — `afro-blue-bass.pdf` committed to `scores/`. PR #6 is open
> for review.*

A second later, a card appears:

> 🎵 **New change proposed — PR #6**
> *Add afro-blue-bass.pdf*
> *Adds afro-blue-bass.pdf in scores/. Uploaded from Slack.*
> Opened by **JunzhL**. Anyone can approve.
> &nbsp;&nbsp;&nbsp; **[ ✅ Approve & Merge ]** &nbsp; **[ ❌ Reject ]** &nbsp; [ View on GitHub ]

You don't have to click anything yourself — anyone in the band can approve.

#### Where files end up automatically

The bot picks the folder based on file type:

| File type | Folder |
|-----------|--------|
| PDF, PNG, JPG, GIF (sheet music / scans) | `scores/` |
| MP3, WAV, M4A, FLAC, OGG (recordings) | `audio/` |
| `.md`, `.txt` (notes) | `practice-notes/` |
| Anything else | `parts/` |

#### What if my file is too big?

The bot replies *"too big for me to handle in Slack — please use the laptop guide
instead."* See § 6 or § 7 for the laptop paths. No size limit there.

### 5b. Approving or rejecting a change

When anyone (you or another member) proposes a change, the bot posts the card
shown above. Rules of thumb:

- **Anyone** in the channel can click either button. The first click wins.
- Clicks take effect immediately. There's a confirm modal on Approve so accidental
  taps don't merge.
- **Nothing reaches the shared copy until someone approves.** Take your time — wait
  hours or days if the band needs to discuss.
- If unsure, click **View on GitHub** first and look at the actual file.
- **Reject** is reversible — the proposer can revise and try again.

#### What happens after a click

- ✅ Approve & Merge → the card updates to *"PR #6 merged to main by @you. Everyone
  can now ask the bot to pull the latest."* The change is now live in the shared
  copy.
- ❌ Reject → the card updates to *"PR #6 was rejected by @you and has been closed."*

### 5c. Adding a task to Linear from Slack

Two ways:

1. **From any message:** hover over it → `⋯` (More actions) → **Create issue in
   Linear** → fill in the short form → Create. Use this when someone said something
   in the channel that should become a task.

2. **Ask the bot:** `@jar add a task: find the horn chart for Really Love, assign to
   Sam`.

Either way, the issue appears in Linear and a notification appears in
`#all-jam-and-jelly`.

### 5d. Asking `@jar` questions

Phrase it like you'd ask a person:

> `@jar what's open?`
> `@jar what's still to do?`
> `@jar tell me what changed last week`
> `@jar what songs do we have scores for?`

The bot replies in the thread within ~30 seconds.

> **Note:** these conversational questions need an active Claude paid plan. If the
> band's plan is on Free, `@jar` will reply with *"chat is offline"* — see § 14 for
> what to do then. Every other Slack feature (file uploads, approvals, tasks,
> notifications) keeps working regardless.

---

## 💻 6 — Path B — laptop with Claude Code *(plain English)*

Use this when:
- The file you want to add is **over 2 MB** (rehearsal audio, big PDFs).
- You have **many files** to handle at once.
- You want help in plain English without learning Git.

You need: Claude Code installed (§ 2d), a GitHub account with access to the repo
(§ 2c).

### 6a. One-time: clone the repo

In Claude Code, in a new chat, type:

> *"Clone the Jam & Jelly repository to my computer."*

Claude will ask where to put it (e.g. `~/Documents/jam-and-jelly`) and set it up.
You'll have a normal folder where you can open, drag, and edit files like any
other.

### 6b. The four things you'll say to Claude

| You say (in Claude Code) | What happens |
|--------------------------|--------------|
| *"I've made some changes — please save them."* | Claude figures out what changed, makes a safely-named branch, writes a clear commit message, and pushes the branch up. You can't accidentally overwrite anyone else's work. |
| *"Create a pull request for my changes."* | Claude writes a plain-language description (you can edit it) and posts it. The band gets the approval card in Slack. |
| *"Show me the changes waiting for approval, then approve PR #5."* | Claude lists open PRs and finalises the one you picked. |
| *"Get me the latest version."* | Claude pulls the shared copy down. If you have unsaved work, it offers to save first so nothing is lost. |

### 6c. Tips for working this way

- **You can't break anything.** Every action is recoverable; the shared copy is
  protected.
- If Claude says something jargon-y, just say *"Explain that simply."*
- If you make a mistake, *"Undo what you just did"* usually works.
- After Claude opens a PR, the band sees it in Slack and approves as usual.

---

## 🧰 7 — Path C — laptop with terminal `git` *(most control)*

Use this when you already know `git`, or want raw control. If you've never opened
a terminal before, path B (Claude Code) is probably an easier first step. This
section assumes nothing else — every command is explained.

You need: Git installed (§ 2e), GitHub CLI (`gh`) installed (recommended).

### 7a. One-time setup

Open your **Terminal** (Mac: Spotlight → "Terminal"; Windows: "Terminal" from the
Start menu; Linux: your usual terminal).

```sh
# Tell git who you are (used in commit history)
git config --global user.name  "Your Name"
git config --global user.email "you@example.com"

# Log in to GitHub via the CLI -- this configures git's authentication too.
# It'll open a browser; click Allow.
gh auth login
# When prompted, pick: GitHub.com -> HTTPS -> Yes (authenticate git) -> browser
```

Now clone the repo (one time):

```sh
cd ~/Documents
git clone https://github.com/JunzhL/jam-and-jelly.git
cd jam-and-jelly
```

You now have `~/Documents/jam-and-jelly` with everyone's files inside.

### 7b. Glossary — what each command means

| Command | Plain English |
|---------|---------------|
| `git status` | Show me what's changed in my folder. |
| `git checkout <branch>` | Switch my folder to a specific version. |
| `git checkout -b <new-branch>` | Make a fresh side-version to work on. |
| `git pull` | Download the latest from GitHub. |
| `git add -A` | Mark all my changes as ready to save. |
| `git commit -m "..."` | Save a snapshot with this note. |
| `git push` | Upload my snapshots to GitHub. |
| `gh pr create` | Propose my work for the band to approve. |
| `git stash` | Set aside unsaved work without committing. |
| `git stash pop` | Bring the stashed work back. |

### 7c. The daily flow

#### Before you start: get the latest
```sh
cd ~/Documents/jam-and-jelly      # go into the repo folder
git checkout main                  # be on the shared-copy view
git pull                           # download latest changes
```

#### Make a change
Edit, add, or delete files using **any** tool you like — Finder/Explorer, your
notation software, a PDF viewer, etc. Git tracks the folder, not the editor.

#### Save your change onto a branch *(not main)*
**Critical rule:** never commit on `main` directly. `main` is the shared copy;
all changes go through a branch + Approve loop.

```sh
git checkout -b add-afro-blue-bass-part   # name in kebab-case, descriptive
git status                                 # show what changed
git add -A                                 # stage all the changes
git commit -m "Add bass part for Afro Blue, second verse"
git push -u origin add-afro-blue-bass-part
```

#### Open a pull request
The easiest way:

```sh
gh pr create --base main \
  --title "Add bass part for Afro Blue" \
  --body  "Adds the second verse bass part for Afro Blue."
```

Or, equivalently, in a browser: visit <https://github.com/JunzhL/jam-and-jelly/pulls>,
GitHub will offer a "Compare & pull request" button for your just-pushed branch.

Within ~3 seconds, the band sees the approval card in `#all-jam-and-jelly`.

#### When the PR is approved & merged
- The branch is deleted automatically.
- Your local copy still has the now-orphan branch. Tidy up:
  ```sh
  git checkout main
  git pull
  git branch -D add-afro-blue-bass-part
  ```

### 7d. Common situations & fixes

| Situation | What to do |
|-----------|------------|
| *"I've started editing but I'm on `main`"* | Branch protection on GitHub will block pushing to main, but to be safe: `git checkout -b my-branch` — your unsaved work follows you onto the new branch. |
| *"I made a typo in my commit message"* | If you haven't pushed yet: `git commit --amend -m "Better message"`. If you have pushed: leave it; the squash-merge will produce a clean message anyway. |
| *"I have uncommitted changes and want to switch branches"* | `git stash` to set them aside, switch, then later `git checkout my-branch && git stash pop` to bring them back. |
| *"I want to throw away changes I made and start over"* | `git restore .` (resets all files to their last-committed state). |
| *"I get a merge conflict when pulling"* | Open the file(s) git mentions. Look for lines like `<<<<<<<`, `=======`, `>>>>>>>`. Pick the right version, delete the marker lines, save. Then `git add <file> && git commit`. If overwhelmed, ask in `#all-jam-and-jelly`. |
| *"I want to look at someone else's branch without merging"* | `git fetch origin && git checkout their-branch-name`. Switch back with `git checkout main`. |
| *"I want to know who changed what"* | `git log --oneline -20` shows the last 20 commits. `git blame path/to/file` shows who last touched each line. |

### 7e. Approving a PR from the command line

You usually click ✅ in Slack. But from the terminal:

```sh
gh pr list                # see open PRs
gh pr view 5              # read PR #5's description
gh pr diff 5              # see what would change
gh pr merge 5 --squash --delete-branch   # approve + merge + tidy up
```

---

## 🔄 8 — Day-to-day workflow examples

A realistic week using a mix of paths.

### Monday — someone finds a new chart
- **Sam** finds a PDF of the Afro Blue tenor saxophone part online.
- Drops it in `#all-jam-and-jelly` with caption *"Afro Blue tenor part"*.
- Bot opens PR #7.
- **JunzhL** (on a coffee break) clicks ✅ Approve. Tenor part is now in `scores/`.

### Tuesday — typo correction
- **Mike** notices a wrong chord in Spanish Joint's guitar part.
- On laptop with Claude Code: edits the PDF in his usual tool, then says
  *"I fixed a chord in Spanish Joint. Save and create a PR."*
- Claude opens PR #8 titled *"Fix bar 24 chord in Spanish Joint guitar"*.
- Sam reviews on phone, clicks Approve.

### Wednesday — planning Thursday's rehearsal
- **JunzhL** opens the Linear app on the phone, creates three tasks:
  *"Print Afro Blue tenor part"* (assigns to Sam),
  *"Bring capo for Spanish Joint"* (Mike),
  *"Confirm time with venue"* (himself).
- Linear posts each task into `#all-jam-and-jelly` automatically — nobody has to
  re-share.

### Thursday — rehearsal
- During rehearsal, **Sam** records a phone snippet of an arrangement idea.
- Drops the M4A into Slack with caption *"new bridge idea for Really Love, 28 sec"*.
- Bot files it under `audio/` and opens PR #9. Approved on the spot.

### Friday — housekeeping
- **JunzhL** opens Linear, checks off Wednesday's completed tasks.
- Archives any tasks older than a month (keeps Linear free tier under 250 issues).

---

## 💬 9 — How Slack should be used

### One channel only
`#all-jam-and-jelly` is the channel for *everything* the band does. Don't fragment
into many channels — the workflow assumes one source of truth.

### Threads
When something needs back-and-forth (e.g. discussing a proposed change), reply in
a **thread** rather than the main channel — keeps the channel scannable.

### Mentions
- `@jar` — talks to the bot.
- `@<person>` — pings a specific person. Use sparingly; most things don't need to
  pull someone away.
- `@channel` / `@here` — pings everyone. Use only for *"please look at this now"*.

### File uploads — captions matter
Whatever you type next to the file becomes the change description that the band
sees on the approval card AND on GitHub forever. Be specific. Re-read [§ 5a].

### Notification settings (right-click the channel → Change notifications)
- **All new messages** — recommended for active members.
- **Mentions only** — quieter. You'll still see PR notifications because they
  include channel mentions.
- **Mute** — silent unless explicitly pinged.

### Search
`Cmd-F` (Mac) or `Ctrl-F` (Windows) inside Slack searches the channel.
Useful for *"what did we say about Afro Blue?"*.

---

## 📋 10 — How Linear should be used

### The board
Linear shows a kanban-style board:

```
 Backlog        Todo            In Progress       Done
 ---------      ---------       -------------     ----------
 idea 1         find chart      print parts       confirmed time
 idea 2         bring gear      learn intro       paid venue
```

A task moves left-to-right as work progresses.

### Creating tasks
- **From Slack** (easiest): hover any message → `⋯` → **Create issue in Linear**.
  The message body pre-fills the description.
- **In Linear itself:** click the **`+`** in the top bar → enter a title, assignee,
  due date.

### Anatomy of a good task
- **Title:** short and verb-first. *"Find horn chart for Really Love"* not
  *"Horn chart"*.
- **Assignee:** the person responsible. (If unsure, leave blank — anyone can
  claim it.)
- **Due date:** if it has a deadline.
- **Priority:** Urgent / High / Medium / Low / No priority. Use sparingly.

### Working a task
1. Open Linear app or web.
2. Pick a task from "Todo" → drag to "In Progress" (or open and change status).
3. Do the work.
4. Mark **Done** when finished, or **Cancelled** if it's no longer needed.

### Notifications
- Task created → posts to `#all-jam-and-jelly` automatically.
- Task assigned to you → Slack DM from Linear's bot.
- Task status change → posts to channel.

You don't need to manually copy task updates into Slack — the integration handles it.

### Archiving
Linear free tier caps at **250 active issues**. Every few months, archive old
finished tasks: Linear → filter by *Done* → multi-select → Archive.

---

## 🎬 11 — Common scenarios — step by step

### "I want to add a sheet music PDF"
**Slack:**
1. Open `#all-jam-and-jelly`.
2. Drag PDF in, caption *"Add Afro Blue piano part"*.
3. Wait 5 seconds. PR card appears.
4. Anyone clicks ✅ Approve. Done.

### "I want to fix a typo in an existing file"
**Slack:** download the original, fix it, re-upload with caption
*"Update Afro Blue piano — corrected key signature"*. The bot replaces the file
on a new branch + opens a PR.

**Laptop / Claude Code:** *"Open `scores/afro blue piano.pdf` … oh wait I'll
edit it in my notation app. Tell Claude when done, then say 'save and PR'."*

**Laptop / terminal:** edit the file, then:
```sh
git checkout -b fix-afro-blue-key
git commit -am "Fix key signature on Afro Blue piano"
git push -u origin fix-afro-blue-key
gh pr create --fill
```

### "I want to plan a rehearsal"
1. Open Linear, create a task *"Rehearsal Tue 2026-06-15 — Afro Blue + Spanish Joint"*.
2. Set assignee (whoever's organising), due date.
3. Notification automatically posts to `#all-jam-and-jelly`.

### "I want to see what changed this week"
- **In Slack:** scroll back in `#all-jam-and-jelly` — every change has a
  notification.
- **On GitHub:** <https://github.com/JunzhL/jam-and-jelly/commits/main> shows
  every merged change chronologically.

### "Someone proposed a change — should I Approve or Reject?"
1. Click **View on GitHub**.
2. Read the change description.
3. Look at the actual file diff (GitHub shows the change clearly).
4. ✅ Approve if it looks right.
5. ❌ Reject if not — then reply in `#all-jam-and-jelly` (in a thread on the card
   if possible) saying *why*, so the proposer can fix it.

### "I want to grab the latest version of a file to my computer"
- **Easiest:** open the file on GitHub in a browser, click **Download** (`...` →
  Download). Works for one-off needs.
- **Laptop / Claude Code:** *"Get me the latest version."*
- **Laptop / terminal:** `cd ~/Documents/jam-and-jelly && git pull`.

---

## 🔔 12 — What notifications you'll see

Everything below appears in `#all-jam-and-jelly`. If you don't want them all, see
the Notification settings in § 9.

| Trigger | Message you'll see |
|---------|--------------------|
| Someone proposes a change (PR opened) | 🎵 *"New change proposed — PR #N"* with Approve / Reject buttons |
| A change is merged into the shared copy | 🤖 *"JunzhL pushed 1 commit to main: …"* (from GitHub's Slack app) |
| A change is **closed without merging** (anywhere) | 🚫 *"PR #N closed without merging: …"* |
| Someone uploads a file in Slack | 🤖 *"Got it — `<filename>` committed to `<folder>/`."* |
| A new Linear task is created | 🗒️ *"<Task title> — assigned to @<who>"* |
| A Linear task changes status | 🗒️ *"<Task title> moved to In Progress"* |
| A GitHub issue is opened | 🐛 *"Issue opened: …"* |

> **Tip:** if a thread keeps pinging you and you've already read it, long-press the
> first message → **Mute thread**. The thread stays open but stops notifying.

---

## 🆘 13 — Troubleshooting & common questions

**"Can I break something by clicking the wrong button?"**
No. Every change is reversible (we keep history forever), and the shared copy is
protected — nothing reaches it without an explicit approval click. There's also a
confirm dialog on Approve.

**"I uploaded a file but the bot said nothing."**
Wait ~10 seconds. If still nothing, your file is probably over 2 MB — switch to
path B or C. If you're sure it's under 2 MB, try again with a slightly different
caption.

**"My file is over 2 MB. What now?"**
Use path B (Claude Code) or path C (terminal) — no size limit. Or, if it's a
recording, trim it first to a shorter clip.

**"I rejected a PR by accident."**
Open the PR on GitHub (click "View on GitHub" from the channel message),
click **Reopen pull request** at the bottom. The Slack card stays as "rejected" but
the PR is back open — re-upload or comment on it.

**"The bot @jar didn't reply to me."**
Wait ~30 seconds — `@jar` chat sometimes takes time. If still nothing, see § 14.

**"Where do I see all the files?"**
<https://github.com/JunzhL/jam-and-jelly> — folders at the top.

**"Where do I see all the tasks?"**
Linear mobile app or <https://linear.app> — the board view.

**"Two of us tried to approve the same PR at once."**
Slack only lets the first click count. The second person will get a quiet
*"already merged"* error. Not a problem.

**"I want to undo a merge that just happened."**
Easiest: revert it as a new change. On GitHub, open the merged PR → scroll to
**Revert** → opens a new PR that undoes the merge. Approve as usual.

**"Can I work offline?"**
- Slack: no — needs internet.
- Laptop with Git: yes, as long as you have a local copy. You make commits offline,
  then `git push` when you're back online.

---

## 🌙 14 — If `@jar` says "chat is offline"

The conversational `@jar` features need an active Claude paid plan. When the
band's plan is on Free, `@jar` will reply with *"My chat brain is offline right
now…"* and a list of alternatives. **Everything else keeps working:**

| Want to… | Do this instead |
|----------|-----------------|
| Add a file | Just attach it in the channel — uploads always work. |
| Approve / reject a change | Use the buttons — always works. |
| Create a task | Hover any message → `⋯` → **Create issue in Linear**. |
| See what's open | Open Linear (tasks) or scroll the channel (PRs are right there). |
| Read / edit a file | Open the **View on GitHub** link from any notification. |
| Anything more complex | Use path B (Claude Code) or path C (terminal) from your laptop. |

The button-driven Slack workflow + native notifications form a complete loop on
their own. The bot is a nice-to-have layer on top, not a critical dependency.

---

## 📇 15 — Quick reference card

Pin this to your phone wallpaper if you like.

```
TO DO THIS                   YOU DO THIS                                   WHERE
─────────────────────────────────────────────────────────────────────────────────
Add a file                   Drop in #all-jam-and-jelly, write caption     Slack
Approve someone's change     Click ✅ Approve & Merge                       Slack
Reject someone's change      Click ❌ Reject                                Slack
Add a task                   ⋯ on a message → Create issue in Linear        Slack
                             OR @jar add a task: ...
Ask the bot something        @jar <your question>                          Slack
See all files                github.com/JunzhL/jam-and-jelly                Web
See all tasks                Linear app                                    Mobile

LAPTOP (Claude Code)         You say...                                    Claude Code
─────────────────────────────────────────────────────────────────────────────────
Save my changes              "Save my changes"
Share with band              "Create a pull request"
Approve a change             "Show open PRs", "Approve PR #5"
Get the latest               "Get me the latest version"

LAPTOP (terminal git)        You type...                                   Terminal
─────────────────────────────────────────────────────────────────────────────────
Get the latest               git pull
Start a change               git checkout -b my-branch
Save the change              git add -A && git commit -m "..." && git push
Propose to the band          gh pr create
Approve a change             gh pr merge <num> --squash --delete-branch
```

---

Welcome aboard! 🎺 If anything in here is unclear, ask in `#all-jam-and-jelly` —
the bot (or a human) will help.
