# App workflow — use all twelve skills, in this order

Do not skip a step because it is familiar. Do not add a step
nobody asked for. If a step does not apply to this app, write
why, in one line, and move on.

## 0. Brief (Karpathy: think before coding)

Fill in `templates/APP_BRIEF.md` and `templates/design.md` first.
State assumptions, list multiple interpretations if the request
is ambiguous, and ask before guessing. UNKNOWN is a valid answer;
an invented answer is not.

## 1. Research (agent-reach)

- What exists already? What do users actually do? What is the
  current state of the platform, API, or store rules?
- Run agent-reach where it helps (GitHub, V2EX, platform search/
  read); use browser/social search where it fails.
- Record sources and dates. Separate a live result from a
  search snippet, a count from content, and a public summary
  from a full post/comment/subtitle.

## 2. Study a reference, if there is one (REAP, clean-room)

- One feature per prompt. Use `skills/reap/REAP-README.md`
  §2 (feature tracing), §4 (behavioural cloning), §8 (Android),
  or §11 (Electron/JS) as appropriate.
- Demand file/function/address evidence. Separate confirmed
  facts, inferences, unknowns. Static first.
- Output: a behavioural spec (inputs, outputs, edge cases,
  failure modes), plus a test idea. No copied code, assets,
  branding, or licensing logic. No server, billing, DRM, or
  paywall cloning.

## 3. Plan (Karpathy: goal-driven)

Turn the brief into verifiable success criteria, one per feature:
"Write a test that reproduces X, then make it pass" / "Users can
do Y, verified by Z". List the files the change must reach:
callers, tests, fixtures, config, exports. That list is the
scope. Extra features are not scope.

## 4. Diagram the system (Archify)

- Before building, draw the planned system: architecture for
  components/services/boundaries, workflow for processes,
  sequence for API call chains, ERD for tables — pick the
  type from the question, per `skills/archify/SKILL.md`.
- Author the candidate JSON from the brief and plan only.
  No invented component, table, field, or call.
- Run `finalize` (see AGENTS.md §4) and repair failed gates.
  A passing receipt is the evidence; a hand-drawn SVG is not.
- At the end of the build, re-diagram the finished system
  for docs, from the code as built, not from the plan.

## 5. Build smallest (Ponytail + Karpathy)

Follow the reuse ladder. Build the smallest version that does
the core job, then finish every part it touches. Keep existing
structure, style, and tokens. Never cut trust-boundary validation,
security, accessibility, or data-loss handling. Risky logic gets
one small test. A known shortcut gets a `shortcut:` comment.

## 6. Design check (Hallmark, web pages only)

- New page: pre-flight first (fonts, palette, locked design.md,
  real material only — no invented numbers, quotes, or logos),
  hero alone, rendered and cold-reviewed, then the rest.
- Existing page: audit only, unless the user names Hallmark.
  Report Floor failures first, then Reflex tells, then Finish
  craft. Do not re-theme, do not change layout, until approved.
- Check at phone width as well as desktop. A broken phone
  layout is a Floor failure.

## 7. Copy check (Humanizer, prose only)

Run the 26-pattern check on every user-facing string the app
ships: landing copy, onboarding, empty states, error messages
that a user reads, docs, README, launch post. Keep every
supported claim. Fix added/dropped facts. File mode: prose only,
code/data/links unchanged.

## 8. Verify (Karpathy: goal-driven)

- Syntax and format checks for every changed file
  (`node --check`, JSON validation, XML/HTML well-formedness
  where applicable).
- ID cross-checks: every ID referenced in code exists in the
  markup/layout, and vice versa for the parts you touched.
- The success criteria from step 3, one by one, with evidence.
- A real run or manual test checklist where a unit test cannot
  cover it (e.g. load unpacked in Chrome, install on a device).
- No secrets in the diff. No seeded/simulated data presented
  as live. No TODO left that the user did not agree to defer.
- Browser tasks: Muse's browser is the default. BrowserMCP
  is a fallback only, with the user's explicit approval,
  for a task that needs their own logged-in browser profile.

## 9. Learn (Hermes learning loop + Hindsight local)

- Hindsight local, once installed: recall before a
  non-trivial task, retain learnings and procedure
  outcomes immediately, reflect to synthesise context.
  Until it is installed, this step runs on Muse's own
  memory and the Hermes loop alone — Hindsight is
  never a blocker, and its setup is never assumed done.
- Pi auto-compact rule, at every handoff and summary:
  unfinished work stays unfinished in writing — pending
  checks, blockers, and unresolved questions included.

- Search memory and past work before starting — that step
  runs first in practice, even though this step records
  its end-of-build half: what was learned, what failed
  and why, what was corrected.
- If a pattern from this build would help in two or more
  future apps, draft a skill for it (or repair the skill
  that should have covered it). Propose it; do not add it
  to the repo without approval for that exact file list.
- Surface stale or conflicting notes, and skills that did
  not help, as a short end-of-build list. Prune superseded
  claims in active summaries; correct dated notes in place
  by naming what they replace.
- No secret, key, or private identifier goes into memory
  or a skill, ever.

## 10. Ship (approval only)

List the exact files changed, the verified checks, what was
skipped/not checked, and any risk. Push, publish, or release
only after the user approves that exact list. A push approval
covers exactly those files — nothing else, no extra "cleanup".
