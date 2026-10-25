# app-builder-skills

One repo, twelve skills, used for every app we build.

This is not a framework and not a code library. It is the working
agreement: how research is done, how a reference app is studied, how
code is written, how a system is diagrammed, how a page is designed, how copy is written, and how what is learned is kept —
before, during, and after building.

Copy this repo (or its `AGENTS.md`) into a new app project, fill in
`templates/APP_BRIEF.md` and `templates/design.md`, and follow
`docs/APP_WORKFLOW.md` in order. Do not skip a step because it is
familiar, and do not add a step nobody asked for.

## The twelve skills

| Skill | What it does | When it runs | Source |
| --- | --- | --- | --- |
| agent-reach | Live research: search and read GitHub, YouTube, Bilibili, V2EX, Reddit, X, Xiaohongshu, and more, one CLI, read-only, zero API fees | Research, before building | https://github.com/Panniantong/agent-reach |
| REAP (REA-Prompts) | Paste-ready prompts for REA reverse engineering: one feature per prompt, file/function/address evidence, fact vs inference vs unknown | Studying a reference app, clean-room only | https://github.com/JoasASantos/REA-Prompts |
| Karpathy guidelines | Think before coding, simplicity first, surgical changes, goal-driven execution with verifiable success criteria | Every code change | https://github.com/multica-ai/andrej-karpathy-skills |
| Ponytail | Smallest complete change, reuse ladder, never cut security or trust-boundary validation, one small test for risky logic | Every code change | https://github.com/dietrichgebert/ponytail |
| Hallmark | Anti-AI-slop design: hard Floor, Reflex gates, Finish checks, sloplint, hero first, fresh-context review | Web pages only, audit-first for existing designs | https://github.com/nutlope/hallmark |
| Archify | Validated architecture, workflow, sequence, data-flow, lifecycle, ERD, class, tree, timeline, and waterfall diagrams as standalone HTML, plus one-page explainers | Diagram the planned system before building, and the finished system for docs | https://github.com/tt-a1i/archify |
| Humanizer | Remove signs of AI writing (26 patterns), keep every supported claim, never invent a fact | User-facing prose only | https://github.com/blader/humanizer |
| Hermes learning loop | Search memory first, capture durable learning, turn a recurring pattern into a skill, improve skills in use, prune what is superseded | After every build, before shipping | Inspired by https://github.com/NousResearch/hermes-agent — loop only, no Hermes code or runtime bundled |
| Pi auto-compact | Never let a summary make unfinished work sound finished; keep every pending check, blocker, and unresolved question | Every summary and handoff, in long sessions | https://github.com/tmustier/pi-auto-compact — deprecated, archived, Pi 0.86+ native; reference note only, nothing installed |
| BrowserMCP | Automate the user's own logged-in browser via MCP, only when Muse's browser cannot do the job | Browser tasks needing the user's own profile, with explicit approval | https://github.com/browsermcp/mcp — capability note only, nothing installed |
| SafeEnv | Self-hosted web app for managing a project's environment variables, with guardrails | An app's own config only, never Muse's secrets | https://github.com/david-mwas/safeenv — reference note only, nothing installed or stored |
| Hindsight local | Retain / recall / reflect: store learnings and recall context before tasks, via a local Hindsight bank | Memory, alongside the Hermes loop, once Hindsight is installed | https://github.com/vectorize-io/hindsight — local skill only, not cloud or self-hosted server |

Full skill texts are in `skills/`. Each skill keeps its own upstream
licence (six MIT, Archify Apache-2.0); the Hermes learning-loop
skill is original work for this collection, inspired by Hermes,
not an upstream text. See `SOURCES.md`.

Notes, learned the hard way:

- agent-reach and Hallmark are larger systems than their SKILL.md
  files. The SKILL.md here is the entry point. Install the full tool
  from upstream when you need its references, themes, or scripts:
  agent-reach via `uv tool install` from its GitHub release (never
  PyPI — the PyPI package of the same name is not this project);
  Hallmark via `npx skills add nutlope/hallmark -g` (Node 18+;
  render checks also need puppeteer-core + Chrome).
- In this Muse VM, agent-reach GitHub + V2EX work; YouTube/Bilibili
  fail on SSL/cert errors and web search timed out. Fall back to
  browser/social search there.
- Hallmark is never used to re-theme an existing design unless the
  user names Hallmark. A locked `templates/design.md` overrides
  themes. For an existing page, Hallmark runs as audit first.
- Archify is the exception to the entry-point rule: its SKILL.md
  alone cannot render anything — it needs its `bin/`, `schemas/`,
  `renderers/`, and `references/` next to it. So `skills/archify/`
  is the full working package (191 files, verified with
  `node bin/archify.mjs doctor`), with only the rendered HTML
  example outputs left out — they are regenerable with
  `finalize`, and they were 13 MB of the upstream 18 MB.
  Diagrams go through `finalize`'s validation gates; a
  hand-drawn SVG is not a substitute when Archify is available.

## How to use this repo for a new app

1. Read `AGENTS.md`. It is the short version of all twelve skills.
2. Fill in `templates/APP_BRIEF.md` — job, audience, material,
   platform, what is out of scope. If an answer is unknown, write
   UNKNOWN, do not guess.
3. Follow `docs/APP_WORKFLOW.md` in order: research → study →
   plan → diagram → build smallest → design check → copy check
   → verify → learn → ship (only with approval). The four
   newest skills are supporting, not new steps: Pi
   auto-compact guards every summary, BrowserMCP is a
   fallback browser tool, SafeEnv covers an app's own
   config, Hindsight local backs the learn step.
4. Use `docs/CHECKLIST.md` before any push or release.
5. End every coding reply with: what was skipped or not checked,
   and any risk the user must know. A known shortcut gets a
   `shortcut: <limit>, <when to upgrade>` comment in code.

## Boundaries (non-negotiable)

- Clean-room only for reference apps: behaviour, never copied code,
  assets, branding, or licensing mechanisms. Never clone a
  server-side system, accounts/billing, DRM, or paywalls.
- REAP sections on anti-cheat, DMA, and cracking are
  defensive/research only. Never use them to bypass a protection.
- Humanizer is for human readers. Getting past AI detectors is
  not a goal, and detectors still flag most of its output.
- Never paste a secret in chat. Keys go into the product's own
  local storage (or the user's terminal), never into a repo, a
  message, or memory.
- Never push to a repo, publish, buy, or delete anything
  irreversible without the user's explicit approval for that
  action. A push approval covers exactly the files listed.
- Label seeded, simulated, or sample data as such. Never present
  it as live data.
- Optional/login channels (agent-reach) stay off unless the user
  picks one per channel. Never copy a login without explicit
  approval, and never log in on the user's behalf.
