# Pre-ship checklist

Check every box with evidence, or write why it does not apply.
A checked box without evidence is not checked.

## Code

- [ ] Every changed line traces to the request (Karpathy surgical)
- [ ] No speculative feature, no single-use abstraction, no new
      dependency for a few lines (Ponytail)
- [ ] No unrelated file "improved" or reformatted
- [ ] Risky logic (branch/loop/parser/money/security) has one
      small test, or a written reason why it cannot
- [ ] Trust-boundary validation, security, accessibility, and
      data-loss handling intact
- [ ] Syntax/format checks pass for every changed file
- [ ] All referenced IDs exist; all new IDs are used
- [ ] No secret, key, token, password, or private identifier in
      the diff, in a comment, or in a sample file

## Research / reference

- [ ] Claims that depend on live state were checked live, with
      source and date, not from a stale snippet
- [ ] Reference-app work is behavioural spec only — no copied
      code, assets, branding, or licensing logic
- [ ] No server, billing, DRM, or paywall cloning

## Diagram (Archify)

- [ ] Planned system diagrammed before building, from the
      brief/plan only — no invented component, table, or call
- [ ] `finalize` receipt passes; failed gates repaired in the
      candidate, not worked around with a hand-drawn SVG
- [ ] Finished system re-diagrammed from the code as built

## Design (web pages)

- [ ] Locked design.md respected (palette, fonts, tokens)
- [ ] No Hallmark Floor failure: contrast, focus-visible,
      reduced motion, no invented facts, phone layout works,
      hero fits 1280x800 without scrolling, no eyebrow /
      tracked-capital labels, no purple-to-blue gradient
- [ ] No invented metric, testimonial, logo, or quote

## Copy

- [ ] Humanizer 26-pattern pass done on user-facing prose
- [ ] Every claim in the copy is supported; nothing invented
- [ ] Seeded/sample data is labelled as such, never as live

## Learn (Hermes learning loop)

- [ ] Memory and past work searched before starting
- [ ] Durable learning, failures, and corrections recorded
      with dates and sources; no secret in memory or a skill
- [ ] Recurring pattern drafted as a skill, or the failing
      skill repaired — proposed, not silently added
- [ ] Superseded claims pruned from active summaries

## Supporting skills

- [ ] Summaries and handoffs keep unfinished work unfinished
      (Pi auto-compact rule)
- [ ] Browser work used Muse's browser by default; any
      BrowserMCP use was explicitly approved for that task
- [ ] No real secret in the diff, in a sample, or in a
      SafeEnv-style config store; Muse's secrets went
      through the Secure Vault, app config is separate
- [ ] Hindsight local, if installed: recall before the task,
      retain after it; if not installed, not assumed done

## Gstack gates (adapted)

- [ ] Office-hours, for a new idea: six forcing questions
      asked one at a time, premises agreed, approach
      picked by the user before any code
- [ ] Review, pre-landing: scope drift checked, gate scan
      of test/CI/config edits done, critical pass with
      sideways sweep, fixes re-reviewed
- [ ] QA: regression test written before each repair,
      minimal fix, re-test, each issue classified
      verified / best-effort / reverted
- [ ] Ship: base merged before tests, version bump,
      CHANGELOG, docs audit, frozen tree verified
      before pushing

## Ship

- [ ] Success criteria from the brief, verified one by one
- [ ] Exact file list prepared for the user's approval
- [ ] Skipped / not checked items and risks listed in the reply
- [ ] Push/publish approval obtained for that exact list
