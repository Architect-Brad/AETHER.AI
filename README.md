<div align="center">

```
 █████╗ ███████╗████████╗██╗  ██╗███████╗██████╗
██╔══██╗██╔════╝╚══██╔══╝██║  ██║██╔════╝██╔══██╗
███████║█████╗     ██║   ███████║█████╗  ██████╔╝
██╔══██║██╔══╝     ██║   ██╔══██║██╔══╝  ██╔══██╗
██║  ██║███████╗   ██║   ██║  ██║███████╗██║  ██║
╚═╝  ╚═╝╚══════╝   ╚═╝   ╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝
         NEURAL INTERFACE  ·  v5.14
```

**Open-source. Local-first. No compromises.**

[![License: GPL-3.0](https://img.shields.io/badge/License-GPL--3.0-00f3ff?style=flat-square&labelColor=0a0a0a)](LICENSE)
[![Single File](https://img.shields.io/badge/Architecture-Single%20File-00ff88?style=flat-square&labelColor=0a0a0a)](index.html)
[![No Build Step](https://img.shields.io/badge/Build-None%20Required-ff00ff?style=flat-square&labelColor=0a0a0a)](index.html)
[![PWA Ready](https://img.shields.io/badge/PWA-Installable-ff6600?style=flat-square&labelColor=0a0a0a)](manifest.json)
[![Zero Dependencies](https://img.shields.io/badge/Backend-Zero%20Dependencies-gold?style=flat-square&labelColor=0a0a0a)](#)

*Runs in your browser. Speaks to any model. Remembers everything.*

</div>

---

## What Is AETHER?

AETHER is a **precision AI neural interface** built for people who refuse to compromise. It runs entirely in your browser — a single HTML file that connects to any AI model anywhere: local inference servers, cloud APIs, or your own metal. No servers. No subscriptions. No telemetry. No middlemen.

It was built by **The Architect** as a direct counter to closed, cloud-locked AI interfaces. The philosophy is simple: your conversations, your models, your data — all sovereign, all local, all encrypted if you want them to be.

> *"Competing with OpenClaw — open, local-first, no compromises."*

---

## Feature Architecture

### Core Intelligence Layer

| Capability | Detail |
|---|---|
| **16 Live Tools** | Web search, weather, GitHub, Gmail, Outlook, Slack, Notion, code execution, OCR, image generation, web scraping, calendar, location, math engine, canvas, ASCII 3D |
| **Chain-of-Thought Engine** | Native `<think>…</think>` block rendering with live streaming — watches reasoning unfold in real time |
| **Deep Research Mode** | Configurable depth (surface → exhaustive), width (focused → comprehensive), criticality (casual → critical with full discriminator pass) |
| **Dual Context** | Multiple conversations running simultaneously in background — switch between them without losing generation state |
| **BM25 + Vector RAG** | Keyword memory with BM25 scoring plus semantic vector search via ONNX embeddings for long-term recall |
| **Workspace System** | File-system or virtual workspace with structured markdown files — AETHER reads, writes, and reasons over your project context |

### Provider Matrix

AETHER speaks natively to every major inference provider:

```
OpenAI · Anthropic · Google Gemini · xAI Grok · DeepSeek · Groq
Mistral · Qwen · Kimi · Together AI · Fireworks · SiliconFlow
OpenRouter · Perplexity · Cohere · Local (Ollama / LM Studio / llama.cpp)
```

All providers use a unified auth layer — Bearer, `x-api-key`, Gemini URL params, and custom headers are all handled automatically. Credentials are AES-256-GCM encrypted at rest.

### Qwen 3.5 Native Support

AETHER has first-class support for the **Qwen 3.5 series** — Alibaba's hybrid-architecture models with 262K native context, Early Fusion multimodality, and Adaptive Thinking. The interface injects native `enable_thinking` parameters, renders reasoning blocks in real time, and correctly maps context windows for all model variants from 0.8B to 35B.

---

## Speech Intelligence

### STT — Speech to Text

| Engine | Where It Works |
|---|---|
| **Browser Native** | Chrome, Edge, Chromium, and all `localhost` origins — zero config, instant |
| **Whisper (API)** | OpenAI's cloud transcription with multi-language support |
| **Whisper.cpp** | Local HTTP server — fully offline, runs on CPU |
| **Whisper.js** | In-browser ONNX model — no server, no internet, no mic permission beyond browser |
| **Google Speech** | Cloud STT with broad language coverage |
| **Vosk** | Local WebSocket server for offline recognition |

**Localhost Security:** AETHER auto-detects secure contexts — `localhost`, `127.0.0.1`, `.local` domains, and `https://` are all treated as fully trusted. Browser STT and TTS work out of the box on all these origins without extra configuration.

### TTS — Text to Speech

| Engine | Detail |
|---|---|
| **Browser Native** | System voices on all platforms — works on localhost, Chrome, Firefox, Safari, Edge |
| **Piper** | High-quality neural TTS via local HTTP server |
| **Kokoro** | In-browser neural synthesis with `af_heart` and other voice packs |

The Call Mode feature uses the TTS engine you've configured — enabling AETHER to vocally check in, read back responses, or run voice sessions entirely client-side.

---

## Deep Research Mode

AETHER's Deep Research mode turns a single message into a structured investigation. Before the query is sent, AETHER:

1. **Prompts for clarification** if your query is ambiguous (under-specified, no context, no question mark) — it asks what you actually need before burning tokens on guesswork
2. **Applies your research parameters:**

| Parameter | Options | Effect |
|---|---|---|
| **Depth** | Surface · Standard · Deep · Exhaustive | Controls reasoning thoroughness and response length |
| **Width** | Focused · Broad · Comprehensive | Controls scope — single topic vs cross-domain sweep |
| **Criticality** | Casual · Important · Critical | Controls fact-checking rigour and discriminator pass |

3. **Critical mode** adds a discriminator pass — AETHER re-examines every major claim after composing its answer, flags uncertain or contested points, and appends a **Confidence Assessment** section with a reliability score.

Activate via the `DEEP` button in the control panel.

---

## File Creation

Every AETHER response can be exported directly from the chat to three formats:

| Format | Detail |
|---|---|
| **Markdown (.md)** | Clean markdown export — structure preserved exactly as rendered |
| **Plain Text (.txt)** | Markdown stripped — just the words, clean and portable |
| **Word Document (.docx)** | Full Office Open XML with AETHER branding — headings, bold, lists, all correctly mapped. Zero dependencies — built with a native ZIP encoder |

Click **`[ SAVE AS ]`** on any AETHER response to access the file picker. Files auto-name from the response heading or a timestamp fallback.

---

## Interface

### The AETHER Wave

The visualizer canvas at the top of the interface is a live neural signal indicator:

- **Idle:** Slow cyan pulse at low amplitude
- **Generating:** White wave, amplitude 18, phase speed 3×
- **Groq / High-Speed Inference:** Orange wave, amplitude 22, phase speed **10×** — the visual signature of 500+ TPS throughput

### Context Bar

The context progress bar tracks token usage against the active model's context window in real time. For API key users, the default context window is **32,768 tokens** — four times the old 8k limit. Local users default to a conservative 8,192. The bar turns red at 90% utilisation.

### Multistep Panel

When AETHER performs multi-step operations (workspace reads, agent tasks, file operations), a floating step tracker appears showing each operation with live status indicators:

```
⏳ Reading CORE_LOGIC.md…
✓  CORE_LOGIC.md — 1,842 chars
✓  Workspace manifest loaded
```

The panel auto-dismisses 2.5 seconds after completion.

### Performance Metrics

TTFT (time-to-first-token) and TPS (tokens per second) are tracked on every request but **hidden by default** — they appear in the status bar only when enabled. Toggle them in **CFG → Streaming → Show TTFT / TPS Metrics**.

---

## Workspace System

The workspace gives AETHER persistent memory across a project. It operates in two modes:

**File System Mode** — Direct access to a folder on your device via the File System Access API. AETHER reads and writes actual files. Changes persist between sessions.

**Virtual Mode** — An in-browser virtual filesystem backed by IndexedDB. No folder required. Survives page refreshes but stays local to the browser.

### Workspace Files

| File | Purpose |
|---|---|
| `CORE_LOGIC.md` | Behavioral rules and task logic for the session |
| `WORKSPACE.md` | Project focus, active questions, current findings |
| `ARCHIVES.md` | Long-term memory — research archive, past conclusions |
| `FACILITIES.md` | Tools, capabilities, external integrations documented |
| `PROTOCOL.md` | Communication style and output format instructions |
| `USER.md` | User profile and preferences for personalisation |
| `LOGS.md` | Timestamped log of all background task outputs |
| `ENCRYPT.md` | Security clearance level for the session |

AETHER reads workspace files on demand using `<read_file>` tags in responses — the system automatically injects the file contents into the next message.

### Dynamic Notifications

The notification system reads your actual workspace state — never generating static filler. When you open the Background panel, AETHER surfaces real intelligence:

- How many conversations are in memory and how many were active today
- Workspace file count with names
- Archive entry count from `ARCHIVES.md`
- Background task log entries from `LOGS.md`
- Quota usage if approaching limits
- Running background task count

---

## Background Tasks

Queue long-running work and let AETHER handle it while you continue other conversations:

| Task Type | What It Does |
|---|---|
| **Research** | Runs a full research query in the background, saves result to the current conversation |
| **Summarise** | Condenses provided text to 3–5 bullets |
| **Remind** | Time-delayed notification after a set delay |
| **Scheduled** | Runs a prompt at a scheduled time, logs to `LOGS.md` |
| **Agent (BG)** | Autonomous multi-tool execution in background |

---

## Security

AETHER encrypts all API keys and hook credentials using **AES-256-GCM** with PBKDF2 key derivation (100,000 iterations, SHA-256). Nothing leaves your device unencrypted. The password is never stored — only a derived key held in session memory.

Setting a password is optional but recommended for shared devices. Reset via **CFG → Security → Change Encryption Key**.

---

## Installation

AETHER requires no build step and no backend. Three ways to run it:

### 1. Direct — Just Open It
```bash
git clone https://github.com/architect-brad/AETHER.AI
cd AETHER.AI
open index.html      # or double-click it
```

### 2. Local Server (Recommended for STT/TTS)
```bash
# Python
python3 -m http.server 3000

# Node
npx serve .

# Then open: http://localhost:3000
```
Running on localhost unlocks the full Browser STT/TTS stack and enables service worker caching.

### 3. Install as PWA
Open AETHER in Chrome or Edge, then:
- **Desktop:** Click the install icon in the address bar
- **Mobile:** Tap Share → Add to Home Screen

The PWA runs offline using cached assets and supports shortcuts for **New Chat** and **Deep Research** directly from your home screen or taskbar.

---

## Configuration

### API Setup (SETUP button)

1. Click **SETUP** in the toolbar
2. Select your provider from the visual grid
3. The endpoint auto-fills — paste your API key
4. Click **SAVE SETUP**

For local models (Ollama, LM Studio, llama.cpp):
- Provider: `Local`
- Endpoint: `http://localhost:11434/v1/chat/completions` (Ollama) or your server's port
- API Key: leave blank or use `ollama` as a placeholder

### Hook Configuration (HOOKS button)

Connect external services:

```
Search:    Tavily · Brave · Serper
Scraping:  Firecrawl · Puter
Email:     Gmail · Outlook
Comms:     Slack
Notes:     Notion
Data:      GitHub · GitLab
Maps:      OpenStreetMap (built-in)
Weather:   OpenWeatherMap
```

### STT / TTS (HOOKS → Speech)

Set your preferred speech engine and save. The microphone button in the input bar activates once configured. For browser-native mode, no keys are needed — just select **Browser** and click the mic.

---

## Supported Models (Selected)

| Provider | Models |
|---|---|
| **OpenAI** | GPT-5.4, GPT-5 Mini, GPT-4.1, GPT-4.1 Mini, o4-mini, GPT-4o |
| **Anthropic** | Claude 4.6 Opus, Claude 4.6 Sonnet, Claude 4.5 Haiku |
| **Google** | Gemini 3.1 Pro, Gemini 2.0 Flash, Gemini 1.5 Pro |
| **xAI** | Grok 4, Grok 4 Fast |
| **DeepSeek** | DeepSeek V3.2, DeepSeek Reasoner |
| **Groq** | Llama 4 Maverick, Llama 4 Scout, Mixtral |
| **Qwen** | Qwen 3.5 (0.8B–35B local), Qwen 3.5 Max/Flash cloud |
| **Mistral** | Large 3, Devstral 2 |
| **Kimi** | K2.5 (256K context) |
| **Local** | Any OpenAI-compatible endpoint |

Context windows are tracked per model. The system auto-detects limits and warns you at 90% utilisation.

---

## Coding Mode

Activate the **CODE** button to enter Coding Mode. In this mode:

- All code blocks require a `lang:filename.ext` header
- AETHER groups related code by file
- Every response includes a `> What changed` blockquote
- Fix mode shows only the corrected code, never the original problem repeated
- A live preview panel renders HTML/CSS/JS output inline
- The Run button executes code via the Piston API (30+ languages)

---

## Quota Tracking

The **QUOTA** panel tracks your API spend in real time:

- Per-session and cumulative cost tracking
- Per-model pricing database (updated for 2026 rates)
- Daily / weekly / monthly reset periods
- Hard cap enforcement — API calls block automatically when the limit is reached
- Full pricing table showing input and output costs for every supported model

---

## OCR

The OCR system supports two engines:

**PaddleOCR** — High-accuracy multilingual OCR using an ONNX model. Runs entirely in-browser via ONNX Runtime Web. Best for structured documents, mixed scripts, and tables.

**Tesseract.js** — Fallback engine with broad language pack support.

Drop any image into the OCR zone, or click **OCR** in the toolbar. The extracted text auto-populates the input field, ready to query.

---

## Architecture

```
aether/
├── index.html        ← Application shell, SVG icon library, all modals
├── script.js         ← Complete application logic (~6,500 lines)
├── style.css         ← Full design system, cyberpunk aesthetic (~4,400 lines)
├── sw.js             ← Service worker (offline cache, background sync)
├── manifest.json     ← PWA manifest with shortcuts and icons
└── logo.svg          ← Application icon
```

Everything ships in four files. No bundler. No framework. No node_modules. The entire codebase runs in a standards-compliant browser with zero compilation.

---

## License

```
AETHER Neural Interface
Copyright (C) 2026 The Architect

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

SPDX-License-Identifier: GPL-3.0-or-later
```

---

## Contributing

Pull requests are welcome. Before contributing:

1. Keep the zero-dependency architecture — no npm packages in the main files
2. All new UI must work on mobile (375px viewport minimum)
3. New tools belong in the `TOOL_REGISTRY` object in `script.js`
4. Maintain the single-file deployability of `index.html`

For bugs, open an issue with your browser version, provider, and the exact error from the browser console.

---

<div align="center">

**Built by The Architect · GPL-3.0 · No telemetry · No ads · No cloud lock-in**

*The neural interface your AI deserves.*

</div>

