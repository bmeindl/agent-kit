---
name: start
description: First-time onboarding for a new agent-kit workspace. Triggers when the user first opens Claude here, when CLAUDE.md shows onboarding-status:pending, or when the user explicitly asks to start (over). Detects skill level, brainstorms use case, sets up minimal folders, runs first capture, seeds 2-week and 6-week reminders, updates CLAUDE.md and state.md.
---

# /start

You are running the onboarding flow for a non-technical user setting up their personal AI workspace. Be warm, patient, and explicit. Show what you're about to do before doing it. If at any point the user seems lost or overwhelmed, slow down rather than push through.

## Before you begin

Read the current state of these files in the workspace:
- `CLAUDE.md` — to confirm onboarding-status is `pending` (or to detect if user is re-running)
- `state.md` — to see if any partial progress exists

If `<!-- onboarding-status: completed -->` is set in `CLAUDE.md`, ask the user: "It looks like onboarding has already been completed. Do you want to (a) start over from scratch, (b) just update one thing (skill level / focus / etc.), or (c) cancel?" — handle accordingly.

Otherwise, proceed.

## Step A — Welcome (warmth before mechanics)

Say something like (adapt phrasing — these are intentions, not scripts):

> Hi. Three things to know before we do anything:
>
> 1. **You can't break anything.** Everything we do stays in this folder you control. If we mess something up, we just edit a file.
> 2. **The first few times will feel slower than just doing the thing yourself.** That's the cost of teaching me who you are. It pays back after 2-3 weeks.
> 3. **Ask me anything.** Even "is this possible?" or "what makes sense here?" — that's the whole point.
>
> Ready? Five minutes total.

Wait for confirmation. If they're hesitant, slow down. If they ask a question, answer it before moving on.

## Step B — Skill-level detection

Ask THREE questions, one at a time. Wait for each answer before asking the next.

1. **"Have you ever opened a Terminal or Command Prompt before today?"** (yes / no / once or twice)
2. **"Have you used ChatGPT (or similar AI tools) regularly in the last 6 months?"** (yes / no)
3. **"Where do you see yourself: (a) I use AI sometimes but I'm not techy, (b) I'm curious and try a lot of things, (c) I'm pretty tech-comfortable."**

Bucket assignment:
- **Q1 = no** → `never-coded`
- **Q1 = no/once + Q2 = yes** OR **Q3 = b** → `chatgpt-fluent`
- **Q1 = yes + Q2 = yes** OR **Q3 = c** → `power-user`

Tone for the rest of the session:
- `never-coded` — explain everything BEFORE doing it. Confirm before each file write. Show file contents when previewing. Avoid jargon — never say "MCP", "API", "stdout", etc. unprompted.
- `chatgpt-fluent` — explain when it matters; confirm before destructive ops; routine writes can be batched with a brief "I'm going to write three files now, here's why."
- `power-user` — terse. Batch operations. Skip "do you want me to proceed?" on routine work.

**Write the skill level to `CLAUDE.md`:** find the line `<!-- skill-level: -->` and replace with `<!-- skill-level: never-coded -->` (or appropriate bucket).

## Step C — Brainstorm the use case (this is a real conversation, not a multiple-choice menu)

Say something like:

> Let's brainstorm what you'd actually use this for. Here are some areas — just for inspiration, not a checklist:
>
> - **People** — folks who matter to you, what you've talked about, what's on their mind
> - **Personal themes** — coaching/reflection, habits, a life topic you're working on
> - **Projects** — a side-project, an investment, a hobby, a specific thing in motion
> - **Work** — organizing yourself better, capturing knowledge from your job
> - **Learning** — something you're studying, notes, your evolving understanding
>
> Which sounds most like you? Or something else entirely? You don't have to commit — we can also start with two areas if that's more honest. **But please not five.** Focus is the whole point.

Listen carefully. Reflect back what you heard in your own words. Ask 1-2 clarifying questions if needed (e.g., "When you say 'people', do you mean the same handful of close people, or a wider network like work contacts?").

**If they pick 3+ areas:** push back gently. "I hear you on all of those. For the next 4 weeks, I'd suggest we pick the one that feels most pressing right now and put the others on a 'later' list. Which is most urgent?"

**Write the focus to `CLAUDE.md`:** Replace `[filled by /start — what we're using this for]` in the "About this workspace" section with a one-sentence summary of the chosen focus.

## Step D — Folder bootstrap (minimal, with discretion)

Tell the user what you're about to do. Adjust language to skill level.

For `never-coded`:
> I'm going to make a few things in your folder. Let me show you each one before I create it:
>
> - `inbox/` — a folder. Inside, a file called `scratch.md` where loose thoughts go.
> - `context/` — a folder for things you want to keep long-term.
> - `state.md` — a small file that helps me remember where we are between conversations.
> - I'll also fill in your `CLAUDE.md` (which already exists) with what we just talked about.
>
> Sound OK? I'll go one at a time and show you the result.

For `chatgpt-fluent` / `power-user`:
> I'm setting up the basic structure: `inbox/scratch.md`, `context/`, `state.md`, and filling in `CLAUDE.md`. Going.

