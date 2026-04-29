---
name: review
description: Handle a due [review: YYYY-MM-DD] marker — walk the user through the embedded questions, capture answers, decide whether to complete (delete marker), defer (rewrite with new date), or take action. Triggers when a review marker comes due (auto-surfaced on session start), or when the user says "/review", "let's review", or "do the review".
---

# /review

Walk the user through a structured reflection on a `[review: YYYY-MM-DD]` marker that came due. Goal: extract honest signal about how the system is working, capture findings, decide next steps.

## Find the marker

If the user just said "/review" without context, scan `inbox/scratch.md` for `[review: YYYY-MM-DD]` lines where `date ≤ today`. If multiple are due, list them and ask which one to do first.

## Walk through it

The marker usually contains embedded questions in parentheses, like:
```
- [review: 2026-05-12] Setup checkpoint — ... (Questions: Q1? Q2? Q3?)
```

1. **Frame it warmly.** "Two weeks ago we agreed I'd check in on this. Five minutes — honest answers, not polite ones. Worth it?"

2. **Ask the embedded questions, one at a time.** Don't dump them all at once. Wait for an answer before the next.

3. **Listen for trouble signals.** If they say:
   - "I haven't really opened it" → don't shame; ask what got in the way
   - "It's been clunky" → drill in: what specifically? Is it a friction we can fix?
   - "I don't see the point yet" → check the maturation curve framing — are we 2 weeks in or 6? Adjust expectations honestly.
   - "It's been useful" → great, but ask what specifically. Concrete examples.

4. **Capture findings to `inbox/scratch.md`** under today's date:
   ```
   ## YYYY-MM-DD — Review findings (<setup checkpoint / 6-week / etc.>)
   - <key finding>
   - <key friction or change desired>
   - <decision or next step>
   ```

## Then: complete, defer, or act

Ask the user:

> Three options for this review marker:
> - **Complete** — we did the review, delete the marker. (Fine if the next review will be different / spontaneous.)
> - **Defer** — push it out (1 week / 2 weeks / 1 month) — for if the timing was off.
> - **Re-anchor** — replace it with a NEW review marker with different questions, based on what we just discovered.

Default suggestion: **complete**. Only defer if they genuinely couldn't do it. Re-anchor if the questions changed (e.g., they're past the setup phase, want a different check-in next time).

### Complete

Edit `inbox/scratch.md` — delete the entire marker line.

### Defer

Edit the marker: change the date to the new one. Keep the questions. Tell user the new date.

### Re-anchor

Delete the old marker. Write a new one with adjusted questions. Date as agreed.

## Update `state.md`

After review, update:
- `**Last review:** YYYY-MM-DD (<short summary, e.g., "system feels stuck on capture habit; will try voice")>`
- Add to `## History`: `- YYYY-MM-DD: Review completed. <one-sentence outcome>.`
- Update `## Next Steps` if the review surfaced new directions.

## If user wants to fix something now

If the review surfaces a clear friction ("the reminder format is annoying", "I never look at scratch.md", "I don't know what to capture"), offer to address it immediately:

> Want to fix that right now while we're in it? It usually takes 2 minutes.

Examples of in-place fixes:
- Adjust skill-level marker in `CLAUDE.md` (they're more confident now)
- Add or remove a subfolder
- Edit the kernel's "About this workspace" focus
- Change the cadence of future reminders

Always read `CLAUDE.md` and `state.md` before editing — preserve the human-edited content.

## Tone

Reviews can feel like homework. Don't make them feel like that. Five minutes max unless they want to go deeper. End with: "Anything else on your mind, or shall we get on with whatever you came here to do?"
