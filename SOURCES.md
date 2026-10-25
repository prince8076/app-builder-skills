# Sources and licences

Each skill in `skills/` keeps its upstream licence. Six
upstreams are MIT; Archify is Apache-2.0. This repo does not
claim authorship of those skills; it only collects them, with
a workflow that uses them together, and adds its own AGENTS.md,
docs, and templates.

| Skill in this repo | Upstream | Licence | Version noted |
| --- | --- | --- | --- |
| agent-reach | https://github.com/Panniantong/agent-reach | MIT | 1.6.0 |
| reap (REA-Prompts) | https://github.com/JoasASantos/REA-Prompts | MIT | README, 2026-10-19 |
| karpathy-guidelines | https://github.com/multica-ai/andrej-karpathy-skills | MIT | CLAUDE.md / SKILL.md |
| ponytail | https://github.com/dietrichgebert/ponytail | MIT | 5.3 |
| hallmark | https://github.com/nutlope/hallmark | MIT | 2.0.0 |
| archify | https://github.com/tt-a1i/archify | Apache-2.0 | 3.2 |
| humanizer | https://github.com/blader/humanizer | MIT | 3.1.0 |
| hermes-learning-loop | Inspired by https://github.com/NousResearch/hermes-agent | — (original text for this collection) | Loop adapted 2026-10-25 |
| pi-auto-compact | https://github.com/tmustier/pi-auto-compact | MIT | Deprecated/archived; reference note only, no upstream SKILL.md |
| browsermcp | https://github.com/browsermcp/mcp | MIT (package @browsermcp/mcp 0.1.3) | Capability note only, no upstream SKILL.md, nothing installed |
| safeenv | https://github.com/david-mwas/safeenv | MIT | Reference note only, no upstream SKILL.md, nothing installed/stored |
| hindsight-local | https://github.com/vectorize-io/hindsight | MIT | Local skill, verbatim upstream SKILL.md (111 lines) |

Notes:

- Karpathy guidelines are derived from Andrej Karpathy's
  observations on LLM coding pitfalls, not written by Karpathy
  himself. The upstream author is forrestchang / multica-ai.
- Hallmark's photo library (upstream) lists photographs hosted
  on Wikimedia Commons under their own licences (CC0, public
  domain, CC BY, CC BY-SA). No photos are bundled in this repo.
- agent-reach: install from the GitHub release only, never
  from PyPI — the PyPI package of the same name is not this
  project. Hallmark: install the full skill via
  `npx skills add nutlope/hallmark -g` when you need its
  themes, references, and scripts; only its SKILL.md is
  bundled here.
- archify: unlike the two above, its SKILL.md alone cannot
  render — it needs its `bin/`, `schemas/`, `renderers/`, and
  `references/` beside it, so the full working package is
  bundled (191 files, `node bin/archify.mjs doctor` passes
  on the bundled copy). Only the rendered HTML example
  outputs are left out; they are regenerable with `finalize`.
- hermes-learning-loop: NOT an upstream skill text and NOT
  Hermes Agent. It is one original SKILL.md written for
  this collection, adapting Hermes' learning loop
  (search past work, capture learning, create and improve
  skills in use, persist knowledge) to this repo's workflow.
  No Hermes code, prompt, skill, gateway, or runtime is
  bundled, and Hermes is not installed by copying this repo.
- pi-auto-compact, browsermcp, safeenv: original summary
  notes written for this collection — none of the three
  has an upstream SKILL.md, and none is installed by
  copying this repo. Pi auto-compact is deprecated and
  archived; BrowserMCP cannot be built from its repo
  alone (monorepo dependencies); SafeEnv is a small,
  unproven web app, not a secret store for Muse.
- hindsight-local: the one verbatim upstream skill in
  this batch, MIT, from vectorize-io/hindsight's
  `skills/hindsight-local/SKILL.md`. It assumes
  `hindsight-embed` is installed and configured with an
  LLM provider; that setup and any API key are separate
  user-approved steps, never in this repo. Cloud and
  self-hosted Hindsight skills were deliberately not
  bundled — local only, matching this stack's
  local-first rule.
- The workflow, AGENTS.md, docs, and templates in this repo
  are new work for this collection, under MIT, unless a
  project that copies this repo says otherwise.
