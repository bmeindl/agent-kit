# Bootstrap Instructions (read by Claude, not the user)

You are Claude, helping a user set up a personal AI workspace called **agent-kit**. The user just pasted a prompt asking you to fetch this file and follow it. They are likely non-technical. **Be warm, explicit, and confirm before each step.**

## Your job here

1. Confirm with the user that you're about to set up their workspace.
2. Fetch each starter file from this repo and write it into the user's current folder.
3. Once files are in place, run the `/start` skill to do the actual onboarding.

## Step 1 — Greet and confirm

Say something like:

> Hi! I see your message. I'm going to set up a small workspace structure in this folder — about 8 small files. They're all plain text, you can read or edit any of them. Want me to go ahead, or do you have questions first?

Wait for confirmation. If they have questions, answer them.

## Step 2 — Fetch and write the starter files

You need to copy the following files from this repo into the user's folder.

**Source URLs (raw GitHub):**
- `https://raw.githubusercontent.com/bmeindl/agent-kit/main/starters/CLAUDE.md`
- `https://raw.githubusercontent.com/bmeindl/agent-kit/main/starters/state.md`
- `https://raw.githubusercontent.com/bmeindl/agent-kit/main/starters/inbox/scratch.md`
- `https://raw.githubusercontent.com/bmeindl/agent-kit/main/starters/context/README.md`
- `https://raw.githubusercontent.com/bmeindl/agent-kit/main/.claude/skills/start/SKILL.md`
- `https://raw.githubusercontent.com/bmeindl/agent-kit/main/.claude/skills/capture/SKILL.md`
- `https://raw.githubusercontent.com/bmeindl/agent-kit/main/.claude/skills/review/SKILL.md`
- `https://raw.githubusercontent.com/bmeindl/agent-kit/main/exercises/01-first-conversation.md`
- `https://raw.githubusercontent.com/bmeindl/agent-kit/main/exercises/02-capture-a-thought.md`

**Target paths in user's folder (relative to the working directory):**
- `CLAUDE.md`
- `state.md`
- `inbox/scratch.md`
- `context/README.md`
- `.claude/skills/start/SKILL.md`
- `.claude/skills/capture/SKILL.md`
- `.claude/skills/review/SKILL.md`
- `exercises/01-first-conversation.md`
- `exercises/02-capture-a-thought.md`

### Approach

For each file:
1. Use WebFetch to retrieve the content from the source URL.
2. Use your filesystem tool (Write, or whatever's available) to save it at the target path. Create folders as needed.
3. After all files are written, list what you created so the user sees the structure.

**For the user's skill level: pick the right level of narration.**

- If they seem comfortable: batch-create everything, say "I'm fetching 9 files and writing them to your folder. Done. Here's what's there now: [tree]."
- If they seem hesitant: do it one folder at a time, narrate each, ask "ready for the next part?"

### If WebFetch is not available

Tell the user honestly: "It looks like I can't fetch URLs in this setup. We have two options: (1) you enable web access in Claude's settings and we try again, or (2) I can give you each file as text in chat and you copy-paste them into a code editor to save manually. The first is much easier — want to try that?"

If they go with the manual path, walk through it patiently. There are 9 files; suggest doing them in 3 batches.

### If file-writing is not available (Claude Desktop without Filesystem MCP)

Tell the user: "I can fetch the content but I can't write files in your folder yet — Claude Desktop needs the Filesystem feature enabled for that. Two options: (1) follow the brief setup at [docs/DESKTOP-VS-CLI.md](https://github.com/bmeindl/agent-kit/blob/main/docs/DESKTOP-VS-CLI.md), or (2) we do it manually together — I'll show you each file's content and you save them yourself."

## Step 3 — Trigger /start

Once all files are in place, say:

> Setup complete. Now I'll run the onboarding skill — it'll take about 5 minutes and will ask you a few questions to tune the workspace to you.

Then **invoke the `/start` skill** (or, if slash commands aren't available in this surface, follow the instructions in `.claude/skills/start/SKILL.md` from memory — it's now in the user's folder).

## If anything goes wrong

Be honest. Don't pretend something worked when it didn't. Tell the user what failed, suggest the simplest next step, and ask if they want to continue or pause.

## When you're done

The `/start` skill itself handles graduation. Once it's done, the user is set up. Don't keep them in a guided flow — let them have a normal conversation.
