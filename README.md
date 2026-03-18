<div align="center">

```
    ╔═══════════════════════════════════════════════════════╗
    ║  ⬡  A E T H E R   N E U R A L   I N T E R F A C E  ║
    ║                      v 5 . 1 4                        ║
    ╚═══════════════════════════════════════════════════════╝
```

**Open-source AI interface built to compete with OpenClaw.**
Fully local. Fully open. No compromises. No backend.

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-00f3ff.svg?style=flat-square)](https://www.gnu.org/licenses/gpl-3.0)
[![Version](https://img.shields.io/badge/version-5.14-00ff88.svg?style=flat-square)](https://github.com/architect-brad/AETHER.AI/releases)
[![Status](https://img.shields.io/badge/status-active-00ff88.svg?style=flat-square)](#)
[![Preferred AI](https://img.shields.io/badge/preferred-Qwen%203.5%20%E2%AC%A1-00ff88.svg?style=flat-square)](#qwen-35--qwen-3-native-support)

[**Launch App**](https://architect-brad.github.io/AETHER.AI/) · [**Documentation**](https://architect-brad.github.io/AETHER.AI/site.html) · [**Report Bug**](https://github.com/architect-brad/AETHER.AI/issues)

</div>

---

## What is AETHER?

AETHER is a precision AI interface that runs entirely in the browser — three files, zero backend, zero telemetry. Connect any OpenAI-compatible API, run local models, or use cloud providers. Built to compete directly with OpenClaw while remaining fully free under GPL-3.0.

**Why AETHER over alternatives?**

| Feature | AETHER | Typical alternatives |
|---------|--------|---------------------|
| **Backend required** | ❌ None | ✅ Required |
| **API key encryption** | AES-256-GCM | Plaintext / none |
| **Qwen 3.5 native** | Full (262K, thinking) | Partial / none |
| **Tool calling** | 16 tools, 3 syntaxes | 0–5 tools |
| **Local model support** | llama.cpp, Ollama, vLLM | Limited |
| **License** | GPL-3.0 free | Proprietary |
| **File count** | 3 | Many |

---

## ⚡ Quick Start

### Option 1 — Local model (free, private)

```bash
# Download Qwen3.5-9B GGUF
wget https://huggingface.co/bartowski/Qwen_Qwen3.5-9B-Instruct-GGUF/resolve/main/Qwen3.5-9B-Instruct-Q4_K_M.gguf

# Start llama.cpp server
./llama-server -m Qwen3.5-9B-Instruct-Q4_K_M.gguf --port 8080 -c 65536 --mlock

# Or use Ollama
ollama run qwen3.5:9b-instruct
```

Open `index.html` — AETHER connects automatically at `localhost:8080`.

### Option 2 — Cloud API

1. Open AETHER → click **SETUP**
2. Select your provider from the logo grid
3. Enter API key → encrypted with AES-256-GCM immediately
4. Pick a model from the suggestion chips
5. Click **SAVE CONFIG**

---

## ⬡ Qwen 3.5 + Qwen 3 Native Support

AETHER is purpose-engineered for the Qwen model families — the recommended local-first AI stack.

### Qwen 3.5 Series — Gated DeltaNet + Early Fusion

> *"The best small model architecture of 2026"* — Trilogy AI Deep Dive

| Model | Parameters | Active | Architecture | Context | Best For |
|-------|-----------|--------|-------------|---------|----------|
| `qwen3.5-0.8b-instruct` | 0.8B | 0.8B | GDN+FFN | 262K | Edge / mobile |
| `qwen3.5-2b-instruct` | 2B | 2B | GDN+FFN | 262K | Constrained hardware |
| `qwen3.5-4b-instruct` | 4B | 4B | GDN+FFN | 262K | Balanced |
| `qwen3.5-9b-instruct` | 9B | 9B | GDN+FFN | 262K | **Recommended** |
| `qwen3.5-25b-instruct` | 25B | 25B | GDN+FFN | 262K | High quality |
| `qwen3.5-35b-a3b-instruct` | 35B | **3B** | **MoE 256E/8A** | 262K | Best quality, fast |

**Key capabilities** (all models):
- **262K native context** via Gated DeltaNet linear-attention architecture
- **Adaptive Thinking** — native `<think>` tags, enabled via `enable_thinking: true`
- **Early Fusion multimodality** — vision and text trained together from layer zero
- **MTP speculative decoding** — auto-injected `num_speculative_tokens: 4`
- Compatible with: vLLM, llama.cpp GGUF, MLC-LLM, Ollama

### Qwen 3 Base Series

| Model | Context | Notes |
|-------|---------|-------|
| `qwen3-0.6b-instruct` | 32K | Ultra-lightweight |
| `qwen3-1.7b-instruct` | 32K | — |
| `qwen3-4b-instruct` | 128K | — |
| `qwen3-8b-instruct` | 128K | Recommended local |
| `qwen3-14b-instruct` | 128K | — |
| `qwen3-32b-instruct` | 128K | High quality |
| `qwen3-235b-a22b-instruct` | 128K | Cloud (Together AI / SiliconFlow) |

---

## 🔧 Features

### Core Interface
- **Real-time streaming** with TTFT and TPS metrics
- **Dual Context** — run two parallel conversations simultaneously
- **Conversation history** in IndexedDB via localforage
- **BM25 + Vector RAG** — semantic document retrieval with cosine similarity
- **KaTeX math rendering** — LaTeX `$inline$` and `$$display$$`
- **Mermaid diagrams** — flowcharts, sequence diagrams, gantt charts
- **OCR Vision** — Tesseract.js image text extraction
- **ASCII 3D Renderer** *(Experimental)* — raymarched SDF scenes with multi-light shading
- **Canvas Workbench** *(Experimental)* — freehand drawing, annotation, PDF rendering

### AI Integration
- **12 cloud providers** with official SVG logos and auto-endpoint configuration
- **Anthropic native** — `x-api-key` header, extended thinking, tool use with `input_schema`
- **Google Gemini** — `?key=` query parameter auth (not Bearer), OpenAI-compat endpoint
- **OpenRouter** — auto-injects `HTTP-Referer` and `X-Title` headers
- **Adaptive Thinking** — live `<think>` streaming with token counter

### ⚛ Deep Research Mode
Multi-step reasoning chains using DeepSeek Reasoner or Qwen3.5 as preferred models:
1. Query decomposition via extended chain-of-thought
2. Automatic tool dispatch (web search → scrape → database query)
3. Synthesis with structured, cited output
4. Cross-verification by reasoning model

### 🛠 Tool Calling Engine
16 built-in tools, 3 syntax parsers, OpenAI function-call dispatch:

```
web_search      scrape          crawl           get_weather
slack_post      slack_read      notion_query    notion_add
hue_lights      hue_set         jira_search     jira_create
gitlab_issues   gitlab_mr       read_file       calculate
```

Parses: ` ```tool_call `, `<tool_call name="">`, `[[tool: value]]`

### Integrations (20+)

| Category | Providers |
|----------|-----------|
| Search | Tavily, Brave, Serper |
| Web Scraping | **Firecrawl** (scrape + crawl) |
| Communication | Slack, Gmail, Outlook |
| Productivity | Notion, Jira Cloud |
| Development | GitHub, GitLab |
| Smart Home | Philips Hue (OpenHue) |
| Cloud Platforms | Google Workspace, Microsoft 365 |
| Weather | OpenWeatherMap |

### Security
- **AES-256-GCM** encryption for all API keys
- **PBKDF2** key derivation (100,000 iterations)
- Zero plaintext storage, zero telemetry
- All processing client-side

### TTS / Voice
Three engines configurable in HOOKS:
- **Browser API** — zero setup, basic quality
- **Kokoro 82M** — on-device via Hugging Face Transformers.js
- **Piper** — high quality via local server

### Personalization
8-step onboarding wizard:
- Name, interests, personality (8 personas: Nova, Sage, Spark, Cipher, Echo, Nexus, Vector, Herald)
- Response style (Concise/Balanced/Detailed)
- Preferred AI model selection
- Privacy & features configuration

Persona shapes every system prompt automatically.

---

## 🏗 Architecture

```
AETHER v5.14
├── index.html    — App shell, SVG sprite, modals (706 lines)
├── script.js     — All logic, API integration, tools (4200+ lines)
└── style.css     — Full design system, cyberpunk OLED (3900+ lines)
```

**Zero runtime dependencies** — everything runs in the browser:

| Layer | Technology |
|-------|-----------|
| Storage | localforage (IndexedDB) + localStorage |
| Crypto | Web Crypto API (AES-256-GCM + PBKDF2) |
| Rendering | Vanilla DOM + CSS custom properties |
| Search | BM25 (pure JS) |
| Math | KaTeX (CDN, lazy) |
| OCR | Tesseract.js (CDN, lazy) |
| Diagrams | Mermaid (CDN, lazy) |
| TTS (optional) | Kokoro 82M via HuggingFace Transformers.js |

---

## API Providers

| Provider | Priority | Auth Method | Notes |
|----------|----------|-------------|-------|
| **Qwen (DashScope)** | ★ Preferred | Bearer | Best local pairing |
| **DeepSeek** | ★ Preferred | Bearer | Best for reasoning |
| Local (llama.cpp/Ollama) | Default | None | Zero cost |
| OpenAI | Supported | Bearer | GPT-5 era models |
| Anthropic | Supported | `x-api-key` | Auto-detected, Claude 4.6 |
| Google Gemini | Supported | `?key=` param | Auto-detected, Gemini 3 |
| Groq | Supported | Bearer | Ultra-fast inference |
| xAI | Supported | Bearer | Grok 4 |
| Mistral | Supported | Bearer | Large 3 |
| OpenRouter | Supported | Bearer + Referer | Multi-provider routing |
| Kimi (Moonshot) | Supported | Bearer | K2.5, 256K context |
| Custom | Any | Configurable | Any OpenAI-compat endpoint |

---

## Development

### Running locally

```bash
# Serve with any static file server
npx serve .
# or
python3 -m http.server 3000
# or just open index.html directly
```

### PWA Installation

```bash
# Add manifest.json + sw.js to enable offline PWA
cp manifest.json sw.js /path/to/your/deployment/
```

### Contributing

1. Fork the repository
2. Make your changes in `script.js`, `style.css`, or `index.html`
3. Test against Qwen3.5 local and at least one cloud API
4. Submit a PR — all contributions must maintain GPL-3.0

---

## Roadmap

- [ ] Multi-modal image generation (FLUX/SDXL via Puter)
- [ ] Voice input (Whisper local via Transformers.js)
- [ ] Plugin system (AETHER Extensions API)
- [ ] Collaborative sessions (WebRTC)
- [ ] Mobile app wrapper (Capacitor)
- [ ] Advanced RAG (vector DB, hybrid retrieval)
- [ ] Agent mode (autonomous multi-step tasks)

---

## License

```
AETHER Neural Interface
Copyright (C) 2026  The Architect

GNU General Public License v3.0
https://www.gnu.org/licenses/gpl-3.0
```

This is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or any later version.

---

<div align="center">
<br>
<strong>⬡ AETHER v5.14</strong> · Built by The Architect · GPL-3.0 · Competing with OpenClaw
<br><br>
<a href="https://architect-brad.github.io/AETHER.AI/">🌐 Website</a> ·
<a href="https://architect-brad.github.io/AETHER.AI/site.html">📖 Docs</a> ·
<a href="https://github.com/architect-brad/AETHER.AI/issues">🐛 Issues</a> ·
<a href="https://github.com/architect-brad/AETHER.AI/discussions">💬 Discussions</a>
</div>
