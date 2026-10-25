# Gstack workflows — adapted, not installed

Adapted from https://github.com/garrytan/gstack (MIT, Garry
Tan): four of its workflows — office-hours, review, qa,
and ship — rewritten in original summary form for Muse.
No gstack code, binary, telemetry, memory system, or
Claude Code slash command is bundled here, and gstack
itself is not installed by copying this repo. The
upstream skills are long, Claude Code-specific files
(office-hours ~1,350 lines, review ~1,200, qa ~780,
ship ~1,230, most of it shared preamble); this file
keeps only the workflow logic that survives without
that harness.

## Governing rule — read first

Gstack's ethos says "boil the ocean": prefer the full
implementation over a 90% shortcut, because AI makes
completeness cheap. That rule does **not** govern here.

In this stack, Karpathy + Ponytail govern: smallest
complete change, simplicity first, no speculative
features, every changed line traces to the request.
Gstack's workflows below are gates and questions
applied to the requested scope — they never expand
scope, and they never justify a bigger build than
the user asked for. Where the two conflict, the
smaller, in-scope version wins.

Two other upstream defaults are also overridden here:

- Gstack ship treats some routine work as needing no
  confirmation. Here, a push, publish, or release
  still needs the user's explicit approval for that
  exact file list, every time. No exception.
- Gstack workflows call their own binaries, telemetry,
  GBrain memory, Aside research, and Greptile review.
  None of those exist here. Their Muse equivalents
  are: memory search + MEMORY.md, browser/web search,
  and this repo's own checklist — used in that order,
  never assumed installed.

## 1. Office-hours — understand before building

Use at the brief stage, before any code. Hard gate:
**no code, no scaffold, no implementation action.**
The only output is a design document, and it is not
written until the user approves the approach.

### Context first

- Read the project's brief, design doc, and recent
  history (docs, git log, current diff) and map the
  codebase areas the request touches.
- Search memory and prior design docs for the same
  problem. If a prior design exists, surface it and
  ask whether to build on it or start fresh. Do not
  re-ask a question memory already answers.
- Ask the goal, plainly: what are you building, who
  is it for, and what stage is it at — idea, has
  users, has paying customers, or internal/demo/
  learning project? The answer sets which questions
  below apply.

### The six forcing questions (startup mode)

Ask one at a time, in order, and wait for the answer.
Push on each until the answer is specific and
evidence-based — a name, a behaviour, a number — not
a category or a hope. Comfort means the question has
not gone deep enough. Skip a question only if an
earlier answer already covers it.

Stage routing: pre-product → Q1, Q2, Q3; has users →
Q2, Q4, Q5; has paying customers → Q4, Q5, Q6;
pure engineering/infra → Q2, Q4 only.

- **Q1 Demand reality:** What is the strongest
  evidence someone actually wants this — not
  interest, not a waitlist signup, but would be
  genuinely upset if it disappeared tomorrow?
  Red flags: "people say it's interesting,"
  waitlist counts, investor excitement. None of
  those are demand. Behaviour, payment, and panic
  when it breaks are.
- **Q2 Status quo:** What are users doing right
  now to solve this, even badly, and what does
  that workaround cost them in time, money, or
  duct-taped tools? If truly nothing exists and
  no one does anything, the problem is probably
  not painful enough.
