# AGENTS.md — app-builder-skills

Standing rule, set 2026-10-25, updated with Archify and the
Hermes learning loop the same day: whenever we are making an
app, use all eight skills in this repo, in the order in
`docs/APP_WORKFLOW.md`.
This file is the short version. The full texts are in `skills/`.

## 1. Research first — agent-reach

Use live research before claiming what exists, what is current, or
what users do. Prefer agent-reach for GitHub/V2EX and for platform
content the normal web search misses; fall back to browser/social
search where agent-reach fails in this environment (YouTube/Bilibili
SSL errors, web timeouts). Read-only only: never post, comment,
like, or message. Optional/login channels stay off unless the user
picks one per channel. Report what was actually returned, not what
a summary or a count implies.

## 2. Study a reference the REAP way — clean-room only

One feature per prompt. Demand file/function/address evidence.
Separate confirmed facts, inferences, and unknowns. Static analysis
first; do not run the target until a runtime question needs it.
End with a behavioural spec or a test, never with copied code.
Extract behaviour, never code, assets, branding, or licensing
mechanisms. Server-side systems, accounts/billing, DRM, and
paywalls are out of scope. Anti-cheat/DMA/cracking prompts are
defensive/research only.

## 3. Think before coding — Karpathy

State assumptions explicitly. Present multiple interpretations
instead of picking one silently. Push back when a simpler approach
exists. Stop and ask when unclear — never guess silently.

## 4. Diagram the system — Archify

After the plan, before building, draw the system with Archify:
architecture for components/services/boundaries, workflow for
processes, sequence for API call chains, ERD for tables, and so
on. Author a candidate JSON from the plan (never invent a
component, table, or call the plan does not name), then run
`node skills/archify/bin/archify.mjs finalize <type>
<candidate.json> <output.html> --quality showcase --json`
and repair any failed gate, in the candidate, before claiming
the diagram is done. A hand-drawn SVG is not a substitute.
Re-run Archify at the end for the finished system, for docs.

## 5. Smallest complete change — Ponytail (default: full)

Reuse ladder, in order: does it need to exist? → already in this
codebase? → standard library / platform feature? → installed
dependency? → one clear line? → only then the minimum code that
works. Never add a dependency for a few lines. Deletion beats
addition. Finish every part the task needs: callers, tests,
fixtures, config it breaks. Keep the codebase's existing structure.

Simplicity first (Karpathy + Ponytail, together): minimum code
that solves the problem, no speculative features, no single-use
abstractions, no error handling for impossible scenarios. Test:
would a senior engineer call this overcomplicated?

Surgical changes: touch only what the request needs, match
existing style, do not "improve" adjacent code. Every changed
line traces to the request. Mention unrelated dead code instead
of deleting it silently, unless the request is explicitly to
clean it up.

Never cut: trust-boundary validation, data-loss error handling,
security, accessibility, anything the user asked for. Risky logic
(branch, loop, parser, money, security) leaves one small test
behind.

Goal-driven execution: turn a task into verifiable success
criteria first (a failing test for a bug, then make it pass).
Verify with real checks (`node --check`, JSON validation, ID
cross-checks, a real run) before claiming done.

## 6. Design check — Hallmark, audit-first

Hallmark applies to web pages. It never re-themes an existing
design unless the user names Hallmark. A locked `design.md`
overrides themes.

Floor (never ships): tokens only for colours/fonts, no
`transition: all`, focus-visible on every interactive element,
reduced-motion fallback, no invented metrics/testimonials/logos,
no eyebrow and no tracked-capital labels, hero headline +
sentence + primary action visible at 1280x800 without scrolling,
no purple-to-blue gradient, no card-in-card, no emoji as icon.

Reflex gates (model defaults) may be overruled only with a
recorded reason. Finish checks are craft detail, never blocking.

For an existing page, run Hallmark as audit: report the tells,
do not change the design until the user approves the fixes.

## 7. Copy check — Humanizer, prose only

Apply to user-facing prose: landing copy, docs, READMEs, launch
posts. Not to code, data, frontmatter, or link targets.

Mark tells strongest first: not-X-but-Y, one-line closers, deep
sayings, staged run-ups, arguing with no one, forced triads,
repeated openings, dashes everywhere, overused AI words, inflated
significance, sales language, borrowed authority, bold as
decoration, decorative headings, chat leftovers, writing for the
wrong reader.

Draft a rewrite keeping every supported claim, check it for
added/dropped facts and surviving tells, then write the final
version with varied sentence length. Never invent a name, number,
date, quote, or citation — ask if a detail is missing. Match a
voice sample if the user gives one. Humanizer is not a detector
bypass.

## 8. Learn, then ship — Hermes learning loop

Search memory before starting; capture durable learning as
it is verified; after a complex task, ask whether a pattern
recurs and, if so, draft a skill for it; when corrected,
fix the memory and skill behind the reply, not just the
reply. At the end of a build, surface stale or conflicting
notes and skills that did not help, as proposals — never
as changes made on their own. Prune superseded claims so
the current account stays true. No secrets in memory, ever.
A new or changed skill enters the repo only with the user's
explicit approval for that exact file list. Full text:
`skills/hermes-learning-loop/SKILL.md`. Hermes itself —
its code, agent, gateway, and runtime — is not bundled
here; only its learning loop is adapted.

## End of every coding reply

What was skipped or not checked, and any risk the user must know.
A known shortcut gets a `shortcut: <limit>, <when to upgrade>`
comment in code.
