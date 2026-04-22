# Project Library

> One person. One harness. 25 projects.

This is the curated index of everything I've built — structured for adoption, not just browsing. Each project includes what it does, how to use it, and why the architecture works the way it does.

**Builder:** [Marius Jauernik](https://github.com/mj-deving) — AI & Fullstack Engineer, building PAI (Personal AI Infrastructure)

---

## n8n Automation & Code-Mode

Production-grade n8n workflows proving that code-first AI automation cuts token costs by 56-96%.

| Project | What it does | Stack | Key Metric |
|---------|-------------|-------|------------|
| [n8n-speed-to-lead](https://github.com/mj-deving/n8n-speed-to-lead) | AI lead qualification in <30s | n8n, Claude, Slack, Sheets | $0.001/lead |
| [n8n-meeting-intelligence](https://github.com/mj-deving/n8n-meeting-intelligence) | Recording to protocol + action items | n8n, Whisper, Claude | 19s processing |
| [n8n-email-triage](https://github.com/mj-deving/n8n-email-triage) | 7-category email classification | n8n, IMAP, Claude, Slack | 11/11 tests |
| [n8n-self-healing](https://github.com/mj-deving/n8n-self-healing) | Workflow learns from failures | n8n, Claude, Slack | 0 tokens on 4th error |
| [n8n-autopilot](https://github.com/mj-deving/n8n-autopilot) | 6 AI workflows, fully code-first | n8nac, Gemini | Origin project |

**Adopt:** Clone [n8n-project-template](https://github.com/mj-deving/n8n-project-template) to start your own code-first n8n project with n8nac + code-mode + Beads.

---

## Code-Mode Ecosystem (npm packages)

The thesis: replace n8n's AI Agent node with direct code execution. Proven 96% token savings.

| Project | What it does | Downloads |
|---------|-------------|-----------|
| [n8n-nodes-utcp-codemode](https://github.com/mj-deving/n8n-nodes-utcp-codemode) | n8n community node for code-mode | npm |
| [code-mode-tools](https://github.com/mj-deving/code-mode-tools) | CLI + MCP server for code-mode sandbox | npm |
| [n8nac-tools](https://github.com/mj-deving/n8nac-tools) | CLI wrapper for n8nac commands | npm |
| [code-first-n8n](https://github.com/mj-deving/code-first-n8n) | 5 POC workflows, the proving ground | Benchmarked |

**Adopt:** `npm install -g code-mode-tools` to get the CLI + MCP server. Use with any n8n instance.

---

## Code-Mode Production Projects

Real-world applications built on the code-mode foundation, each with measured benchmarks.

| Project | What it does | Stack | Token Savings |
|---------|-------------|-------|--------------|
| [rag-pipeline-factory](https://github.com/mj-deving/rag-pipeline-factory) | Tell it what you want, get a deployed RAG pipeline | n8n, TypeScript | 56% |
| [soc-alert-triage](https://github.com/mj-deving/soc-alert-triage) | Parallel threat intel enrichment | Shodan, MITRE, VT, AbuseIPDB | 86% |

**Adopt:** Fork and customize the enrichment sources for your domain (HR, finance, compliance).

---

## AI Agents & Research

Progressive agent architectures — from single-agent to multi-agent orchestration.

| Project | What it does | Stack | Key Metric |
|---------|-------------|-------|------------|
| [managed-agents-research](https://github.com/mj-deving/managed-agents-research) | 5 progressive agent demos | Claude Agent SDK, Python | 42 tests, $0.42-$1.97/run |
| [langgraph-agent](https://github.com/mj-deving/langgraph-agent) | State machine: plan, research, write, review | LangGraph, FastAPI, Tavily | 16 tests, SSE |
| [crewai-n8n-bridge](https://github.com/mj-deving/crewai-n8n-bridge) | 5 multi-agent crews as REST API | CrewAI, FastAPI, Docker | 54 tests, SSE |
| [voice-agent](https://github.com/mj-deving/voice-agent) | AI phone agent for medical practices | FastAPI, Vapi, Fly.io | 156 tests |
| [rag-hybrid-chatbot](https://github.com/mj-deving/rag-hybrid-chatbot) | Hybrid RAG: Vector + Knowledge Graph + CRAG | Qdrant, NetworkX, Python | 61 tests |
| [agent-playground](https://github.com/mj-deving/agent-playground) | Interactive chat UI for research agents | Next.js 14, SSE | Live demo |

**Adopt:** Start with `managed-agents-research` for agent patterns, `crewai-n8n-bridge` if you need n8n integration.

---

## Infrastructure & Platform

Systems that other projects depend on.

| Project | What it does | Stack |
|---------|-------------|-------|
| [omniweb-agents](https://github.com/mj-deving/omniweb-agents) | Autonomous agent framework — SENSE/ACT/CONFIRM | TypeScript, 67K LOC, 3,249 tests |
| [my-pai-cloud-solution](https://github.com/mj-deving/my-pai-cloud-solution) | Cloud deployment platform for PAI agents | TypeScript, 412 tests |
| [cortex](https://github.com/mj-deving/cortex) | AI knowledge ingestion (Scout/Comb/Waggle) | TypeScript, Cloudflare Workers |
| [claudeclaw](https://github.com/mj-deving/claudeclaw) | PAI mobile surface — Telegram bot | Claude Agent SDK, grammY |

---

## Security & Operations

| Project | What it does | Stack |
|---------|-------------|-------|
| [openclaw-hardened](https://github.com/mj-deving/openclaw-hardened) | Security-first OpenClaw deployment | Shell, 15-phase guide |
| [agentskills](https://github.com/mj-deving/agentskills) | Agent Skills spec + SuperColony contribution | Python, 2,159 LOC |

---

## Tools & Utilities

| Project | What it does | Stack |
|---------|-------------|-------|
| [markdown-reader](https://github.com/mj-deving/markdown-reader) | CLI: markdown to beautiful HTML reading view | TypeScript |
| [arcade-hub](https://github.com/mj-deving/arcade-hub) | Real-time arcade machine monitoring | Spring Boot, WebSocket, PostgreSQL |

---

## How to Use This Library

**Explore:** Browse the categories above. Each project links to its repo with full README.

**Adopt:** Look for the "Adopt" sections — they tell you exactly how to start using a project.

**Fork & Customize:** Every project is designed to be forked. The architecture decision that matters most is called out in each README.

**Connect:** Projects are connected. The [dependency graph](https://github.com/mj-deving/KI-Roadmap) in KI-Roadmap shows how they relate.

---

## Stats

| Metric | Value |
|--------|-------|
| Total projects | 25 |
| Total tests | 3,900+ |
| npm packages | 3 (1,685 downloads/month) |
| Languages | TypeScript (primary), Python, Java, Shell |
| Token savings proven | 56% to 96% across code-mode projects |
| External validation | Anthropic (98.7% savings), Cloudflare ("the better way to use MCP") |

---

*Built with [PAI](https://github.com/mj-deving/KI-Roadmap) — Personal AI Infrastructure*
