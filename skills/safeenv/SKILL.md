# SafeEnv — reference note, with guardrails

Source: https://github.com/david-mwas/safeenv (MIT, 2025,
David Mwas). SafeEnv is a web app, built with Go +
React + Tailwind, for securely storing and retrieving
environment variables for a project. There is no SKILL.md
upstream; this file is an original summary for this
collection.

## What it is, and what it is not

- It is an app a user can self-host to manage their
  own project's environment variables through a web
  interface, with authentication and real-time sync
  to its backend.
- It is **not** a skill, **not** a replacement for
  Muse's Secure Vault, and **not** where Muse's own
  secrets go. Keys, tokens, and passwords for Muse's
  work go through the Secure Vault flow, or into the
  product's own local storage (for example, an
  extension popup's local storage) — never into a
  repo, a chat message, or a SafeEnv instance run by
  someone else.
- It is small and unproven in this stack (4 stars at
  check time). Evaluate it before using it for
  anything production: who hosts it, who can read
  the values, how they are encrypted, and how access
  is revoked.

## When it may fit an app being built

Only if the app itself needs a team-facing way to
manage its own environment variables, the user has
chosen to self-host SafeEnv, and the values involved
are that app's config — never Muse's credentials,
never the user's personal accounts.

In that case:

- self-host it; do not use a third-party-hosted
  instance for real secrets
- never commit a `.env` file, a real value, or a
  sample containing a real value
- document where the values live and how they are
  rotated, without writing any value in the docs
- keep the app's config separate from Muse's
  credentials at all times

## Limits

- This file installs nothing and stores nothing.
  Installing or deploying SafeEnv is a separate,
  user-approved step, with its own security review.
- If the choice is between SafeEnv and the Secure
  Vault for Muse's own work, the Secure Vault wins.
  Always.
