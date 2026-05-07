# CLAUDE.md — Operating instructions for this repo

This file orients an AI coding assistant (Claude Code or similar) working in
`awesome_ai_agents`. The repo is a curated awesome-list of AI agents — not a
software project. Almost every change is a content edit: adding, updating,
deduping, or relocating an entry in a curated list.

## What this repo is

A community-maintained, Apache-2.0-licensed catalogue of AI-agent tools,
frameworks, datasets, models, courses, and projects. New entries arrive via
pull requests and issues from the community.

The substantive content lives in three companion files alongside this one:

| File | Purpose |
|------|---------|
| [`SKILL.md`](./SKILL.md) | The maintainer skill — the procedure for adding/updating entries — and the canonical curated lists (Using / Learning / Building). |
| [`REFERENCES.md`](./REFERENCES.md) | Event announcements, the contributors roll, sharing copy, and the license note. |
| [`README.md`](./README.md) | Short landing page that points readers at the three files above. |

The legacy "everything in one README" layout has been split: the README is now
a navigation page, the curated lists live in `SKILL.md`, and supporting/social
content lives in `REFERENCES.md`.

## Repository layout

```
.
├── CLAUDE.md         # this file — agent operating instructions
├── SKILL.md          # maintainer skill + curated lists
├── REFERENCES.md     # event, contributors, sharing copy, license note
├── README.md         # landing page with links into the above
├── LICENSE           # Apache 2.0 — do not edit
├── VERSION           # single-line semver, currently 0.0.13
├── .gitignore        # standard Python ignores
└── assets/           # logo + 4 screenshots referenced from SKILL.md
```

## Entry conventions

Every entry in a curated list follows the same shape:

```
- [Name](https://example.com) - One-sentence description.
```

The longer `Repositories` section uses an extended pattern with multiple
trailing reference links separated by ` | `:

```
- [Name](https://example.com) - One-sentence description [github](https://...) | [docs](https://...) | [website](https://...)
```

Contribution guidelines (verbatim from the original README):

- Relevance to AI agents (e.g. category — using agents, learning agents,
  building agents).
- Clear documentation and accessibility (e.g. name + link + 1-sentence
  description).

## Where new entries go

Match the entry to a category inside `SKILL.md`:

- **Using → Applications** — agents end-users can adopt today.
- **Learning → Repositories** — open-source projects to study and run.
- **Learning → Courses** — structured learning material.
- **Building → Benchmarks / Datasets / Deployment / Ethics / Frameworks /
  LLM Models / Prompt Engineering / Security / Testing / Tools / Workflows** —
  building blocks for developers.

Insert in alphabetical order under the chosen H3 heading.

## Contributors and version

- New PR contributors are appended to the **Pull Request Contributors** list
  in `REFERENCES.md` as `- [@handle](https://github.com/handle) — <Project>`.
- New issue contributors go under **Issue Contributors** as
  `- [@handle](https://github.com/handle) — <Project> ([#NN](issue-url))`.
- `VERSION` is a single-line semver. Bump the patch component on a meaningful
  addition (new entry); bump minor for a new section or batch addition.

## Branch / PR rules

- Develop on a feature branch off `main`.
- Open PRs against `main`. Drafts are fine while iterating.
- Do not modify `LICENSE`, and do not push directly to `main`.
- Hooks and signing settings should be left as the user has configured them —
  do not pass `--no-verify` or `--no-gpg-sign`.

## Quick checklist before committing a list change

1. Entry lives under the correct H3 inside `SKILL.md`.
2. Format matches the convention exactly (`- [Name](url) - sentence.`).
3. Alphabetical position is correct within the section.
4. Contributor is recorded in `REFERENCES.md` if new.
5. `VERSION` bumped if the change warrants it.
6. No duplicate entry already exists (search by name and by URL host).
