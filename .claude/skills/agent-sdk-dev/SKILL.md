---
name: agent-sdk-dev
description: Verify and harden Python or TypeScript apps built with Anthropic's Claude Agent SDK. Use when the user is writing, reviewing, or debugging code that imports `claude-agent-sdk` (Python) or `@anthropic-ai/claude-agent-sdk` (TS), or asks whether their agent setup is correct.
---

## Purpose

Comprehensively validate Claude Agent SDK applications: confirm the SDK is installed and current, the integration follows documented patterns, and the app handles real-world failure modes. Prioritize SDK functionality and best practices over generic style concerns (no PEP 8 nits, no import-order religion).

## Eight verification dimensions

1. **SDK installation**
   - Python: `claude-agent-sdk` present in `requirements.txt` / `pyproject.toml`; version current.
   - TS: `@anthropic-ai/claude-agent-sdk` in `package.json`; version current.

2. **Environment setup**
   - Dependency manifest exists and is consistent (`requirements.txt`, `pyproject.toml`, `package.json` + lockfile).
   - Python version / Node version pinned where appropriate.

3. **SDK usage patterns**
   - Imports match the public API surface.
   - Client initialization follows the docs (correct constructor args, defaults overridden intentionally).
   - Tool / agent setup uses documented hooks.

4. **Code quality**
   - Syntax valid; imports resolve.
   - Errors handled at the right boundary (don't swallow, don't blanket-catch).

5. **Security**
   - No hardcoded API keys; `ANTHROPIC_API_KEY` read from env.
   - `.env` files in `.gitignore`.
   - User-provided prompts sanitized when fed into shell / SQL.

6. **Best practices**
   - System prompt is explicit and bounded.
   - Model selection matches the task (Opus for complex reasoning, Sonnet for general, Haiku for fast/cheap).
   - Permissions / tool allowlists scoped tightly.
   - MCP server integration follows the documented config schema.

7. **Functionality**
   - Agent execution flow handles partial failures and retries.
   - Streaming is consumed correctly (no dropped tokens, proper backpressure).
   - Tool-use loops have a termination condition.

8. **Documentation**
   - README covers setup + run.
   - Env vars listed; example `.env.example` present.

## Reference docs

- Python: https://docs.claude.com/en/api/agent-sdk/python
- TypeScript: https://docs.claude.com/en/api/agent-sdk/typescript

Always validate against the official docs, not training-era memory of the SDK.

## Output format

Report status with one of:
- **PASS** — all eight dimensions clean.
- **PASS WITH WARNINGS** — works, but improvements recommended (list them).
- **FAIL** — at least one blocker (list with file:line + fix).

For each finding, give: location, what's wrong, why it matters, exact remediation.

## Tools

`Read`, `Grep`, `Glob`, `Bash` (for `pip show` / `npm ls` / running tests), `Edit` (for fixes when authorized).

---
*Adapted from `ComposioHQ/awesome-claude-plugins/agent-sdk-dev/agents/agent-sdk-verifier-py.md` (Python) and `agent-sdk-verifier-ts.md` (TypeScript).*
