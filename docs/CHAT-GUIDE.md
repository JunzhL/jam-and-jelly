# 💬 Chat Guide — using the band bot in Slack

Everything happens in the **#all-jam-and-jelly** Slack channel. You don't need GitHub, Git, or
any app beyond Slack on your phone. Here's everything you can do.

---

## Add or update a music file

**Just drop the file into the channel** (the `+` / paperclip in Slack) and add a short
note describing it, e.g.:

> *[uploads `afro-blue-bass.pdf`]* — bass part for Afro Blue, second verse

The bot picks it up, files it in the right place, and proposes it as a change for the
band to approve. You'll get a reply with a link.

## Ask the bot to do something

Type **`@jar`** followed by what you want, in plain English:

> `@jar what songs do we have scores for?`
> `@jar get me the latest version of Spanish Joint`
> `@jar what changes are waiting for approval?`

Ask it like you'd ask a person — it'll figure it out or ask you to clarify.

## Create a task

Two easy ways:

1. **Ask the bot:**
   > `@jar add a task: find the horn chart for Really Love, for Sam`
2. **From any message:** hover over the message → `⋯` (More actions) → **Create issue in
   Linear**. Fill in the short form.

Tasks live in **Linear**. You'll see notifications in the channel, and a daily
"🎵 Still to do" summary. Tap through to Linear for the full list.

## Approve or reject a change

When someone proposes a change, the bot posts it in the channel with two buttons:

> 🎵 **New change proposed — PR #5**
> *Add bass part for Afro Blue*
> &nbsp;&nbsp;&nbsp; **[ ✅ Approve & Merge ]** &nbsp; **[ ❌ Reject ]** &nbsp; [ View on GitHub ]

- **Anyone in the channel** can click. **Approve & Merge** adds it to the shared copy.
- **Reject** sends it back. Add a comment saying why so the person can fix it.
- Nothing reaches the shared copy until someone approves — so it's safe to take your time.

## Get the latest

> `@jar give me the latest`

The bot tells you what's new.

---

## Good to know

- **You can't break anything.** Every change is reviewed before it counts, and old
  versions are always recoverable.
- The bot only acts in **#all-jam-and-jelly** — keep band file chat in that channel.
- **File size limit:** uploads in Slack are capped at ~2 MB. If you have a bigger
  file (e.g. a long audio recording), the bot will tell you and you can add it via
  the laptop path instead — see [BAND-GUIDE.md](BAND-GUIDE.md).
- Prefer working from a computer with files in a folder? See
  [BAND-GUIDE.md](BAND-GUIDE.md) instead.
- Something stuck or confusing? Just say so in the channel — `@jar` or a
  human will help.

## If `@jar` says "chat is offline"

The conversational `@jar` features need an active Claude paid plan. If that's lapsed,
the bot will reply with a "chat is offline" message — everything else still works:

| Want to… | Do this instead |
|----------|-----------------|
| Add a file | Just attach it in the channel — file uploads always work, even when chat is offline. |
| Approve / reject a change | Click the buttons on the PR notification — always works. |
| Create a task | Hover over any message → `⋯` (More actions) → **Create issue in Linear**. |
| See what's open | Look at the GitHub notifications already in the channel, or open the Linear app. |
| Anything more complex | Use the laptop guide — [BAND-GUIDE.md](BAND-GUIDE.md). |
