# App workflow — use all six skills, in this order

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

## 4. Build smallest (Ponytail + Karpathy)

Follow the reuse ladder. Build the smallest version that does
the core job, then finish every part it touches. Keep existing
structure, style, and tokens. Never cut trust-boundary validation,
security, accessibility, or data-loss handling. Risky logic gets
one small test. A known shortcut gets a `shortcut:` comment.

## 5. Design check (Hallmark, web pages only)

- New page: pre-flight first (fonts, palette, locked design.md,
  real material only — no invented numbers, quotes, or logos),
  hero alone, rendered and cold-reviewed, then the rest.
- Existing page: audit only, unless the user names Hallmark.
  Report Floor failures first, then Reflex tells, then Finish
  craft. Do not re-theme, do not change layout, until approved.
- Check at phone width as well as desktop. A broken phone
  layout is a Floor failure.

## 6. Copy check (Humanizer, prose only)

Run the 26-pattern check on every user-facing string the app
ships: landing copy, onboarding, empty states, error messages
that a user reads, docs, README, launch post. Keep every
supported claim. Fix added/dropped facts. File mode: prose only,
code/data/links unchanged.

## 7. Verify (Karpathy: goal-driven)

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

## 8. Ship (approval only)

List the exact files changed, the verified checks, what was
skipped/not checked, and any risk. Push, publish, or release
only after the user approves that exact list. A push approval
covers exactly those files — nothing else, no extra "cleanup".
