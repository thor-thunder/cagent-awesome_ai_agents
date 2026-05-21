# Section Guide

Use this to decide where a new entry belongs in `README.md`.

---

## Using (line ~100)
Consumer and enterprise AI agent products people can use today.

### Applications (line ~106)
End-user AI agent products across any category: coding assistants, personal assistants, sales agents, research tools, voice agents, browser agents, etc. This is the largest section. When in doubt whether a product is "usable" rather than a framework/tool, put it here.

---

## Learning (line ~168)
Resources for growing AI agent skills.

### Repositories (line ~176)
GitHub repositories, open-source projects, and research codebases that are primarily educational or demonstrative — good for learning how agents work. Includes agent frameworks that have a strong learning/reference angle (e.g. AutoGPT, BabyAGI, LangChain).

### Courses (line ~484)
Structured learning resources: online courses, tutorials, curricula, MOOCs.

---

## Building (line ~511)
Technical infrastructure for developing AI agents.

### Benchmarks (line ~516)
Datasets and frameworks for evaluating LLM/agent performance. Includes leaderboards.

### Datasets (line ~570)
Raw data collections used for training, fine-tuning, or evaluating LLMs and agents.

### Deployment (line ~675)
Platforms, infrastructure, and tooling for hosting and serving AI agents in production. Includes cloud services, model-serving platforms, containerisation helpers.

### Ethics (line ~830)
Resources on responsible AI, alignment, safety principles, bias, fairness, and governance.

### Frameworks (line ~991)
Libraries and SDKs used to *build* agents programmatically (LangChain, LlamaIndex, CrewAI, AutoGen, etc.). Distinguished from Applications (end-user products) and Tools (single-purpose utilities).

### LLM Models (line ~1031)
Foundation models and model APIs that power agents: GPT, Claude, Gemini, Llama, Mistral, open-source weights, etc.

### Prompt Engineering (line ~1154)
Techniques, guides, papers, and tools focused on crafting effective prompts (CoT, few-shot, ReAct, etc.).

### Security (line ~1244)
Resources on AI security: prompt injection defences, jailbreak research, red-teaming, guardrails, PII protection.

### Testing (line ~1291)
Tools and frameworks for testing AI agent behaviour, output quality, and reliability.

### Tools (line ~1431)
Single-purpose utilities that agents use or that assist agent development: memory stores, vector databases, search APIs, TTS/STT, code execution sandboxes, observability dashboards.

### Workflows (line ~1629)
Automation and orchestration tools: workflow engines, no-code/low-code pipeline builders, GitHub Actions, Zapier-style platforms.

---

## Decision guide

| The thing is… | Put it in… |
|---|---|
| A product users log into / install | Using → Applications |
| A GitHub repo that teaches agent concepts | Learning → Repositories |
| A course or tutorial series | Learning → Courses |
| A library you `pip install` to build agents | Building → Frameworks |
| A foundation model or model API | Building → LLM Models |
| A cloud hosting / serving platform | Building → Deployment |
| A dataset for training or eval | Building → Datasets |
| A benchmark or leaderboard | Building → Benchmarks |
| A prompt guide or technique paper | Building → Prompt Engineering |
| A security/safety tool or paper | Building → Security |
| A testing/eval library | Building → Testing |
| A single-purpose utility (memory, search, TTS…) | Building → Tools |
| A workflow/automation platform | Building → Workflows |
