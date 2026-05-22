# Awesome Agent Skills

> A curated, **opinionated** index of production-tested skills, plugins, and CLAUDE.md packs for AI coding agents — Claude Code, Codex, Cursor, OpenCode, Aider, Gemini CLI, and more.

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![Update Status](https://github.com/ATOM00blue/awesome-agent-skills/actions/workflows/update.yml/badge.svg)](https://github.com/ATOM00blue/awesome-agent-skills/actions/workflows/update.yml)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0--1.0-lightgrey.svg)](LICENSE)

This is **not** a directory dump. Every entry is hand-picked, briefly explained, and tagged with **when to use it** and **when not to use it**. Opinions are explicit, not hidden behind neutral descriptions.

If a skill below looks great but you've found it underwhelming in practice, [open an issue](https://github.com/ATOM00blue/awesome-agent-skills/issues) — that's how this list stays useful.

> **Note on naming**: The community uses "skills", "plugins", "personas", "rules", "instructions" interchangeably. They are all variations of: *some markdown file the agent reads to change its behavior*. This list collects the good ones, regardless of label.

---

## Contents

- [General Coding Behavior](#general-coding-behavior)
- [Language-Specific](#language-specific)
- [Code Review](#code-review)
- [Testing](#testing)
- [Documentation](#documentation)
- [Security](#security)
- [Refactoring & Cleanup](#refactoring--cleanup)
- [Workflow & Process](#workflow--process)
- [Domain-Specific (Frontend, Backend, Data, etc.)](#domain-specific)
- [Token Efficiency](#token-efficiency)
- [Frameworks & Build Systems](#frameworks--build-systems)
- [Skill Authoring (meta)](#skill-authoring-meta)
- [Contributing](#contributing)

---

## General Coding Behavior

These shape how the agent thinks, communicates, and structures work — independent of language.

### `andrej-karpathy-skills` 🌟

- **Repo:** [multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills)
- **What it is:** A single CLAUDE.md derived from Andrej Karpathy's observations on common LLM coding pitfalls (over-eager abstraction, premature generalization, etc.).
- **When to use:** As your default base CLAUDE.md for any project. Pairs well with more specific skills layered on top.
- **When not:** If you're already using a stricter, project-specific guide. Don't blend conflicting "voices."
- **Why it works:** Names anti-patterns the agent actually exhibits (rather than vague "write good code" instructions).

### `obra/superpowers` 🌟

- **Repo:** [obra/superpowers](https://github.com/obra/superpowers)
- **What it is:** A full agentic-skills framework + opinionated software-development methodology.
- **When to use:** If you want a structured spec → plan → implement → verify workflow that the agent follows consistently.
- **When not:** Tiny scripts or one-off changes — the overhead isn't justified.
- **Why it works:** Treats the agent like a junior engineer who needs a process, not a vibe.

### `kiro_planner` (built-in)

- **Where:** Bundled with Kiro CLI as the planner agent role.
- **What it is:** A planning-only persona that produces a step-by-step implementation plan before touching code.
- **When to use:** Multi-file changes where understanding scope first prevents redo loops.
- **When not:** Trivial fixes (typos, single-function edits) — straight-to-execution is faster.

---

## Language-Specific

### Python

- **[NVIDIA/skills](https://github.com/NVIDIA/skills)** — official agent skills published by NVIDIA, includes Python coding conventions and CUDA-aware practices.
- **[Imbad0202/academic-research-skills](https://github.com/Imbad0202/academic-research-skills)** — research workflow (write → review → revise) tuned for Python data work.

### TypeScript / JavaScript

- **[dotnet/skills](https://github.com/dotnet/skills)** — published by Microsoft .NET team but the patterns (strict typing, contract testing, docs-first) port well to TypeScript/Node.
- *Looking for a great pure TS skill — [PR welcome](https://github.com/ATOM00blue/awesome-agent-skills/issues/new).*

### Rust

- *Underserved category. If you maintain a tested Rust CLAUDE.md, please [contribute](#contributing).*

### Go

- *Underserved category. If you maintain a tested Go CLAUDE.md, please [contribute](#contributing).*

### Multi-language

- **[Lum1104/Understand-Anything](https://github.com/Lum1104/Understand-Anything)** — turns a codebase into an interactive knowledge graph the agent can query. Works across most languages via tree-sitter.

---

## Code Review

- **[colbymchenry/codegraph](https://github.com/colbymchenry/codegraph)** — pre-indexed code knowledge graph for Claude Code, Codex, Cursor, OpenCode. Cuts tool calls and tokens dramatically when the agent needs to navigate a codebase.

  > **Honest note:** Adds a ~2k–5k-token graph header to every prompt. Worth it for repos > 10k LOC; overkill for tiny ones.

---

## Testing

- *Looking for a curated test-driven CLAUDE.md. The Anthropic [Claude Code best practices doc](https://www.anthropic.com/engineering/claude-code-best-practices) covers TDD-with-agents but isn't packaged as a skill.*

---

## Documentation

- **[Imbad0202/academic-research-skills](https://github.com/Imbad0202/academic-research-skills)** — academic writing pipeline (research → write → review → revise → finalize). Good template for any technical-writing skill.

---

## Security

- *Underserved category right after the May 2026 GitHub / Nx Console / Mini Shai-Hulud attacks. If you've packaged "do not exfiltrate", "verify dependencies", "treat .env files as untrusted" as a skill, please [contribute](#contributing).*

- **[ATOM00blue/extensionguard](https://github.com/ATOM00blue/extensionguard)** — not a skill, but a CLI you can have your agent call before installing VS Code extensions.

- **[ATOM00blue/safeinstall](https://github.com/ATOM00blue/safeinstall)** — not a skill, but a CLI your agent can wrap around `npm install`.

---

## Refactoring & Cleanup

- *Looking for a "code archaeology" skill — one that has the agent investigate why something exists before refactoring it.*

---

## Workflow & Process

- **[obra/superpowers](https://github.com/obra/superpowers)** — see [General Coding Behavior](#general-coding-behavior). The methodology layer of this is what makes it shine.
- **[anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official)** — Anthropic-managed directory of plugins for Claude Code. The official baseline.

---

## Domain-Specific

### Frontend / UI

- *Underserved. If you have a "design-system aware" skill (knows your tokens, components, accessibility constraints), [contribute](#contributing).*

### Backend / API

- *Underserved.*

### Data / ML

- **[Imbad0202/academic-research-skills](https://github.com/Imbad0202/academic-research-skills)** — research → analysis → publication pipeline.

### Game Development

- *Empty. Open invitation.*

---

## Token Efficiency

The category that exploded in March-May 2026 as Anthropic and OpenAI tightened usage limits.

- **[drona23/claude-token-efficient](https://github.com/drona23/claude-token-efficient)** — a single CLAUDE.md that keeps Claude responses terse on heavy workflows. Drop-in.
- **[colbymchenry/codegraph](https://github.com/colbymchenry/codegraph)** — pre-indexed knowledge graph (covered above). Reduces grep/read tool calls.
- **[ATOM00blue/codemap](https://github.com/ATOM00blue/codemap)** — *(coming soon in this index series)* universal single-file code map for any agent.

> **Anti-pattern alert:** Don't combine multiple "be terse" skills — they conflict and confuse the agent. Pick one.

---

## Frameworks & Build Systems

- *Looking for: framework-specific skills (Next.js, Django, Rails, Bun, Vite). [Contribute](#contributing) if you have one tested in production.*

---

## Skill Authoring (meta)

Resources for writing your own skills:

- **[Anthropic — Claude Code Best Practices](https://www.anthropic.com/engineering/claude-code-best-practices)** — official guide. Read this first.
- **[obra/superpowers — methodology section](https://github.com/obra/superpowers)** — opinionated take on what a "skill" should contain.
- **[andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills)** — minimalist single-file approach worth studying.

### Style guide

A skill is good if:

1. **It names anti-patterns the agent actually exhibits.** Vague "write clean code" advice is ignored.
2. **It includes counter-examples.** "Do this. Don't do that." beats abstract principles.
3. **It is < 500 lines.** Larger skills get the early sections forgotten.
4. **It is project-agnostic.** Project-specific stuff belongs in `AGENTS.md` / `CLAUDE.md` at the project root.
5. **It declares scope.** "This skill is for review, not for implementation" prevents misuse.

---

## Anti-patterns (what NOT to do)

These keep showing up. Don't add them to this list.

- **"You are an expert..."** prompts that are 80% flattery, 20% content. Cut to the content.
- **Massive numbered lists of 20+ rules.** The agent silently drops the back half.
- **Conflicting voices in the same skill.** Pick one tone.
- **Skills that try to do everything.** Better: one skill per concern.
- **Skills that hard-code a specific model.** "Use Claude Opus 4.7" ages badly.
- **Skills that disable safety behaviors.** Hard pass. We don't list those here.

---

## Contributing

Pull requests are very welcome. Quality bar:

- [ ] You've used the skill in a real project, not just read its README.
- [ ] You can describe **when not to use it** (every skill has a downside).
- [ ] It is open-source with a permissive license.
- [ ] No duplicates — search the existing list first.

To submit:

1. Open a PR adding the entry to the right section in this README.
2. Use the existing template:

   ```markdown
   ### [skill-name](https://github.com/owner/repo)

   - **What it is:** _one sentence_
   - **When to use:** _real use case_
   - **When not:** _honest downside_
   - **Why it works:** _1-2 sentences_
   ```

3. If a category is empty (most are right now), highlight that you're filling it.

See [CONTRIBUTING.md](CONTRIBUTING.md) for the full details.

---

## License

This **list itself** is [CC0-1.0](LICENSE) (public domain — copy it, fork it, embed it). The linked skills retain their own licenses.

---

## Why this list exists

The pattern: a viral agent skills repo lands on GitHub trending. Within a week, fifteen "awesome-X-skills" lists appear, each linking the same five popular skills, with no curation, no tagging, no opinion. They become useless after their first week.

This list aims to be the opposite:

- **Hand-curated, not automated.** Every entry was used, not just starred.
- **Opinionated.** "When not to use" is as important as "when to use."
- **Honest about gaps.** The empty sections (Rust, frontend, security) are flagged so contributors know where they're needed.
- **Stays current.** A weekly bot checks for dead links and stale repos.

---

*Maintained by [@ATOM00blue](https://github.com/ATOM00blue). Last meaningful update: 2026-05-22.*
