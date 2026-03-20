# ⬡ AETHER Neural Interface

> Open-source AI — no backend, no account, no cost. GPL-3.0.

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Providers](https://img.shields.io/badge/Providers-22-00f3ff)]()
[![Qwen 3.5](https://img.shields.io/badge/Qwen3.5-262K_ctx-00ff88)]()
[![Agent Mode](https://img.shields.io/badge/Agent_Mode-v2-ffd700)]()

---

```
git clone https://github.com/architect-brad/AETHER.AI.git
cd AETHER.AI && open index.html
```

**That's it. Three files. No server.**

---

## Features at a Glance

| Feature | Status |
|---------|--------|
| Agent Mode v2 (plan→act→evaluate→retry + persistent workspace memory) | ✅ v5.14 |
| Whisper.js offline STT (WebGPU, no API key) | ✅ v5.14 |
| FLUX.2 image generation (inline display + inpainting) | ✅ v5.14 |
| Call Mode — "AETHER Calling" voice check-ins | ✅ v5.14 |
| Background scheduled tasks (daily/weekly recurring) | ✅ v5.14 |
| Location awareness (GPS + Nominatim geocoding) | ✅ v5.14 |
| Email sending (browser agent + anonymous mailto) | ✅ v5.14 |
| Animated loading states (7 cycling icons) | ✅ v5.14 |
| 22 providers (incl. Veo, Moondream2, FLUX.2, Nano Banana) | ✅ v5.14 |
| Qwen 3.5 native — 262K ctx, adaptive thinking | ✅ v5.13 |
| Browser automation (Browser Use + Playwright) | ✅ v5.13 |
| AES-256-GCM encrypted keys | ✅ v5.x |
| 17 built-in tools (3 syntaxes) | ✅ v5.x |

---

## Quick Start

```bash
# Local — Qwen 3.5 (free, private, 262K context)
./llama-server -m Qwen3.5-9B-Instruct-Q4_K_M.gguf --port 8080 -c 65536

# Or with Ollama
ollama pull qwen3.5:9b-instruct && ollama serve

# Or cloud — just open AETHER and enter any API key
```

---

## Call Mode

AETHER can call you. Click the **CALL** button. A full voice conversation UI opens:

- Pulsing avatar rings while connecting
- Context-aware greeting based on your workspace
- Waveform animation while AETHER speaks
- Voice recognition for your responses
- Mute, end, switch-to-chat controls
- Call transcript saved to conversation

> "AETHER Calling…" browser notification triggers before the UI opens.

---

## Agent Mode v2

```
AGENT → enter goal → set steps → run

AETHER:
  ⟨agent:plan⟩
  1. gitlab_issues → fetch open bugs
  2. prioritise by impact
  3. browser_agent → create Notion sprint
  ⟨/agent:plan⟩
  Step 1/10 — [[gitlab_issues: "AETHER.AI"]]
  ✓ Found 14 issues
  Step 2/10 — analysing…
  Step 3/10 — [[browser_agent: "create sprint in Notion"]]
  ⟨agent:done⟩Sprint created at notion.so/...⟩/agent:done⟩
```

Each step writes to `WORKSPACE.md` — resume after interruption, full cross-session memory.

---

## FLUX.2 Image Generation

```
"generate an image of a cyberpunk city at sunset"

→ FLUX.2 animated ring loader
→ Inline image result
→ Save ↓ | Edit ✏ | Regen ↺
```

Configure in SETUP → FLUX.2 provider + BFL API key.

---

## Background Scheduled Tasks

```
⏰ Schedule → Daily at 08:00:
"Check RAM prices and write a summary report"

Every morning at 8:00 AM:
  1. AETHER wakes up in the background
  2. Runs web_search for RAM prices
  3. Writes report to WORKSPACE.md + LOGS.md
  4. Sends push notification: "Morning report ready"
```

Use cases: price monitoring, Slack digest, Jira review, news summaries.

---

## Architecture

```
AETHER.AI/
├── index.html       # UI shell (~773 lines)
├── script.js        # All logic (~5830 lines)
├── style.css        # Design system (~4374 lines)
├── manifest.json    # PWA
├── sw.js            # Service worker
├── logo.svg         # Hexagon + lightning bolt
└── site.html        # Product hub
```

---

## Providers (22)

★ Preferred: Qwen (DashScope), DeepSeek  
Cloud: OpenAI, Anthropic, Google Gemini, Groq, xAI, Mistral, Cohere, OpenRouter, Kimi, Together AI, SiliconFlow, Perplexity AI, Meta AI, Microsoft Copilot, Fireworks  
New: Veo (video gen), Moondream2 (vision), FLUX.2 (image gen), Nano Banana (edge AI)  
Custom: Any OpenAI-compatible endpoint

---

## Tool Registry (21)

`web_search` `scrape` `crawl` `get_weather` `slack_post` `slack_read` `notion_query` `notion_add` `hue_lights` `hue_set` `jira_search` `jira_create` `gitlab_issues` `gitlab_mr` `read_file` `calculate` `browser_agent` `email_send` `location_get` `image_gen`

---

## Auth Auto-Detection

| Provider | Auth Method |
|----------|-------------|
| Anthropic | `x-api-key` + `anthropic-version` (auto) |
| Gemini | `?key=` URL param — never Bearer (auto) |
| OpenRouter | `HTTP-Referer` + `X-Title` (auto) |
| All others | `Authorization: Bearer YOUR_KEY` |

---

## Contributing

GPL-3.0. Fork → change → test → PR.

[Issues](https://github.com/architect-brad/AETHER.AI/issues) · [Discussions](https://github.com/architect-brad/AETHER.AI/discussions) · [PRs](https://github.com/architect-brad/AETHER.AI/pulls)

---

*⬡ AETHER — Neural Interface for the open web. GPL-3.0.*
