# 🎸 Band Guide — working from your laptop

This is for when you want to add or change music files **on your own computer**. You don't
need to learn Git or type any commands — you just talk to Claude in plain English, and it
does the technical part for you.

> Prefer not to install anything? You can do everything from Slack instead — see
> [CHAT-GUIDE.md](CHAT-GUIDE.md). This laptop guide is the alternative.

> **When to definitely use this guide over Slack:** uploading a big file (over
> ~2 MB — Slack uploads are capped) or when `@jar` chat is showing as offline.
> The laptop path always works.

---

## One-time setup (about 15 minutes)

You only do this once.

1. **Install Claude Code.** Go to <https://claude.com/claude-code> and follow the
   installer for your computer (Mac or Windows). Sign in with your Claude account.
2. **Get the band folder.** Ask the band organiser for the link, then in Claude Code say:
   > *"Clone the Jam & Jelly repository to my computer."*
   Claude will ask where to put it and set everything up.
3. That's it. The folder behaves like a normal folder — you can open the PDFs, add files,
   etc. — but Claude can now save and share your changes for you.

---

## Everyday use

Open Claude Code, make sure you're in the band folder, and just ask. Here are the four
things you'll do:

### 1. Save your changes
After you've added, edited, or removed files in the folder, say:
> *"I've made some changes — please save them."*

Claude will put your work on a safely-named branch and tell you the name and a short
summary. **Your changes never overwrite anyone else's.**

### 2. Share your changes with the band
When you want the band to see and approve your work, say:
> *"Create a pull request for my changes."*

Claude writes a plain-language description (you can edit it) and posts it. The band gets a
notification in Slack.

### 3. Approve someone's change *(organiser / approver)*
To see what's waiting and finalise an approved change:
> *"Show me the changes waiting for approval"* — then — *"Approve number 3."*

### 4. Get the latest version
To bring your folder up to date with the band's shared copy:
> *"Get me the latest version."*

If you have unsaved work, Claude will offer to save it first so nothing is lost.

---

## Tips

- **You can't break anything.** Every change is reversible, and the shared copy is
  protected — it only updates after an approval.
- If Claude says something confusing, just ask: *"Explain that simply."*
- Stuck? Ask in the `#all-jam-and-jelly` Slack channel.
