---
name: capture
description: Deliberate capture of a thought, learning, or decision into inbox/scratch.md with light routing. Triggers when the user says "/capture", "remember this", "save this", "let me capture", or similar. Distinguishes fleeting notes (just save), learnings (save + flag for later promotion to context/), and decisions (save with [decision:] marker).
---

# /capture

Help the user save something with a little more deliberation than the default "just say it" capture protocol.

## Flow

1. **Get the content.** If they already said what to capture, use that. Otherwise: "What do you want me to remember?"

2. **Light routing question** (only if not obvious from content):

   > Is this:
   > - **Fleeting** — just a note, may not matter later (default)
   > - **A learning** — an insight, observation, or pattern you want to come back to
   > - **A decision** — a commitment to do or change something

   For `chatgpt-fluent` and `power-user` skill levels: skip this question if you can clearly tell which it is from the content. Just say "I'm filing this as a [type] — say if I should change that."

3. **Write to `inbox/scratch.md`.** Append at the bottom (under any existing date sections). Format depending on type:

   **Fleeting** (default):
   ```
   ## YYYY-MM-DD
   - <content>
   ```

   **Learning** (add a 🌱 marker — humans and the agent can both see "this might deserve to graduate to context/" later):
   ```
   ## YYYY-MM-DD
   - 🌱 <content>
   ```

   **Decision** (add a `[decision]` marker for findability):
   ```
   ## YYYY-MM-DD
   - [decision] <content>
   ```

4. **Show what you wrote.** Briefly. Don't make a big deal of it.

5. **Update `state.md`** — increment "Captures so far: N+1".

## Special cases

- **User captures something about a person and there's a `context/people/` folder** → after writing to scratch.md, ask: "This is about [name] — want me to also note it under `context/people/[name].md`? It can live in both places, or just here for now."

- **User has 5+ recent learnings (🌱) in scratch.md** → gently suggest: "I notice you've been collecting learnings about [theme]. Want to spend 5 minutes pulling them together into a `context/[theme].md` so they don't get lost in scratch?" Only suggest once per session.

- **User explicitly says "save to context"** → write directly to a topic file in `context/` instead of scratch. If the topic file doesn't exist, ask: "What should this file be called?"

## Tone

Lightweight. Capture should feel like throwing a coin in a jar — frictionless, satisfying, no lecture. Don't ask 4 questions when 0 will do.

## When you're done

Just confirm in one line. "Got it — saved to scratch as a learning." Move on.
