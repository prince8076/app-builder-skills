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

## Ship

- [ ] Success criteria from the brief, verified one by one
- [ ] Exact file list prepared for the user's approval
- [ ] Skipped / not checked items and risks listed in the reply
- [ ] Push/publish approval obtained for that exact list
