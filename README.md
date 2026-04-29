# agent-kit

> A starting point for building a personal AI workspace with Claude. The AI does the rest.

If you've ever thought *"I want my AI to actually remember me"* — this is for you.

You'll end up with a small folder on your computer where Claude keeps track of you over time: thoughts you've captured, things that matter to you, what you're working on. It gets sharper the more you use it. **It is yours, lives on your computer, and you control it.**

---

## Who this is for

- **Anyone who's used ChatGPT** and felt the frustration of "it doesn't remember anything"
- **Non-developers welcome** — we walk you through everything in plain language
- **You don't need GitHub, Git, or a terminal** to start using it once you've set up Claude itself

If you're a developer: you'll probably skim the README, run the CLI path, and be done in 5 minutes.

---

## How to start (≈10 minutes)

### Step 1 — Install Claude (one-time)

Pick one. **Either works**, with different tradeoffs:

| | Claude Code (CLI) | Claude Desktop App |
|---|---|---|
| Best for | Comfortable with simple terminal commands | Visual, no terminal at all |
| Setup time | ~5 min | ~10 min (one extra step) |
| Ongoing | Type `claude` in a folder | Click a folder, chat |

**→ See [`docs/DESKTOP-VS-CLI.md`](docs/DESKTOP-VS-CLI.md)** for which to pick.

Quick links:
- **Claude Code (CLI):** https://claude.com/claude-code (install command provided there)
- **Claude Desktop:** https://claude.ai/download

### Step 2 — Make a folder for your workspace

Anywhere you like. Examples: `Documents/my-agent-kit`, `Desktop/my-claude`, etc. Name it anything.

This folder is where your AI workspace lives. **Everything stays on your computer** unless you decide otherwise.

### Step 3 — Open Claude in that folder

**If using Claude Code (CLI):**
1. Open Terminal (Mac) or Command Prompt / PowerShell (Windows)
2. Navigate to the folder: `cd Documents/my-agent-kit` (or wherever it is)
3. Type `claude` and press Enter

**If using Claude Desktop:**
1. Open Claude Desktop
2. Drag your folder into the chat window — OR — click `File → Add to Project` and select your folder
3. Make sure the Filesystem feature is enabled for that folder (see [Desktop setup notes](docs/DESKTOP-VS-CLI.md))

### Step 4 — Paste this message

```
Hi! I'd like to set up a personal AI workspace based on the agent-kit project.
Please fetch this file and follow it carefully:

https://raw.githubusercontent.com/bmeindl/agent-kit/main/INSTRUCTIONS.md

I'm not technical and I'd rather not memorize anything — please walk me 
through gently. Show me what you're about to do before doing it. If I'm 
confused, slow down rather than push through.
```

That's it. Claude will fetch what it needs, set up your workspace, ask you a few questions, and start coaching.

---

## Stuck?

| Symptom | Try |
|---|---|
| "WebFetch isn't available" / "I can't access URLs" | Make sure web access is enabled in your Claude settings. In Desktop, this is under Settings → Tools. |
| "I can't write files" (Desktop only) | The Filesystem MCP isn't enabled for your folder. See [Desktop setup notes](docs/DESKTOP-VS-CLI.md). |
| "What's a folder?" | Mac: Finder → File → New Folder. Windows: right-click in File Explorer → New → Folder. |
| Anything else | Just tell Claude what's stuck. Honestly — it can usually figure it out. |

---

## What you get

Your folder will contain:

- `CLAUDE.md` — the file Claude always reads first, and where your kernel principles live
- `state.md` — where you are right now, what's next, history
- `inbox/scratch.md` — loose thoughts, captures, dated entries
- `context/` — long-term memory; things worth keeping
- `.claude/skills/` — small skills like `/start`, `/capture`, `/review`

Everything is plain text. You can read it, edit it, delete it, version-control it later if you want.

---

## What you DON'T need

- ❌ A GitHub account
- ❌ Git installed
- ❌ Node.js
- ❌ npm or pip or any package manager
- ❌ Programming knowledge
- ❌ A subscription to anything beyond Claude itself

---

## Philosophy

A few things to know before you start. **TL;DR: this is slow at first.**

- The first 5 sessions will feel slower than just doing the task yourself. That's normal.
- The system gets sharper over weeks, not minutes.
- It needs you to come back. If you don't open it for two weeks, it doesn't get magically smarter.
- The most important sentence you'll learn to say: **"let's adjust this."**

For more, see [`docs/PHILOSOPHY.md`](docs/PHILOSOPHY.md). It's a 5-minute read and worth it.

---

## License

MIT. Fork it, modify it, build your own variant — that's the whole point.

## Credits

Made by [@bmeindl](https://github.com/bmeindl). Inspired by the Ground Control system Benjamin uses for his own work, distilled to a generic kernel.
