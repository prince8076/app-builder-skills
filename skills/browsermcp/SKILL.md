# BrowserMCP — capability note, not a default tool

Source: https://github.com/browsermcp/mcp (BrowserMCP, MCP
server for browser automation, package `@browsermcp/mcp`
v0.1.3, adapted from the Playwright MCP server). Docs:
https://docs.browsermcp.io. There is no SKILL.md upstream;
this file is an original summary for this collection.

## What it is

An MCP server + Chrome extension that lets an AI
application automate the user's own browser, using the
user's existing browser profile — so logged-in sessions
stay logged in — instead of launching a fresh browser
instance. Automation runs locally on the user's machine.

## When to use it

Only when Muse's own browser cannot do the job, and
only with the user's explicit approval for that task:

- a task that genuinely needs the user's logged-in
  browser profile, in their own browser, for their own
  account
- a multi-step website interaction that Muse's live
  browser cannot complete

Muse's browser is the default. Do not reach for
BrowserMCP first, and do not install it speculatively.

## Limits, read before using

- Upstream README says this repo **cannot yet be
  built on its own** due to dependencies on utils and
  types from the monorepo where it is developed.
  Install from the published package and docs, not
  by cloning this repo and expecting a build.
- It needs the Chrome extension and the user's browser
  profile. That profile holds logged-in sessions: treat
  it as sensitive, never copy it, never send its
  contents anywhere, and never use it for an account
  the user did not name for that task.
- Never use it to bypass a site's protections,
  paywall, DRM, or bot checks to take data the user
  does not have a right to, and never use it to act
  on someone else's account.
- A sign-in, purchase, or other irreversible step
  still needs the user's approval for that exact
  action, exactly as with Muse's own browser.
- This file installs nothing. Installing BrowserMCP
  is a separate, user-approved step.
