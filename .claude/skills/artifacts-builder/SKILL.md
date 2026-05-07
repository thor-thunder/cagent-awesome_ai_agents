---
name: artifacts-builder
description: Build sophisticated single-file HTML artifacts for Claude.ai using React + TypeScript + Vite + Tailwind + shadcn/ui, then bundle into one self-contained HTML file. Use when the user asks for a Claude artifact, an interactive single-page demo, or a portable React widget.
---

## Activation

```block
auto-trigger: claude artifact, html artifact, single-file html, react widget, interactive demo, shadcn, "build me a", "make me a", "interactive page", "self-contained ui", "one html file", parcel bundle, vite scaffold
terminate-on: "ship it", "that's it", "done", bundled index.html opens correctly in a fresh tab, user accepts the artifact, user pivots to a different task
parallel-mcp: Context7
```

## Always run in parallel with Context7

Whenever this skill activates, in the same tool-use block also call:

1. `mcp__context7__resolve-library-id` for every library in play: react, vite, parcel, tailwindcss, shadcn-ui, plus any extras the user requests (recharts, framer-motion, three.js, etc.).
2. `mcp__context7__get-library-docs` to fetch authoritative usage — shadcn/ui component APIs and Tailwind 3.4.1 utilities especially drift across versions.

Cite library + version when picking APIs; don't guess at component prop shapes.

## Stack (fixed)

- React 18 + TypeScript
- Vite (dev) + Parcel (bundling)
- Tailwind CSS 3.4.1
- shadcn/ui (40+ components pre-installed by the init script)
- Path aliases configured

## Four-step workflow

### 1. Initialize
Run the init script to scaffold the frontend repo. The result has React+TS, Tailwind 3.4.1, path aliases, the shadcn/ui component library, and Parcel bundling configured.

### 2. Develop
Build the artifact. Use shadcn/ui primitives. Compose, don't reinvent. Run `vite` for hot reload during development.

### 3. Bundle
Run the bundling script to inline all JS, CSS, and dependencies into a single `index.html`. The output is portable and pasteable into Claude.ai's artifact panel.

### 4. Share
Hand the user the single HTML file (or its contents).

## Design rules — avoid AI slop

Do **not** ship:
- Excessive centered layouts.
- Purple gradients (especially purple-to-pink).
- Uniform rounded corners on every element.
- Inter as the default font.
- Default shadcn-out-of-the-box look without intentional design choices.

Make deliberate typographic, spacing, and color decisions. Reach for distinctive — not generic.

## Optional testing

Playwright or Puppeteer are available but optional. Prefer presenting the artifact first; add tests only if the user asks for stability guarantees.

## Workflow

1. Read the user's brief; clarify visual direction if it's underspecified.
2. Fire Context7 lookups for every library you'll use (especially shadcn components by name).
3. Initialize → develop → bundle → ship.
4. Verify the bundled HTML opens correctly in a fresh browser tab before delivering.

## Tools

`Bash` (init / dev / bundle scripts), `Read`, `Write`, `Edit`, `Glob`, `Grep`, plus Context7 MCP tools (parallel, always).

---
*Adapted from `ComposioHQ/awesome-claude-plugins/artifacts-builder/skills/artifacts-builder/SKILL.md`.*
