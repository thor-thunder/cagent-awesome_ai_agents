# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository overview

This is a documentation-only "awesome list" repository — there is no code, no build system, and no test suite. The entire content is `README.md`, a curated, community-maintained directory of AI agent tools, resources, and projects. The current patch version is tracked in `VERSION`.

## Structure of README.md

The README is organized into three top-level sections:

- **Using** — Applications (consumer and enterprise AI agent products)
- **Learning** — Repositories and Courses for learning about AI agents
- **Building** — Technical resources broken into subsections:
  - Benchmarks, Datasets, Deployment, Ethics, Frameworks, LLM Models, Prompt Engineering, Security, Testing, Tools, Workflows

## Entry format

Every entry follows this pattern:

```
- [Name](primary_url) - One-sentence description. [label](url) | [label](url)
```

The description is followed by optional supplementary links (github, website, docs, discord, demo, etc.) separated by ` | `. Example:

```
- [AutoGPT](https://github.com/Significant-Gravitas/AutoGPT) - AutoGPT provides accessible AI tools for building and using AI agents, offering Forge for agent creation, agbenchmark for performance evaluation, and a user-friendly UI. [github](https://github.com/Significant-Gravitas/AutoGPT) | [github profile](https://github.com/Significant-Gravitas)
```

Entries within each subsection are sorted **alphabetically by name**.

## Contributing

When adding a new entry:

1. Place it in the correct subsection under Using, Learning, or Building.
2. Maintain alphabetical order within the subsection.
3. Use the entry format above: name, primary link, one sentence, then supplementary links.
4. Ensure relevance to AI agents (using, learning, or building them).
5. Bump the patch version in `VERSION` (e.g. `0.0.13` → `0.0.14`).

## Skill: `/agent-docs`

A project slash command is available at `.claude/commands/agent-docs.md`. Invoke it with `/agent-docs` (optionally with a description of what you want to do) to get step-by-step guidance on adding entries, finding the right section, or formatting correctly.

Supporting reference files live in `.claude/agent-docs/`:
- `sections.md` — every section/subsection with descriptions and a decision table for placement
- `format.md` — full entry format spec, link-label conventions, and copy-paste examples

## Assets

`assets/` contains only static images used in the README (`logo.webp`, `1.png`–`4.png`). No changes to assets are expected during normal content maintenance.