The starter files (`inbox/scratch.md`, `context/README.md`) should already exist from the bootstrap. If not, create them with minimal content.

**Subfolder check.** Based on the chosen focus, decide if ONE subfolder makes sense:
- Focus = People → propose `context/people/`
- Focus = Learning → propose `context/notes/`
- Focus = Project(s) → propose `context/<project-name>/` (ask for name)
- Focus = Personal themes → usually NO subfolder (themes evolve, naming is hard early)
- Focus = Work → usually NO subfolder yet (work has many shapes)

Ask:

> For your focus on [...], one subfolder might earn its place: `context/[name]/`. Want me to create it now, or wait until we have something to put in it?

If they say wait or hesitate — wait. **Default to NOT creating it.**

If they say yes — create it with an empty `README.md` inside that says `Things related to [focus] go here.`

**Update `state.md`** with the new "Subfolders:" line if a subfolder was created.

## Step E — First capture (learning by doing)

Tailor the prompt to the chosen focus:
- People → "Tell me about one person who matters to you and is on your mind right now. A sentence or three is plenty."
- Personal themes → "What's a thought or observation you've had this week about [their theme] that you'd want to remember?"
- Projects → "In two sentences: what's the project, and what's the next step you keep meaning to take?"
- Work → "What's something at work you wish you'd remembered better last week?"
- Learning → "What's something you learned recently that surprised you, or that you want to come back to?"

Wait for their answer. Then:

1. Append it to `inbox/scratch.md` with today's date. Format:
   ```
   ## [YYYY-MM-DD]
   - [their content, lightly cleaned up — fix obvious typos but preserve their voice]
   ```
2. Show them what you wrote.
3. Narrate: "That's the whole capture protocol. From now on, anytime you tell me something worth remembering, I'll add it here. You don't need a special command — just say it. If you want to be deliberate, say `/capture`."

## Step F — Reminder seeding

Compute two dates:
- `review_2w` = today + 14 days
- `review_6w` = today + 42 days

Append to `inbox/scratch.md`:

```
---

## Reminders (set during onboarding)

- [review: <review_2w>] Setup checkpoint — How does the system feel? Is it paying back? (Questions: Have you opened Claude regularly? Has scratch.md grown? Has anything been clunky? Anything you want to change?)
- [review: <review_6w>] 6-week maturity check — Is this paying back yet? Time to add a second focus area? (Questions: What's working? What isn't? What capability would help most next?)
```

Tell the user:

> I just set two reminders for myself. In 2 weeks (<date>) and in 6 weeks (<date>). Next time you open Claude here on or after those dates, I'll bring them up before anything else. They're intentional, not a bug — the system needs check-ins to stay sharp.

## Step G — Update state.md

Open `state.md` and update:

```markdown
**Last updated:** <today>

## Current State

- **Skill level:** <bucket>
- **Onboarding completed:** <today>
- **Active focus:** <one-sentence focus>
- **Subfolders:** <subfolder if created, else "none yet">
- **Captures so far:** 1
- **Last review:** -

## Next Steps

- Continue captures naturally — anytime something matters, just say it
- In 2 weeks (<review_2w>): first setup checkpoint
- Optional: explore what else this can do — ask me "can I do X?" anytime

## History

- <today>: Onboarding completed. Skill level: <bucket>. Focus: <focus>. First capture written.
```

## Step H — Update CLAUDE.md onboarding status

Find `<!-- onboarding-status: pending -->` in `CLAUDE.md` and change it to `<!-- onboarding-status: completed -->`.

Also fill in:
- Owner (ask the user "what's your name?" if not already known) — replace `[your name]`
- Started — replace `[filled by /start]` with today's date

## Step I — Graduation

Say something like:

> You're set up. Four things to take with you:
>
> 1. **Just talk to me normally.** Slash commands are optional — `/capture` if you want to be deliberate, otherwise just say things.
>
> 2. **Ask me anything.** "Can I do voice notes?" "Can I read my email?" "Can it remind me to call mom?" — ask. I'll research and propose options. Nothing is automatically off the table.
>
> 3. **It lives if you come back.** If I don't hear from you for two weeks, the system doesn't get magically smarter. We're a relationship, not an app you install once.
>
> 4. **The most important sentence is "let's adjust this."** When something feels off, say it. We change it. The kernel (`CLAUDE.md`) is yours — it should reflect you, not me.
>
> Want me to walk you through one of the practice exercises? They're optional — just two short ones in `exercises/`.

## Edge cases

- **User wants to abort mid-flow.** Save what you've gathered to `state.md` under a "Partial onboarding" section. Tell them: "No problem. When you come back, run `/start` again — I'll pick up where we left off."
- **User picks a focus that doesn't fit any of the inspirations.** Great — go with it. Adapt step E's first-capture prompt to their actual focus.
- **User has zero idea what to use this for.** Don't force it. Suggest: "Let's start with personal themes — anything that's been on your mind lately. We can refine the focus after a week of just talking." Set focus to "exploring".
- **User on Windows uses backslashes in paths.** Always use forward slashes when writing in files. Claude handles platform translation.

## When you're done

Mark onboarding as completed and stop. Don't keep the user in a guided flow once they've graduated — let them experience normal conversation.
