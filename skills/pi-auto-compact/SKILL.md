# Pi auto-compact — reference note, not an installed extension

Source: https://github.com/tmustier/pi-auto-compact (MIT, 2026,
Thomas Mustier). Status, from its own README: **deprecated
and the repository is archived**. Pi 0.86 and later provide
native mid-turn automatic compaction; Pi's
`compaction.modelOverrides` replaces this extension. Do not
install it for Pi 0.86+, and do not install it for Muse at
all — it is a Pi package, not a Muse skill, and there is no
SKILL.md upstream. This file exists only because the user
asked for all four repos to be added to the stack, and the
one durable idea in it is worth keeping.

## The idea worth keeping

When a long session is summarised — by compaction, by a
handoff, or by a new agent picking up the work — the
summary must not make unfinished work sound finished.

Keep, explicitly, in every summary and handoff:

- every pending check and tentative finding
- every candidate that has not been verified
- every blocker and unresolved question
- every task that was approved but not yet pushed,
  verified, or delivered

Dropping any of those lets the next agent act on an
unverified conclusion, or claim a task is done when it
is not.

## How this stack already does it

- The working todo list is the source of truth for
  unfinished work. A task stays open until its result
  reaches the user; a tool call, a handoff, or an
  attempted action does not complete it.
- The Hermes learning loop (see
  `skills/hermes-learning-loop/SKILL.md`) records
  failures, corrections, and verified outcomes with
  dates and sources, and prunes superseded claims
  instead of silently dropping them.
- Before retrying a failed or interrupted action,
  check what it already did — a failed report does
  not prove nothing happened.

## Limits

- This is not a compaction tool. It does not change
  how Muse compacts, and it does not install anything
  for Pi.
- If the user ever works in Pi, the migration path is
  Pi's own native compaction settings, per the
  upstream README — not this extension.
