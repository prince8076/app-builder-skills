# Hermes learning loop — adapted, not copied

Inspired by Nous Research's Hermes Agent
(https://github.com/NousResearch/hermes-agent, MIT): a
self-improving agent that creates skills from experience,
improves them during use, persists what it learns, searches
its own past work, and builds a deepening model of its user
across sessions.

This file is original work for this collection. It borrows
the loop, not Hermes' code, prompts, skills, or agent
runtime. Hermes itself is not installed or bundled here.

## The loop, in order

### 1. Search first

Before starting a task, search memory and past
conversations, and read the project's AGENTS.md and
MEMORY.md. A preference, decision, failure, or root cause
already recorded is not re-derived, re-asked, or contradicted
without new evidence. An empty search does not prove
nothing was saved — check the files themselves.

### 2. Capture during the work

Record only what is durable, as it is verified:

- facts, preferences, decisions, and commitments
- failures and their root causes, with the fix that worked
- verified outcomes (commit, file, check that passed)

Date events by when they happened. Keep a source
reference so a later check can reach the evidence.
Memory is not a transcript, a transaction log, or a copy
of a todo list. Never record a secret, key, token,
password, or private identifier — record where it is
stored, if anywhere, never its value.

### 3. After a complex task, ask: does this recur?

If a pattern, workaround, or check would help in two or
more future apps, draft a skill for it — or update the
existing skill that should have covered it. A one-off
fix is not a skill. A skill that failed in use is a
candidate for repair, not for repeating.

Drafting is not adding: a new or changed skill goes
into the repo only with the user's explicit approval
for that exact file list, like any other push.

### 4. Improve in use, follow corrections through

When the user corrects you, or a skill gives a wrong
or stale answer:

- fix the reply, and fix the memory and skill behind it
- follow the correction through every affected note,
  doc, and pending follow-up
- leave the current account clear about what is known,
  who said it, and when — superseded claims do not stay
  active in summaries

Correcting one message while leaving the stale note in
place guarantees the same mistake next time.

### 5. Nudge, at the end of a build — never mid-task

At the end of a build or a session, surface at most a
short list, only where there is evidence:

- a memory that conflicts with what just happened
- a skill that did not help, or was not used when it
  should have been
- a pattern from this build worth turning into a skill

Do not interrupt work in progress with a review, and
do not manufacture outreach from silence. A nudge is a
proposal for the user to accept, change, or decline —
never a change made on its own.

### 6. Prune

Remove what is superseded, not what is merely old.
In active summaries, correct the claim in place. In
dated notes, add an explicit correction naming what it
replaces. Useful history stays reachable; the current
account stays true.

## What this loop never does

- It never stores a secret to "remember" it.
- It never presents a seeded, simulated, or guessed
  value as a recorded fact.
- It never copies another product's code, branding,
  assets, or licensing mechanism into a skill.
- It never pushes, publishes, or deletes anything
  irreversible without the user's explicit approval
  for that exact action.
- It never treats a past approval as approval for a
  new task.
