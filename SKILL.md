# Skills registry — `cagent-awesome_ai_agents`

Eight skills live under `.claude/skills/<name>/SKILL.md`. Claude Code auto-discovers them when working in this repo. This file is the human-readable registry: what each skill does, the keywords that auto-trigger it, the keywords that terminate it, and which MCP servers it calls in parallel.

The auto-trigger logic is interpreted by Claude from each skill's `description` (in YAML frontmatter); the explicit keyword lists below are the contract — keep them in sync if you edit a skill.

| # | Skill | Context7 | Coupler.io |
|---|---|:-:|:-:|
| 1 | [`frontend-developer`](.claude/skills/frontend-developer/SKILL.md) | ✅ | — |
| 2 | [`canvas-design`](.claude/skills/canvas-design/SKILL.md) | — | — |
| 3 | [`code-review`](.claude/skills/code-review/SKILL.md) | ✅ | ✅ |
| 4 | [`documentation-generator`](.claude/skills/documentation-generator/SKILL.md) | — | ✅ |
| 5 | [`debugger`](.claude/skills/debugger/SKILL.md) | ✅ | — |
| 6 | [`artifacts-builder`](.claude/skills/artifacts-builder/SKILL.md) | ✅ | — |
| 7 | [`agent-sdk-dev`](.claude/skills/agent-sdk-dev/SKILL.md) | — | — |
| 8 | [`backend-architect`](.claude/skills/backend-architect/SKILL.md) | ✅ | ✅ |

---

## 1. `frontend-developer`

**Purpose** — Build/fix UI in React, Vue, Angular, Svelte, Next.js, Remix. Component architecture, responsive design, performance, state management, accessibility.

```block
auto-trigger: react, vue, angular, svelte, next.js, nextjs, remix, component, frontend, ui, tailwind, css, responsive, accessibility, a11y, wcag, bundle size, core web vitals, lazy load, state management, redux, zustand, jotai, hook, suspense, server component, *.tsx, *.jsx, *.vue, *.svelte
terminate-on: "ship it", "lgtm", "done", "that's enough", dev server renders the change, all type errors cleared, user accepts the patch, user pivots to non-frontend topic
parallel-mcp: Context7
```

## 2. `canvas-design`

**Purpose** — Produce museum-quality single-page PDF/PNG artwork, philosophy-first. Use only when the user wants design-forward art, not generic UI.

```block
auto-trigger: canvas, poster, art piece, visual art, museum quality, magazine quality, aesthetic, philosophy, design-forward, one-pager, manifesto, pdf artwork, png artwork, illustration, composition, typography poster, branding artwork
terminate-on: "ship it", "that's the one", "done", both <movement>.md and <movement>.{pdf,png} delivered, user approves the visual, user pivots to non-design topic
parallel-mcp: (none)
```

## 3. `code-review`

**Purpose** — Comprehensive review across quality / security / performance / testing / documentation, with concrete fixes. Use after a diff is staged or a PR is open.

```block
auto-trigger: review this, code review, pr review, review the diff, review the changes, "what do you think of", quality check, security review, performance review, /pr-review, branch comparison, "before merging", git diff present
terminate-on: "ship it", "lgtm", "approved", "merge it", all blocker findings addressed and re-checked, user marks review complete, user pivots to a different PR or task
parallel-mcp: Context7, Coupler.io
```

## 4. `documentation-generator`

**Purpose** — Generate developer docs: code-level (functions/methods), API references (endpoints), project-level (README, setup, contribution).

```block
auto-trigger: write docs, generate documentation, document this, readme, api docs, jsdoc, docstring, swagger, openapi, contributing.md, setup guide, onboarding, "explain how to use", "what does this function do", missing docs, undocumented
terminate-on: "ship it", "that's enough", "done", README/docs file written and reviewed, all public surface covered, user accepts the doc, user pivots to coding work
parallel-mcp: Coupler.io
```

## 5. `debugger`

**Purpose** — Root-cause analysis for errors, test failures, unexpected behavior. Five-step methodology: capture → reproduce → localize → fix → verify.

```block
auto-trigger: error, exception, stack trace, traceback, fails with, broken, "not working", "why is this", regression, flaky, test failing, segfault, "it worked yesterday", undefined is not a function, NullPointerException, panic:, OOM, 500 error, bug, crash
terminate-on: "fixed", "works now", "thanks", regression test added and passing, original reproducer no longer fails, surrounding suite green, user confirms resolution, user pivots to a different bug or feature
parallel-mcp: Context7
```

## 6. `artifacts-builder`

**Purpose** — Build single-file HTML artifacts for Claude.ai using React + TS + Vite + Tailwind + shadcn/ui, then bundle to one portable HTML file.

```block
auto-trigger: claude artifact, html artifact, single-file html, react widget, interactive demo, shadcn, "build me a", "make me a", "interactive page", "self-contained ui", "one html file", parcel bundle, vite scaffold
terminate-on: "ship it", "that's it", "done", bundled index.html opens correctly in a fresh tab, user accepts the artifact, user pivots to a different task
parallel-mcp: Context7
```

## 7. `agent-sdk-dev`

**Purpose** — Verify and harden Python or TypeScript apps that use Anthropic's Claude Agent SDK. Eight verification dimensions, PASS / WARN / FAIL output.

```block
auto-trigger: claude-agent-sdk, @anthropic-ai/claude-agent-sdk, agent sdk, "is my agent setup correct", agent verifier, anthropic agent, ANTHROPIC_API_KEY, MCP server config in agent code, "verify my agent", system prompt review, tool-use loop, agent permissions
terminate-on: PASS or PASS WITH WARNINGS or FAIL report delivered, user accepts the report, all blocker findings remediated and re-verified, user pivots away from the SDK
parallel-mcp: (none)
```

## 8. `backend-architect`

**Purpose** — Design APIs, server logic, databases, scalable backend systems. Six areas: API design, DB architecture, system patterns, security, perf/scale, DevOps.

```block
auto-trigger: api design, rest api, graphql, grpc, schema design, database design, indexing, n+1, microservices, monolith, event sourcing, cqrs, serverless, queue, kafka, redis, oauth2, jwt, rate limit, "how should i structure", "scale this", capacity planning, slo, sla, terraform, ci/cd, "production architecture"
terminate-on: "approved", "ship it", "done", architecture document delivered and accepted, first slice implemented and verified, user accepts the design, user pivots to a different concern
parallel-mcp: Context7, Coupler.io
```

---

## How parallel MCP works

When a skill marked `Context7` or `Coupler.io` activates, its body instructs Claude to issue the corresponding MCP tool calls in the **same tool-use block** as its main investigation tools. This means a single user request fans out to (a) the main work and (b) authoritative external context in one round trip — no sequential round trips, no stale training-era memory.

- **Context7 MCP** (server `4197a4f1-…`) — `mcp__context7__resolve-library-id` + `mcp__context7__get-library-docs`. Use for library/framework API surface.
- **Coupler.io MCP** (server `4467290b-…`) — `mcp__coupler__list-skills` + `mcp__coupler__get-skill`. Use for data-pipeline / dataset / integration ground truth.

## Termination semantics

`terminate-on` keywords are signals to **exit the skill cleanly and return to the default agent loop** — they're not hard kill switches. If the user says "done" but the work clearly isn't finished, ask before stopping. If the deliverable is met (e.g. tests pass, file written, fix verified), terminate even without an explicit keyword.

---

*All 8 skills adapted from [`ComposioHQ/awesome-claude-plugins`](https://github.com/ComposioHQ/awesome-claude-plugins).*
