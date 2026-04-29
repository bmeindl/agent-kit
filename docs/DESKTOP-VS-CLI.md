# Claude Desktop vs Claude Code (CLI) — Which to Use

Both work. They differ slightly in setup and ongoing UX. Pick based on your comfort.

---

## TL;DR

| | Claude Code (CLI) | Claude Desktop |
|---|---|---|
| **Best if** | You're OK opening Terminal occasionally | You strongly prefer never seeing a terminal |
| **Setup** | Install + run `claude` in folder | Install + add folder to project + enable Filesystem MCP |
| **Ongoing** | `cd folder && claude` | Open Desktop → Project pre-set |
| **File-writing** | Works out of the box | Needs Filesystem MCP enabled (one-time) |
| **Slash commands** | Native, well-discoverable | Native, less discoverable |

**Recommendation if you can't decide:** Claude Code (CLI). The setup is shorter, and the file-writing works without extra configuration. The terminal command (`claude`) is the only command you'll ever need.

---

## Claude Code (CLI) — full setup

1. Install: visit https://claude.com/claude-code and run the install command (it's one line, copy-paste in Terminal)
2. Open Terminal
3. Navigate to your workspace folder: `cd Documents/my-agent-kit`
4. Type `claude` and press Enter
5. Done — paste the bootstrap prompt from the README

To return later: open Terminal, `cd` to the folder, type `claude`.

**On Windows:** PowerShell or Command Prompt instead of Terminal.

---

## Claude Desktop — full setup

The Desktop app is friendlier visually but needs one extra setup step (enabling file-writing):

### 1. Install Claude Desktop

Download from https://claude.ai/download.

### 2. Enable Filesystem access for your folder

Claude Desktop has a feature called the "Filesystem MCP" that lets the AI read AND write files in folders you grant it access to. You need to enable this once for your `agent-kit` folder.

How (as of Claude Desktop late-2025/early-2026):

1. Open Claude Desktop
2. Click `Claude` (top menu) → `Settings` → `Developer` (or `Tools`)
3. Look for a section about "Filesystem" or "MCP servers"
4. Add your `agent-kit` folder path to the allowed list
5. Restart Claude Desktop

If your version of Desktop has a friendlier UI for this — great, follow that. The exact location of the setting moves between versions.

**If you can't figure it out:** the CLI path is genuinely easier. We're not embarrassed to recommend it.

### 3. Add your folder to a project

- Drag the folder into a Claude Desktop chat — OR —
- File → Add to Project → select your folder

### 4. Paste the bootstrap prompt

From the README. Same as CLI from here on.

---

## What if I picked the wrong one?

Both write to the same plain-text files. **If you set up with one and want to switch — just open the same folder with the other.** Your CLAUDE.md, state.md, inbox/, context/ are all there. No migration needed.

---

## What if neither works?

Something's likely an environment issue (firewall, corporate IT, etc.). Tell Claude (or the friend who recommended this) what happened. The honest answer might be: this isn't ready for your setup yet — that's fine.
