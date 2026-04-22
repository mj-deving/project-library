# Project Library

> One person. One harness. 25 projects.

[![Projects](https://img.shields.io/badge/projects-25-teal)](https://github.com/mj-deving/project-library) [![Tests](https://img.shields.io/badge/tests-3%2C900%2B-green)](https://github.com/mj-deving/project-library) [![npm](https://img.shields.io/badge/npm_packages-3-red)](https://www.npmjs.com/~mj-deving) [![TypeScript](https://img.shields.io/badge/primary-TypeScript-blue)](https://github.com/mj-deving)

This is the curated index of everything I've built — structured for adoption, not just browsing. Each project includes what it does, how to use it, and why the architecture works the way it does.

**Builder:** [Marius Jauernik](https://github.com/mj-deving) — AI & Fullstack Engineer, building PAI (Personal AI Infrastructure)

**Detailed cards:** See [PROJECTS.md](PROJECTS.md) for 10 flagship deep-dives with architecture decisions and adoption guides.

---

## n8n Automation & Code-Mode

Production-grade n8n workflows proving that code-first AI automation cuts token costs by 56-96%.

| Project | What it does | Stack | Key Metric |
|---------|-------------|-------|------------|
| [n8n-speed-to-lead](https://github.com/mj-deving/n8n-speed-to-lead) | AI lead qualification in <30s | ![n8n](https://img.shields.io/badge/-n8n-EA4B71?style=flat-square) ![Claude](https://img.shields.io/badge/-Claude-D4A574?style=flat-square) | $0.001/lead |
| [n8n-meeting-intelligence](https://github.com/mj-deving/n8n-meeting-intelligence) | Recording to protocol + action items | ![n8n](https://img.shields.io/badge/-n8n-EA4B71?style=flat-square) ![Whisper](https://img.shields.io/badge/-Whisper-74AA9C?style=flat-square) | 19s processing |
| [n8n-email-triage](https://github.com/mj-deving/n8n-email-triage) | 7-category email classification | ![n8n](https://img.shields.io/badge/-n8n-EA4B71?style=flat-square) ![Claude](https://img.shields.io/badge/-Claude-D4A574?style=flat-square) | 11/11 tests |
| [n8n-self-healing](https://github.com/mj-deving/n8n-self-healing) | Workflow learns from failures | ![n8n](https://img.shields.io/badge/-n8n-EA4B71?style=flat-square) ![TS](https://img.shields.io/badge/-TypeScript-3178C6?style=flat-square) | 0 tokens on 4th error |
| [n8n-autopilot](https://github.com/mj-deving/n8n-autopilot) | 6 AI workflows, fully code-first | ![n8nac](https://img.shields.io/badge/-n8nac-EA4B71?style=flat-square) ![Gemini](https://img.shields.io/badge/-Gemini-4285F4?style=flat-square) | Origin project |

**Adopt:** Clone [n8n-project-template](https://github.com/mj-deving/n8n-project-template) to start your own code-first n8n project with n8nac + code-mode + Beads.

---

## Code-Mode Ecosystem (npm packages)

The thesis: replace n8n's AI Agent node with direct code execution. Proven 96% token savings.

| Project | What it does | Stack | Downloads |
|---------|-------------|-------|-----------|
| [n8n-nodes-utcp-codemode](https://github.com/mj-deving/n8n-nodes-utcp-codemode) | n8n community node for code-mode | ![TS](https://img.shields.io/badge/-TypeScript-3178C6?style=flat-square) ![n8n](https://img.shields.io/badge/-n8n-EA4B71?style=flat-square) | 1,422/mo |
| [code-mode-tools](https://github.com/mj-deving/code-mode-tools) | CLI + MCP server for code-mode sandbox | ![TS](https://img.shields.io/badge/-TypeScript-3178C6?style=flat-square) ![MCP](https://img.shields.io/badge/-MCP-8B5CF6?style=flat-square) | npm |
| [n8nac-tools](https://github.com/mj-deving/n8nac-tools) | CLI wrapper for n8nac commands | ![TS](https://img.shields.io/badge/-TypeScript-3178C6?style=flat-square) ![CLI](https://img.shields.io/badge/-CLI-333?style=flat-square) | npm |
| [code-first-n8n](https://github.com/mj-deving/code-first-n8n) | 5 POC workflows, the proving ground | ![TS](https://img.shields.io/badge/-TypeScript-3178C6?style=flat-square) ![n8n](https://img.shields.io/badge/-n8n-EA4B71?style=flat-square) | Benchmarked |

**Adopt:** `npm install -g code-mode-tools` to get the CLI + MCP server. Use with any n8n instance.

---

## Code-Mode Production Projects

Real-world applications built on the code-mode foundation, each with measured benchmarks.

| Project | What it does | Stack | Token Savings |
|---------|-------------|-------|--------------|
| [rag-pipeline-factory](https://github.com/mj-deving/rag-pipeline-factory) | Tell it what you want, get a deployed RAG pipeline | ![n8n](https://img.shields.io/badge/-n8n-EA4B71?style=flat-square) ![TS](https://img.shields.io/badge/-TypeScript-3178C6?style=flat-square) | 56% |
| [soc-alert-triage](https://github.com/mj-deving/soc-alert-triage) | Parallel threat intel enrichment | ![n8n](https://img.shields.io/badge/-n8n-EA4B71?style=flat-square) ![Security](https://img.shields.io/badge/-Security-DC3545?style=flat-square) | 86% |

**Adopt:** Fork and customize the enrichment sources for your domain (HR, finance, compliance).

---

## AI Agents & Research

Progressive agent architectures — from single-agent to multi-agent orchestration.

| Project | What it does | Stack | Key Metric |
|---------|-------------|-------|------------|
| [managed-agents-research](https://github.com/mj-deving/managed-agents-research) | 5 progressive agent demos | ![Claude SDK](https://img.shields.io/badge/-Claude_SDK-D4A574?style=flat-square) ![Python](https://img.shields.io/badge/-Python-3776AB?style=flat-square) | 42 tests |
| [langgraph-agent](https://github.com/mj-deving/langgraph-agent) | State machine: plan, research, write, review | ![LangGraph](https://img.shields.io/badge/-LangGraph-1C3C3C?style=flat-square) ![FastAPI](https://img.shields.io/badge/-FastAPI-009688?style=flat-square) | 16 tests, SSE |
| [crewai-n8n-bridge](https://github.com/mj-deving/crewai-n8n-bridge) | 5 multi-agent crews as REST API | ![CrewAI](https://img.shields.io/badge/-CrewAI-FF6B35?style=flat-square) ![Docker](https://img.shields.io/badge/-Docker-2496ED?style=flat-square) | 54 tests, SSE |
| [voice-agent](https://github.com/mj-deving/voice-agent) | AI phone agent for medical practices | ![FastAPI](https://img.shields.io/badge/-FastAPI-009688?style=flat-square) ![Vapi](https://img.shields.io/badge/-Vapi-7C3AED?style=flat-square) | 156 tests |
| [rag-hybrid-chatbot](https://github.com/mj-deving/rag-hybrid-chatbot) | Hybrid RAG: Vector + Knowledge Graph + CRAG | ![Qdrant](https://img.shields.io/badge/-Qdrant-DC382D?style=flat-square) ![Python](https://img.shields.io/badge/-Python-3776AB?style=flat-square) | 61 tests |
| [agent-playground](https://github.com/mj-deving/agent-playground) | Interactive chat UI for research agents | ![Next.js](https://img.shields.io/badge/-Next.js-000?style=flat-square) ![SSE](https://img.shields.io/badge/-SSE-4CAF50?style=flat-square) | Live demo |

**Adopt:** Start with `managed-agents-research` for agent patterns, `crewai-n8n-bridge` if you need n8n integration.

---

## Infrastructure & Platform

Systems that other projects depend on.

| Project | What it does | Stack | Key Metric |
|---------|-------------|-------|------------|
| [omniweb-agents](https://github.com/mj-deving/omniweb-agents) | Autonomous agent framework — SENSE/ACT/CONFIRM | ![TS](https://img.shields.io/badge/-TypeScript-3178C6?style=flat-square) ![Node](https://img.shields.io/badge/-Node.js-339933?style=flat-square) | 67K LOC, 3,249 tests |
| [my-pai-cloud-solution](https://github.com/mj-deving/my-pai-cloud-solution) | Cloud deployment platform for PAI agents | ![TS](https://img.shields.io/badge/-TypeScript-3178C6?style=flat-square) ![CF](https://img.shields.io/badge/-Cloudflare-F38020?style=flat-square) | 412 tests |
| [cortex](https://github.com/mj-deving/cortex) | AI knowledge ingestion (Scout/Comb/Waggle) | ![TS](https://img.shields.io/badge/-TypeScript-3178C6?style=flat-square) ![CF Workers](https://img.shields.io/badge/-CF_Workers-F38020?style=flat-square) | D1, R2 |
| [claudeclaw](https://github.com/mj-deving/claudeclaw) | PAI mobile surface — Telegram bot | ![Claude SDK](https://img.shields.io/badge/-Claude_SDK-D4A574?style=flat-square) ![grammY](https://img.shields.io/badge/-grammY-26A5E4?style=flat-square) | Live on TG |

---

## Security & Operations

| Project | What it does | Stack | Key Metric |
|---------|-------------|-------|------------|
| [openclaw-hardened](https://github.com/mj-deving/openclaw-hardened) | Security-first OpenClaw deployment | ![Shell](https://img.shields.io/badge/-Shell-4EAA25?style=flat-square) ![Security](https://img.shields.io/badge/-Security-DC3545?style=flat-square) | 15-phase guide |
| [agentskills](https://github.com/mj-deving/agentskills) | Agent Skills spec + SuperColony contribution | ![Python](https://img.shields.io/badge/-Python-3776AB?style=flat-square) ![Demos](https://img.shields.io/badge/-Demos-FFD700?style=flat-square) | 2,159 LOC |

---

## Tools & Utilities

| Project | What it does | Stack | Key Metric |
|---------|-------------|-------|------------|
| [markdown-reader](https://github.com/mj-deving/markdown-reader) | CLI: markdown to beautiful HTML reading view | ![TS](https://img.shields.io/badge/-TypeScript-3178C6?style=flat-square) ![CLI](https://img.shields.io/badge/-CLI-333?style=flat-square) | Bun runtime |
| [arcade-hub](https://github.com/mj-deving/arcade-hub) | Real-time arcade machine monitoring | ![Java](https://img.shields.io/badge/-Java-ED8B00?style=flat-square) ![Spring](https://img.shields.io/badge/-Spring_Boot-6DB33F?style=flat-square) | WebSocket, PG |

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
