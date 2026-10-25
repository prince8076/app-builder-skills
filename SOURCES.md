# Sources and licences

Each skill in `skills/` keeps its upstream licence. All six
upstreams are MIT. This repo does not claim authorship of
those skills; it only collects them, with a workflow that
uses them together, and adds its own AGENTS.md, docs, and
templates.

| Skill in this repo | Upstream | Licence | Version noted |
| --- | --- | --- | --- |
| agent-reach | https://github.com/Panniantong/agent-reach | MIT | 1.6.0 |
| reap (REA-Prompts) | https://github.com/JoasASantos/REA-Prompts | MIT | README, 2026-10-19 |
| karpathy-guidelines | https://github.com/multica-ai/andrej-karpathy-skills | MIT | CLAUDE.md / SKILL.md |
| ponytail | https://github.com/dietrichgebert/ponytail | MIT | 5.3 |
| hallmark | https://github.com/nutlope/hallmark | MIT | 2.0.0 |
| humanizer | https://github.com/blader/humanizer | MIT | 3.1.0 |

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
- The workflow, AGENTS.md, docs, and templates in this repo
  are new work for this collection, under MIT, unless a
  project that copies this repo says otherwise.
