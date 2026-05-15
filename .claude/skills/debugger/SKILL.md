---
name: debugger
description: Systematic root-cause analysis for errors, test failures, and unexpected behavior. Use when something is broken and you need a real fix, not a symptom mask.
---

## Activation

```block
auto-trigger: error, exception, stack trace, traceback, fails with, broken, "not working", "why is this", regression, flaky, test failing, segfault, "it worked yesterday", undefined is not a function, NullPointerException, panic:, OOM, 500 error, bug, crash
terminate-on: "fixed", "works now", "thanks", regression test added and passing, original reproducer no longer fails, surrounding suite green, user confirms resolution, user pivots to a different bug or feature
parallel-mcp: Context7
```

## Always run in parallel with Context7

Whenever this skill activates, in the same tool-use block also call:

1. `mcp__context7__resolve-library-id` for every library implicated by the stack trace, error message, or failing test (the framework, the assertion library, the runtime, the dep that throws).
2. `mcp__context7__get-library-docs` to confirm behavior — known issues, version-specific bugs, expected exception shapes.

Don't guess at library internals; pull docs in parallel with the investigation.

## Five-step methodology

### 1. Capture
- Error message verbatim.
- Full stack trace.
- Environment: language version, key dep versions, OS, runtime mode (dev/prod/test).
- Recent changes: `git log --oneline -20`, `git diff HEAD~1`.

### 2. Reproduce
- Find or write the smallest input that triggers the failure deterministically.
- If the bug is flaky, instrument enough to make it deterministic before fixing.
- Confirm it reproduces on a clean checkout.

### 3. Localize
- Read the failing line and 50 lines around it with `Read`.
- Use `Grep` to follow the call chain backward from the throw site.
- Form a falsifiable theory of what's wrong, not a vibe.

### 4. Fix minimally
- The smallest change that addresses the root cause.
- No drive-by refactors, no "while I'm here" cleanup, no defensive guards for impossible states.
- If two roots are tangled, fix one per change.

### 5. Verify
- Re-run the original reproducer; confirm it now passes.
- Run the surrounding test suite to catch regressions.
- Add a regression test that would have caught this bug.

## Diagnostic moves

- `console.log`/`print` ladders are fine in the heat of debugging — remove them in the final patch.
- Bisect: `git bisect` when "it worked yesterday".
- Inspect variable values at the failure point, not assumptions.
- Read library source via Context7 docs when behavior contradicts your model.

## Deliverable shape

For each diagnosed issue, report:
1. **Root cause** — what's actually wrong, in one sentence.
2. **Evidence** — the trace / log / test output that proves it.
3. **Fix** — the patch (file:line + replacement).
4. **Verification** — exact commands run and their output.
5. **Prevention** — regression test added; or process change to avoid the class of bug.

Address the underlying issue, never just the symptom.

## Tools

`Read`, `Edit`, `Bash`, `Grep`, `Glob`, plus Context7 MCP tools (parallel, always).

---
*Adapted from `ComposioHQ/awesome-claude-plugins/debugger/agents/debugger.md`.*
