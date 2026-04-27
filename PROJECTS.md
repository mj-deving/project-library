# Project Cards — 10 Flagships

> Detailed cards with architecture decisions and adoption guides.
> For the full index of all 25 projects, see [INDEX.md](INDEX.md).

> **Narrativ:** v6.1 — Fullstack + alle Projekte · Stand 2026-04-14 · See [Portfolio-Narrativ.md](https://github.com/mj-deving/KI-Roadmap/blob/main/Roadmap/Portfolio-Narrativ.md)

---

### [Speed-to-Lead Autopilot](https://github.com/mj-deving/n8n-speed-to-lead)

> Automated lead qualification and personalized response in under 30 seconds.

**Stack:** `n8n` `Gemini 2.0 Flash` `Google Sheets` `Gmail` `Slack`
**Tests:** 10/10 leads scored correctly | **Key Metric:** ~8s end-to-end, ~$0.001/lead

**What it does:** A webhook receives an inquiry, an LLM scores it on four weighted criteria (budget, urgency, service match, decision-maker signal) for a 0-100 composite score, logs the full breakdown to Google Sheets or HubSpot, sends a personalized email, and posts a Slack alert with priority tagging and live response time. Includes a standalone HTML contact form with zero dependencies.

**Architecture decision:** Structured Output Parser with AutoFix sub-model. If the LLM returns malformed JSON, a dedicated AutoFix node automatically retries with a correction prompt instead of failing the workflow. This makes the scoring pipeline self-correcting without human intervention.

**Adopt it:** Fork the repo and run `npx n8nac init` to connect your n8n instance. Swap in your own scoring criteria by editing the German-language system prompt in the Qualify Lead node. The Google Sheets variant works out of the box; switch to HubSpot by deploying the alternate workflow file and creating the custom properties listed in the README.

---

### [RAG Hybrid Chatbot](https://github.com/mj-deving/rag-hybrid-chatbot)

> Chat with your documents using hybrid vector + knowledge graph retrieval with adaptive query routing.

**Stack:** `FastAPI` `Qdrant` `NetworkX` `fastembed` `Claude via OpenRouter` `Docker`
**Tests:** 61 | **Key Metric:** 4-way adaptive routing (simple/standard/complex/relational)

**What it does:** Upload PDFs, Markdown, or text files and ask questions with cited answers. The system combines vector search (Qdrant with local ONNX embeddings) and a knowledge graph (NetworkX with LLM-extracted entities) for retrieval. A query classifier routes each question through one of four pipelines, and a Corrective RAG filter removes irrelevant chunks before generation.

**Architecture decision:** Local embeddings via fastembed (paraphrase-multilingual-MiniLM-L12-v2, 384-dim, ONNX) instead of an embedding API. This eliminates an external dependency, removes per-query embedding costs, and keeps document data off third-party servers. The only external call is generation via OpenRouter.

**Adopt it:** Run `docker compose up --build` with an OpenRouter key in `.env` and you are running at localhost:8000. For English-only corpora, switch the embedding model to `BAAI/bge-small-en-v1.5` via the `EMBEDDING_MODEL` env var. Add your own documents through the `/upload` endpoint or the drag-and-drop chat UI.

---

### [Managed Agents Research](https://github.com/mj-deving/managed-agents-research)

> Autonomous research agents that plan, execute, and self-critique across five progressive demos.

**Stack:** `Claude Agent SDK` `Python 3.12` `Starlette` `WebSearch/WebFetch` `Docker`
**Tests:** 42 | **Key Metric:** Reports avg 2,253 words, 8-18 sources, $0.42-$1.97/run

**What it does:** Five demos showing progressively more sophisticated agent patterns with the Claude Agent SDK. From single-agent one-shot research (Demo 1) to multi-agent orchestration with plan-and-execute plus reflection (Demo 5). Demo 3 exposes an HTTP API that n8n or any client can call. Demo 4 uses Haiku for planning/reflection and Sonnet for execution to cut costs while maintaining quality.

**Architecture decision:** Multi-model routing in Demo 4 -- Haiku handles planning and reflection at 10x lower cost while Sonnet handles the execution phase that requires reasoning quality. Three separate `query()` calls per run, each with the optimal model for its phase. Plan+Reflect costs $0.04-$0.08 for the cheap phases vs $0.15-$0.20 if Sonnet did everything.

**Adopt it:** Clone the repo, `pip install -r requirements.txt`, and run any demo script with a topic string. Demo 3 is the integration-ready one: start the Starlette server and POST topics to `/research`. Import the included n8n workflow JSON to get webhook-triggered research with email delivery out of the box.

---

### [Voice Agent](https://github.com/mj-deving/voice-agent)

> AI phone agent for medical practices -- answers calls, books appointments, detects emergencies, all in German.

**Stack:** `Vapi.ai` `FastAPI` `Claude Sonnet 4` `ElevenLabs TTS` `Docker` `Fly.io`
**Tests:** 156 | **Key Metric:** 5/5 live call scenarios passed

**What it does:** Lisa, the AI assistant, answers incoming calls in German for medical practices. She distinguishes new and existing patients, books appointments with availability checking, transfers calls for prescriptions, detects emergencies and recommends 112, sends call summaries via email/webhook, and adapts greetings to holidays and office hours. Multi-practice support via YAML configuration.

**Architecture decision:** YAML-driven multi-practice configuration instead of code changes per customer. Each practice is a YAML file defining the assistant name, greeting, services, office hours, and transfer number. Deploying for a new practice means creating one YAML file and running the setup script -- zero code changes required.

**Adopt it:** Copy `configs/praxis_template.yaml`, fill in your practice details, and run `python scripts/setup_vapi.py --config your-practice.yaml --webhook-url <your-url>`. The script creates the Vapi assistant, registers tools, and optionally provisions a phone number. Deploy via `fly deploy` for Frankfurt-region hosting or use Docker locally.

---

### [LangGraph Agent](https://github.com/mj-deving/langgraph-agent)

> Autonomous research agent with explicit state machine, quality loop, and SSE streaming.

**Stack:** `LangGraph` `FastAPI` `Tavily` `SQLite Checkpointer` `Claude Sonnet 4 via OpenRouter`
**Tests:** 5 topics verified | **Key Metric:** ~$0.06/run, quality gate at score >= 7

**What it does:** Four-node LangGraph pipeline (plan, research, write, review) with conditional edges that form a quality loop. The reviewer scores reports 0-10; if below 7, it loops back to the planner with feedback for up to 2 iterations. SQLite persistence saves state after each node, and a FastAPI server streams node transitions via SSE in real-time.

**Architecture decision:** Explicit state machine with conditional edges instead of prompt-driven looping. The quality gate is a first-class graph construct -- the reviewer score triggers a deterministic edge back to the planner, not a prompt that says "try again." This makes the loop visible as a Mermaid diagram, state inspectable at every node, and iteration count enforceable.

**Adopt it:** Clone, create a venv, `pip install -r requirements.txt`, and set `OPENROUTER_API_KEY` plus `TAVILY_API_KEY` (free tier: 1000 searches/month) in `.env`. Run from CLI with `python -m src.run "your topic"` or start the API server with `uvicorn src.api:app` for SSE streaming at `/research/{id}/stream`.

---

### [Meeting Intelligence Pipeline](https://github.com/mj-deving/n8n-meeting-intelligence)

> Meeting audio or transcript in, structured protocol with action items, decisions, and follow-ups out.

**Stack:** `n8n` `Claude Sonnet 4` `Whisper API` `Google Sheets` `Gmail` `Slack`
**Tests:** 3 scenarios verified | **Key Metric:** 19s processing, 6 action items extracted

**What it does:** A 14-node n8n workflow that accepts meeting transcripts (text webhook) or audio files (audio webhook with Whisper transcription). Claude Sonnet extracts summary, decisions, action items with owners and deadlines, open questions, follow-ups, key topics, and sentiment. Results go to Google Sheets as a protocol row, Gmail as an HTML-formatted protocol, and Slack with priority-tagged action items.

**Architecture decision:** Dual-trigger architecture with text and audio webhooks feeding the same analysis pipeline. This lets teams send raw audio from recording tools (Whisper handles transcription) or pre-existing transcripts from tools like Otter.ai -- same output format either way. A local Whisper Docker option keeps audio data on-premises for GDPR compliance.

**Adopt it:** Push the workflow to your n8n instance with `npx n8nac push`, configure the five credentials (OpenRouter, Google Sheets, Gmail, Slack, optionally OpenAI for Whisper), and POST a test payload to `/webhook/meeting-text`. For audio input, point your recording tool at `/webhook/meeting` with multipart upload.

---

### [Email Triage Agent](https://github.com/mj-deving/n8n-email-triage)

> Automatic email classification, routing, and response with 7 categories and 4 action types.

**Stack:** `n8n` `Claude Sonnet 4` `IMAP/Gmail` `Google Sheets` `Slack`
**Tests:** 11/11 executions passed | **Key Metric:** ~7s/email, ~$0.01/classification

**What it does:** Polls Gmail via IMAP, classifies each email with Claude Sonnet across 7 categories (support, sales, billing, partnership, spam, personal, newsletter), 4 priorities, and sentiment analysis. Routes by action type: auto-reply for routine support, draft for sales/billing, escalate to Slack for urgent/negative items, ignore for spam. Logs everything to Google Sheets with 11 columns.

**Architecture decision:** Dual-trigger with IMAP polling for production and webhook for testing, feeding a shared Normalize Input node. This means the entire classification and routing pipeline can be tested with `curl` against the webhook without needing real emails, while production runs on IMAP polling at 60-second intervals with zero changes to the downstream logic.

**Adopt it:** Clone, `npm install`, and `npx n8nac push` the workflow to your n8n instance. Set up IMAP credentials with a Gmail app password (2FA required), configure the five credential types, and run the setup workflow to create the Google Sheet. Send the 10 included mock emails via `./tests/send-mock-emails.sh` to verify classification accuracy.

---

### [CrewAI-n8n Bridge](https://github.com/mj-deving/crewai-n8n-bridge)

> FastAPI service exposing CrewAI multi-agent crews as REST endpoints with SSE streaming and dynamic crew creation.

**Stack:** `CrewAI 1.14` `FastAPI` `Claude Sonnet 4 via OpenRouter` `SerperDev` `Docker`
**Tests:** 54 | **Key Metric:** 5 built-in crews, 70-186s/run, $0.02-$0.15/run

**What it does:** Wraps CrewAI multi-agent crews in a REST API. Five built-in crews (research, sales, content, strategy, research-flow) cover sequential, hierarchical, and flow-based processes. Dynamic crew creation lets you define agents, tasks, and process type at runtime via POST. Three result delivery modes: polling, SSE streaming for live agent steps, or webhook callback.

**Architecture decision:** Dynamic crew creation via API instead of only YAML-configured static crews. POST a JSON payload with agents, tasks, tools, and process type to `/crews`, then kick it off immediately. This turns CrewAI from a developer tool into a platform service where n8n workflows or other clients can compose and run custom multi-agent pipelines without code changes.

**Adopt it:** `pip install crewai 'crewai[tools]' fastapi uvicorn httpx`, set `OPENROUTER_API_KEY` and optionally `SERPER_API_KEY`, and run `uvicorn app.main:app`. Import the included n8n workflow JSONs from the `n8n/` directory for webhook-triggered crew execution. Or use `docker compose up` for the bridge plus n8n in one command.

---

### [Agent Playground](https://github.com/mj-deving/agent-playground)

> Interactive chat UI for AI research agents with SSE streaming, conversation history, and dual agent modes.

**Stack:** `Next.js 14` `TypeScript` `Tailwind CSS v4` `SSE` `localStorage`
**Tests:** -- | **Key Metric:** 2 agent modes, real-time streaming, zero-dependency markdown

**What it does:** A responsive dark-theme chat interface that connects to the managed-agents-research backend. Supports basic single-pass research and plan-and-reflect iterative reasoning through a mode toggle. The Next.js API route wraps the synchronous backend response in an SSE stream with typed progress events, delivering chunked reports with live markdown rendering. Conversation history persists in localStorage.

**Architecture decision:** SSE streaming proxy in the Next.js API route rather than direct client-to-backend connection. The API route converts the synchronous backend JSON response into a typed SSE stream (status/chunk/done/error events), giving the frontend real-time progress without requiring the backend to support streaming natively. This decouples the UI experience from backend capabilities.

**Adopt it:** Start the managed-agents-research backend on port 8000, then `npm install && npm run dev`. The playground runs at localhost:3000. Set `BACKEND_URL` to point to a different backend. The zero-dependency markdown parser in `lib/markdown.ts` and the SSE hook in `hooks/useResearchAgent.ts` are portable to any streaming agent UI.

---

### [Self-Healing n8n Workflow](https://github.com/mj-deving/n8n-self-healing)

> Self-healing workflow system that learns from failures -- the 4th identical error routes from memory with zero LLM tokens.

**Stack:** `n8n` `n8nac` `OpenRouter` `Workflow Static Data` `Slack`
**Tests:** 6 scenarios verified | **Key Metric:** 70% fewer LLM calls at scale via learning loop

**What it does:** A four-workflow system (API Data Sync, Self-Healer, Error Generator, Monitor) that catches structured errors, enriches them with heal history and upstream reachability, diagnoses via historical patterns or LLM or deterministic rules, and recovers with retry/backoff/fallback/escalate strategies. Once an error type has been healed successfully 3 times, the 4th match skips the LLM entirely and routes from stored history.

**Architecture decision:** Learning loop via workflow static data that compounds diagnosis knowledge. The system tracks every heal outcome by error type. After 3 successful heals with the same strategy, that pattern becomes the dominant repair path -- subsequent matches return `diagnosis_source: historical` with 0 tokens and sub-400ms response. This turns a per-error LLM cost into a one-time learning investment.

**Adopt it:** Clone, `npm install`, and run `npm run setup:n8n -- http://your-n8n:5678` with your `N8N_API_KEY`. Push all four workflows with `npx n8nac push`. Test with `npm run demo:errors` to trigger all six error scenarios. The system works without an OpenRouter key (deterministic fallback), but adding one enables LLM diagnosis for novel errors that then get learned.

---
