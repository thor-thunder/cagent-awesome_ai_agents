# Entry Format Guide

## Base pattern

```
- [Name](primary_url) - One-sentence description. [| [label](url) ...]
```

- **Name** — the product or project's proper name, capitalised as it brands itself.
- **primary_url** — the most canonical link: usually the GitHub repo, or the official website if there is no public repo.
- **Description** — exactly one sentence ending with a period. No markdown in the sentence. Aim for 1–2 clauses that say *what it is* and *what it does*.
- **Supplementary links** — optional, separated by ` | `. Each is `[label](url)`. Common labels: `github`, `github profile`, `website`, `docs`, `discord`, `demo`, `announcement`, `twitter`, `linkedin`, `npm`, `video`, `research paper`, `landing page`.

## Alphabetical ordering

Entries within a subsection are sorted **case-insensitively by the display name** (the text inside `[…]`). Numbers sort before letters (`01` before `A`).

## Examples from the repo

Minimal entry (website only):
```
- [AnyBiz](https://anybiz.io) - AnyBiz offers AI-driven sales agents that enhance sales strategies through intelligent automation, continuous learning, and hyper-personalization, operating 24/7 without breaks [website](https://anybiz.io)
```

Entry with multiple supplementary links:
```
- [AutoGPT](https://github.com/Significant-Gravitas/AutoGPT) - AutoGPT provides accessible AI tools for building and using AI agents, offering a comprehensive framework including Forge for agent creation, agbenchmark for performance evaluation, a leaderboard for competition, a user-friendly UI, and CLI for seamless integration and management [github](https://github.com/Significant-Gravitas/AutoGPT) | [github profile](https://github.com/Significant-Gravitas)
```

Entry with demo and announcement:
```
- [AgentOps](https://github.com/AgentOps-AI/agentops) - AgentOps aims to improve AI agent development with tools for observability, evaluations, and replay analytics [github](https://github.com/AgentOps-AI/agentops) | [website](https://www.agentops.ai/) | [docs](https://docs.agentops.ai) | [discord](https://discord.gg/mKW3ZhN9p2) | [demo](https://x.com/AlexReibman/status/1772771418780176674)
```

## Common mistakes to avoid

- Do **not** repeat the name at the start of the description ("AutoGPT is…" is fine; "This is AutoGPT…" is not).
- Do **not** include markdown formatting (bold, code) inside the description sentence.
- Do **not** add a trailing period after supplementary links.
- Do **not** omit the primary URL — the `[Name](url)` link is mandatory.
- The `github` supplementary link should point to the specific repo, while `github profile` points to the organisation/user page.
