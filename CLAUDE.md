# CLAUDE.md

I am an autonomous agent.

## What this repo is

A curated list of AI agents (`README.md`), forked from `jim-schwoebel/awesome_ai_agents`. The repo also ships **8 Claude Code skills** under `.claude/skills/<name>/SKILL.md`, each adapted from `ComposioHQ/awesome-claude-plugins`. Every skill carries its own activation contract — `auto-trigger` keywords, `terminate-on` keywords, and `parallel-mcp` servers — in a `## Activation` block at the top of its `SKILL.md`.

## Compose multiple skills per command

Skills are **not mutually exclusive** — combine them. **For bigger projects, activate 3–5 skills in a single command** so build, debug, knowledge retrieval, and fix happen in one orchestrated flow rather than serial round-trips.

Example combinations:

- **Build + debug + read knowledge + fix** — `frontend-developer` + `debugger` + `documentation-generator` + `code-review`. Use when the request is "build this feature, fix what breaks, ground decisions in docs, review the diff before commit."
- **Architect + build + verify + review** — `backend-architect` + `agent-sdk-dev` + `code-review`. Use for "design this Agent SDK service, implement it, then review."
- **Artifact + design + docs** — `artifacts-builder` + `canvas-design` + `documentation-generator`. Use for "build a Claude artifact with intentional visual design and a setup README."
- **Debug + architect + review** — `debugger` + `backend-architect` + `code-review`. Use for "this query is slow — diagnose, redesign the data layer, review the migration."
- **Full stack** — `frontend-developer` + `backend-architect` + `debugger` + `code-review` + `documentation-generator`. Use when shipping an end-to-end feature.

When skills compose, **their parallel-MCP blocks compound** — Context7 and Coupler.io fire in the same tool-use block whenever at least one active skill requires them. One round trip, all context.

## Routing summary

| Skill | When to apply |
|---|---|
| `frontend-developer` | UI work in React/Vue/Angular/Svelte/Next.js/Remix; components, perf, a11y, state |
| `canvas-design` | Museum-quality single-page PDF/PNG art (philosophy-first); not generic UI styling |
| `code-review` | Diff staged or PR open; quality / security / perf / tests / docs feedback |
| `documentation-generator` | READMEs, API refs, function/method docs, contribution guides |
| `debugger` | Stack traces, test failures, regressions — root cause, not symptoms |
| `artifacts-builder` | Single-file HTML artifacts for Claude.ai (React + TS + Vite + Tailwind + shadcn) |
| `agent-sdk-dev` | Code imports `claude-agent-sdk` (Py) or `@anthropic-ai/claude-agent-sdk` (TS) |
| `backend-architect` | API design, DB design, scaling, auth, capacity / cost tradeoffs |

Exact triggers + termination keywords live in the `## Activation` block at the top of each `.claude/skills/<name>/SKILL.md`. Read those before activating.

## Parallel MCP — never skip

When any active skill says "Always run in parallel with Context7" or "…with Coupler.io", issue those MCP tool calls **in the same tool-use block** as the main investigation tools (Read / Grep / Glob / Bash). Not after. Same block.

- **Context7** — `mcp__context7__resolve-library-id` + `mcp__context7__get-library-docs`. Library/framework API truth; never rely on training memory.
- **Coupler.io** — `mcp__coupler__list-skills` + `mcp__coupler__get-skill`. Data-pipeline / dataset / integration ground truth.

## Termination

Each skill's `terminate-on:` keywords are **soft** signals — exit the skill cleanly and return to default behavior, not a hard kill. If the user says "done" but work clearly isn't finished, ask first. If the deliverable is met (test passes, fix verified, file written, doc accepted), terminate even without an explicit keyword. Multi-skill composes terminate independently — frontend-developer can finish while debugger keeps running.
