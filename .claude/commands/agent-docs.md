Help the user work with this awesome AI agents list. $ARGUMENTS

You have access to detailed supporting docs in `.claude/agent-docs/`:
- `sections.md` — every section and subsection with descriptions of what belongs there
- `format.md` — entry format rules, link label conventions, and real examples

## When adding a new entry

1. Read `.claude/agent-docs/sections.md` to determine the correct subsection.
2. Read `.claude/agent-docs/format.md` for the exact format to use.
3. Insert the entry in alphabetical order within that subsection in `README.md`.
4. Bump the patch version in `VERSION` (e.g. `0.0.13` → `0.0.14`).
5. Commit both files together.

## When the user asks where something belongs

Read `.claude/agent-docs/sections.md` and explain which section fits and why.

## When the user asks about the entry format

Read `.claude/agent-docs/format.md` and show them the relevant rule or example.
