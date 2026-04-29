# What is this?

Maybe you landed on this GitHub repo from a link a friend sent. Or from a search. Without context, it's not obvious what you're looking at.

## Short version

`agent-kit` is a starter for building a **personal AI workspace** with Claude. Specifically: a small folder structure + a few "skills" that turn a generic AI chat into something that remembers you over time.

You end up with a folder on your computer where the AI keeps track of:
- What you're working on
- People who matter to you
- Things you've learned and decided
- Your voice, preferences, working style

It's not an app. It's text files + a few clever instructions that make Claude (or another AI) work like a long-term collaborator instead of a goldfish.

## How it works (technically, briefly)

- A file called `CLAUDE.md` lives in your folder. Claude reads it at the start of every conversation. It contains your kernel: who you are, how you like to be talked to, what we're working on.
- A file called `state.md` tracks where you are right now and what's next.
- A folder `inbox/` holds loose thoughts (date-stamped).
- A folder `context/` holds long-term memory.
- A few "skills" (`/start`, `/capture`, `/review`) make common operations smooth.

Everything is plain text. You own it. You can read, edit, delete, version-control it.

## How you use it

You just talk to Claude in that folder. Like ChatGPT, but the AI has a persistent memory of who you are.

When you say "remember this" — it's in scratch.md tomorrow.
When you come back after a week — it picks up where you left off.
When something feels wrong — you say "let's adjust this" and the kernel changes.

## How to start

Read [README.md](../README.md). Takes ~10 minutes including installing Claude.

## The bigger context

This was distilled from a much larger personal AI workspace I built for myself ("Ground Control"). After enough friends saw it and said *"I want this too"* but had no idea where to start, I packaged the universal kernel — the parts that work for anyone, not just my work — into this repo.

It's intentionally minimal. Three skills, one kernel, no plugins on day one. The system is designed to grow *with you*, not start fully formed.

## Who it's not for

- People who want a polished consumer app — this isn't that
- People who won't put 5-10 minutes per week into a system — it doesn't sustain without you
- People expecting magic on day 1 — see [PHILOSOPHY.md](PHILOSOPHY.md), this is slow at first

If you're still here after reading this — start with [README.md](../README.md).