- **Q3 Desperate specificity:** Name the actual
  human who needs this most — title, what gets
  them promoted, what gets them fired, what keeps
  them up at night. A category ("healthcare
  enterprises", "SMBs") is not a person.
- **Q4 Narrowest wedge:** What is the smallest
  version someone would pay real money for this
  week — not after the platform is built? One
  feature, one workflow, shippable in days.
  "We need the full platform first" is a red
  flag, not a plan.
- **Q5 Observation and surprise:** Have you
  watched someone use this without helping them?
  What did they do that surprised you? Surveys
  lie, demos are theatre, and "as expected"
  means filtered through existing assumptions.
  Users doing something the product was not
  designed for is often the real product.
- **Q6 Future-fit:** If the world looks
  meaningfully different in 3 years, does this
  become more essential or less — and why,
  specifically? "The market is growing" and
  "AI keeps getting better" are not a thesis;
  every competitor can cite them.

Posture during the diagnostic: be direct to the
point of discomfort, take a position on every
answer and state what evidence would change it,
and name common failure patterns plainly
("solution in search of a problem", "interest
equals demand", "waiting until it's perfect").
Do not praise a vague answer into passing.

Escape hatch: if the user says "just do it" or
"skip the questions", ask the 2 most critical
remaining questions for their stage, then proceed.
If they push back a second time, respect it and
proceed. A full skip is allowed only with a fully
formed plan backed by real evidence (users, revenue,
named customers) — and even then, the premise
challenge and alternatives below still run.

### Premise challenge, then alternatives

Before proposing solutions, put premises to the
user for explicit agree/disagree:

1. Is this the right problem, or would a different
   framing yield a dramatically simpler or more
   impactful solution?
2. What happens if we do nothing — real pain or
   hypothetical one?
3. What existing code already partially solves this
   and can be reused?
4. If the deliverable is a new artifact (app, CLI,
   library, package): how will users get it?
   Distribution and a CI/CD path are part of the
   design, or explicitly deferred — not forgotten.

Then generate 2–3 distinct approaches, each with
summary, effort (S/M/L/XL), risk, pros, cons, and
what existing code it reuses. One must be the
**minimal viable** approach (fewest files, smallest
diff, ships fastest). One must be the **ideal
architecture**. One may be creative/lateral.
Recommend one, with a one-line reason mapped to
the user's stated goal — and stop. Do not write
the design doc until the user picks an approach,
even if one approach is clearly winning.

## 2. Review — pre-landing, read-only first

Use before anything ships, on a branch diff against
its base. The pass is read-only: collect findings
first, fix only after the pass is complete, then
re-review. Never edit reviewed source mid-pass.

1. **Branch and base.** Confirm you are not on the
   base branch and that a diff exists against it.
   If there is no diff, there is nothing to review.
2. **Scope drift.** Compare stated intent (brief,
   commits, PR description) with the actual diff.
   Flag scope creep (unrelated files, unrequested
   features or refactors) and missing requirements
   (unaddressed requirements, missing tests,
   partial implementations) before judging code
   quality.
3. **Checklist.** Read this repo's CHECKLIST.md
   and apply it in order: critical findings first,
   then informational. If the checklist cannot be
   read, stop and report that — never proceed
   without it.
4. **Gate scan.** List every edit to tests, CI,
   lint/runner config, snapshots, and golden files
   in the diff. A weakened test, a loosened
   assertion, a skipped check, or a changed
   snapshot is a finding in its own right, not a
   footnote. A partial or unavailable scan is
   missing coverage, never a clean result.
5. **Critical pass.** Read the diff, not just its
   summary. For every finding, sweep sideways:
   grep the same pattern at every other ingress,
   command, and call site, and rate severity on
   the worst sibling. Data loss, a trust-boundary
   bypass, or uncapped spend is forced CRITICAL —
   no lane, dedup, or prior decision downgrades it.
   Keep findings anchored to changed code.
   Before recommending a fix, check current best
   practice for the framework version in use and
   whether a built-in already replaces the
   workaround. Shared-code opportunities count
   only with at least two verified, first-party
   authored call sites in this diff — invented
   future callers do not qualify, and existing
   libraries are reuse targets before extraction.
6. **Fix, then re-review.** Apply fixes, re-run
   the pass on the new candidate, and report what
   remains. A finding is closed only by a fix
   verified in the re-review, not by being
   discussed.

## 3. QA — test, fix, verify

Use on a target: a browser URL, an API route, a
CLI command, a job, a worker, or a webhook. Never
force a browser surface when there is no URL, and
never request credentials in chat.

### Setup

Parse target, tier, mode, and scope from the
request, or ask. Tiers decide which issues get
fixed: **quick** = critical + high only;
**standard** (default) = + medium;
**exhaustive** = + low/cosmetic.
Modes: full, quick, or regression against a prior
report/baseline. On a feature branch without an
explicit scope, test the diff and its adjacent
behaviour.

Check for a clean working tree first. If it is
dirty, stop and offer: commit before QA, stash
and pop after, or abort for manual cleanup — and
execute only the user's choice. Keep every report,
screenshot, and evidence file in a fresh run
directory; never overwrite a previous report.

### Baseline, then triage

Probe the target's surfaces in order: happy paths,
error paths, edge cases, and adjacent behaviour
the change touches. Sort issues by severity and
apply the selected tier; lower-tier issues and
issues not fixable from source (third-party
widgets, infrastructure) are marked deferred,
not silently dropped.

### Fix loop, per issue, in severity order

1. **Diagnose and reproduce.** Record actual
   versus documented behaviour before any edit.
   Modify only the responsible files.
2. **Regression test before repair.** Write the
   test first and prove it fails for the defect,
   not for a bad fixture. Record a value card:
   protects = what it guards; fails_when = what
   makes it fail; why_new = why existing coverage
   does not catch it; seam = none, or the
   production seam it needs (prefer testing at
   the real boundary over adding a seam no
   production caller needs); no_claim = what a
   green test does not prove. Extend an existing
   table or fixture when one covers the boundary
   instead of adding a near-duplicate test.
3. **Minimal fix.** No unrelated refactors or
   features.
4. **Re-test.** Re-run the regression, the
   original failing probe, and the adjacent happy
   path. For browser defects, recheck in the
   browser. A failed or unavailable recheck stays
   unresolved: try one revised minimal fix, else
   classify it reverted.
5. **Classify each issue:** verified (passed
   re-test, with any missing coverage disclosed);
   best-effort (fix applied but not fully
   verifiable, e.g. needs auth state or an
   external service); reverted (regression
   detected or finding unresolved — undo only
   this run's repair, keep the valid regression
   and evidence, mark deferred). Never discard
   the user's changes.
6. **Self-regulation.** Every 5 fixes, and after
   any revert, stop and evaluate: show what has
   been done and ask whether to continue. Stop
   immediately after two reverts, or one edit to
   a file unrelated to the finding, or when fixes
   keep spanning many files or only low issues
   remain. Hard cap: 50 fixes, then stop
   regardless of what remains.

## 4. Ship — integrate, test, review, release

Route, in order: integrate → test and review →
prepare the release → verify frozen content →
push and publish. Advance only after the current
step's gates clear; a repair inserts its own steps
before the still-pending work, never discarding it.

1. **Pre-flight.** Confirm you are on a feature
   branch, not the base branch. Fetch the base,
   inspect the diff stat and untracked files, and
   log. If the fetch fails, stop and restore
   access first.
2. **Merge the base branch before tests.** Then
   run the test suites. A red suite is a stop,
   not a note.
3. **Review.** Run the review workflow above on
   the diff, and the QA workflow on the target
   where it applies. Prior clear reviews never
   replace these gates.
4. **Coverage and plan completion.** Audit test
   coverage of the diff and whether the plan's
   requirements are actually complete, including
   scope drift found in review.
5. **Prepare the release.** Version bump, then
   CHANGELOG entry, then docs audit — on every
   ship, not only on big ones. Docs that describe
   behaviour the diff changed must be updated in
   the same ship.
6. **Verify frozen content.** Re-check the exact
   tree that will be pushed: tests, review, and
   docs all green on that content, not on an
   earlier version of it.
7. **Push and publish — approval only.** Commit
   the verified tree, push, and open or update
   the PR, only after the user approves that exact
   file list and action. Steps that prevent
   duplicate bumps, pushes, or PRs never prevent
   verification — if the content changed, it is
   verified again.

## What was deliberately left out

- Gstack binaries, telemetry, session tokens, and
  review logs. Evidence here is the diff, the test
  run, and the report — not a token.
- GBrain memory, Aside research, Greptile review,
  and Capy sessions. Replaced by memory search,
  browser/web search, and this repo's checklist.
- Apple App Store / TestFlight distribution, and
  any other platform-specific release adapter.
  If a ship needs one, it is a separate, scoped
  step, not part of this workflow.
- The "boil the ocean" completeness principle, as
  a governing rule. See the governing rule above:
  it does not override Karpathy + Ponytail.
