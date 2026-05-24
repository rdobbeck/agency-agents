# CLAUDE.md

Guidance for AI assistants (Claude Code and others) working in this repository.

## What this repository is

**The Agency** (`agency-agents`) is a curated collection of **AI agent persona
definitions** — not application source code. Each agent is a single Markdown
file describing a specialized expert (its identity, mission, rules, workflows,
deliverables, and success metrics). Users copy these files into
`~/.claude/agents/` to activate them in Claude Code, or read them as reference
prompts.

There is **no build, no runtime, no package manager, and no test suite**. The
"product" is the prose and structure of the Markdown files. The only executable
code is a bash linter (`scripts/lint-agents.sh`) that validates agent files.

There are currently **61 agents** across 9 divisions, plus a **NEXUS** strategy
layer that defines how to orchestrate many agents together.

## Repository structure

Agent files live in nine division directories:

| Directory | Division | Count |
|-----------|----------|-------|
| `design/` | UX/UI and creative specialists | 7 |
| `engineering/` | Software development specialists | 8 |
| `marketing/` | Growth and marketing specialists | 11 |
| `product/` | Product management specialists | 3 |
| `project-management/` | PM and coordination specialists | 5 |
| `testing/` | QA and testing specialists | 8 |
| `support/` | Operations and support specialists | 6 |
| `spatial-computing/` | AR/VR/XR specialists | 6 |
| `specialized/` | Unique specialists that don't fit elsewhere | 7 |

Supporting content:

- `strategy/` — **NEXUS** multi-agent orchestration framework. Defines pipeline
  modes (Full / Sprint / Micro), phase playbooks (`playbooks/phase-0` …
  `phase-6`), coordination templates (`coordination/`), and scenario runbooks
  (`runbooks/`). `strategy/QUICKSTART.md` and `strategy/EXECUTIVE-BRIEF.md` are
  the entry points. Note: `strategy/` is listed in the linter's scan dirs, but
  these are narrative documents, not agents — several (e.g. `QUICKSTART.md`,
  `nexus-strategy.md`) intentionally lack agent frontmatter and so report ERRORs
  in a full-repo lint. This is pre-existing and harmless: CI only lints files
  *changed* in a PR, so untouched strategy docs never block. Avoid editing those
  files in a way that newly trips the linter on a PR.
- `examples/` — Worked examples of multiple agents collaborating on one mission.
- `scripts/lint-agents.sh` — The frontmatter/structure validator.
- `.github/workflows/lint-agents.yml` — CI that runs the linter on changed
  agent files in pull requests.
- `README.md` — The public catalog of all agents (kept in sync manually).
- `CONTRIBUTING.md` — The authoritative agent template and style guide.

## Agent file format

Every agent file is Markdown with **YAML frontmatter** followed by the persona
body. The canonical template lives in `CONTRIBUTING.md`; match the structure of
existing files in the same division.

Required frontmatter (enforced by the linter — missing any is a hard ERROR):

```markdown
---
name: Agent Name
description: One-line description of the agent's specialty and focus
color: colorname or "#hexcode"
---
```

Recommended body sections (the linter WARNs if absent — don't introduce new
warnings):

- `## 🧠 Your Identity & Memory`
- `## 🎯 Your Core Mission`
- `## 🚨 Critical Rules You Must Follow`
- Plus: Technical Deliverables, Workflow Process, Communication Style,
  Learning & Memory, Success Metrics, Advanced Capabilities.

The linter specifically greps the body (case-insensitive) for the strings
`Identity`, `Core Mission`, and `Critical Rules`, and warns if the body is under
50 words.

## Conventions

- **File naming**: lowercase, hyphenated, typically prefixed with the division
  name — e.g. `engineering-frontend-developer.md`,
  `marketing-growth-hacker.md`. The prefix convention is not universal
  (`project-management/project-manager-senior.md`, and several files under
  `spatial-computing/` and `specialized/` use a descriptive name without the
  directory prefix). When adding a new agent, follow the dominant pattern in its
  target directory.
- **Personality first**: Agents have a distinct voice and narrow, deep
  specialization. Avoid generic "helpful assistant" phrasing. See the
  CONTRIBUTING.md "Agent Design Principles" for the bar.
- **Concrete deliverables**: Include real, runnable code examples (with language
  tags), templates, and measurable success metrics — not pseudo-code or vague
  guidance.
- **Emoji section headers**: Section headings use emoji prefixes throughout, by
  convention. Match surrounding files. (This is a content style choice in the
  agent files — it does not change the rule that you should not add emojis to
  code or other deliverables unless asked.)
- **Line endings**: `.gitattributes` enforces LF for `.md`, `.yml`, `.yaml`,
  `.sh`. Don't introduce CRLF.

## Working in this repo

Since there's no application to run, "validating a change" means running the
linter and keeping documentation in sync.

**Lint agent files** (run before committing changes to any agent file):

```bash
./scripts/lint-agents.sh                 # lint all agents
./scripts/lint-agents.sh path/to/agent.md  # lint specific files
```

CI (`.github/workflows/lint-agents.yml`) runs the linter only on agent files
changed in a PR. Errors block merge; warnings do not, but avoid adding new ones.

**Keep the README in sync.** `README.md` contains the master catalog table and a
total agent count (currently "61 Specialized Agents"). When you **add, remove,
or rename** an agent, you must also:

1. Add/update its row in the correct division table in `README.md`.
2. Update the agent count in the README "Stats" section.
3. Verify the relative link to the agent file resolves.

The README is maintained by hand — there is no generator — so this is easy to
forget. Treat it as part of the change, not a follow-up.

## Adding a new agent (checklist)

1. Pick the right division directory (or propose a new one).
2. Create `<division>-<agent-name>.md` following the CONTRIBUTING.md template.
3. Include valid frontmatter (`name`, `description`, `color`) and the
   recommended sections (Identity, Core Mission, Critical Rules, etc.).
4. Run `./scripts/lint-agents.sh <your-file>` and resolve all errors.
5. Add the agent to the README catalog table and bump the count.
6. Commit with a clear message (existing history uses imperative style, e.g.
   "Add Accessibility Auditor — Testing Division").

## Git workflow

- Active development branch for this work: `claude/claude-md-docs-ftT9e`.
- Develop and push to the designated branch; do not push to `main` without
  explicit permission.
- Do not open a pull request unless explicitly asked.

## What not to do

- Don't add a build system, dependencies, or `package.json` — this is a
  content repo. (`.gitignore` anticipates future Node/Python tooling, but none
  exists today.)
- Don't strip the emoji-prefixed section headings or the established structure
  from agent files; consistency across the collection is a feature.
- Don't edit an agent file without checking whether the README catalog needs a
  corresponding update.
- Don't commit personal scratch files — `scratch/`, `notes/`, `TODO.md`, and
  `NOTES.md` are gitignored on purpose.
