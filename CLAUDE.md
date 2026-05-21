# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository overview

This is a documentation-only "awesome list" repository — there is no code, no build system, and no test suite. The entire content is `README.md`, a curated, community-maintained directory of AI agent tools, resources, and projects, versioned in `VERSION` (current: `0.0.13`).

## Structure of README.md

The README is organized into three top-level sections:

- **Using** — Applications (consumer and enterprise AI agent products)
- **Learning** — Repositories and Courses for learning about AI agents
- **Building** — Technical resources broken into subsections:
  - Benchmarks, Datasets, Deployment, Ethics, Frameworks, LLM Models, Prompt Engineering, Security, Testing, Tools, Workflows

## Entry format

Every entry follows this pattern:

```
- [Name](primary_url) - One-sentence description [| [resource_label](url) ...]
```

Supplementary links (github, website, docs, discord, demo, etc.) are appended with pipe separators, e.g.:

```
- [AutoGPT](https://github.com/Significant-Gravitas/AutoGPT) - AutoGPT provides accessible AI tools for building and using AI agents... [github](https://github.com/Significant-Gravitas/AutoGPT) | [github profile](https://github.com/Significant-Gravitas)
```

Entries within each subsection are sorted **alphabetically by name**.

## Contributing

When adding a new entry:

1. Place it in the correct subsection under Using, Learning, or Building.
2. Maintain alphabetical order within the subsection.
3. Use the entry format above: name, primary link, one sentence, then supplementary links.
4. Ensure relevance to AI agents (using, learning, or building them).
5. Bump the patch version in `VERSION` (e.g. `0.0.13` → `0.0.14`).

## Assets

`assets/` contains only static images used in the README (`logo.webp`, `1.png`–`4.png`). No changes to assets are expected during normal content maintenance.
