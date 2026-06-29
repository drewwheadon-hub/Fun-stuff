# AI Footprint Estimator

An interactive tool to estimate the **energy consumption**, **carbon emissions**, and **water usage** of various AI operations adjusted to your local electricity grid and water use variables.

## Overview

This tool helps you understand the environmental cost of using different AI services. Move sliders to match your actual AI usage patterns, select your region and compute location, and see instant estimates for:

- **Energy** (kWh)
- **CO₂ emissions** (kg CO₂e)
- **Water usage** (liters)

All numbers are **order-of-magnitude estimates** and useful for comparison, not for compliance reporting.

## Features

- **17 everyday AI operations**: from AI web search to code completion to voice synthesis
- **Custom AI workflows**: fine-tuning and training from scratch (LoRA, full fine-tune, GPT-3-class, frontier models)
- **Region-aware carbon intensity**: 
  - 60+ countries with 2023 generation averages
  - Sub-national precision: US states (eGRID 2024), Canadian provinces, Australian states, Chinese regional grids
- **Compute location presets**: 
  - Major cloud providers (AWS, Azure, GCP with specific regions)
  - AI-lab estimated blends (Anthropic, OpenAI, Google Gemini)
  - Or use your local grid
- **Model-specific energy**: 
  - Open models measured on Hugging Face AI Energy Score (Dec 2025)
  - Proprietary models with mid-range estimates
  - Covers Claude, GPT-4o, Gemini, Llama, Mistral, Gemma, Stable Diffusion, and others
- **Multiple time scales**: per-day, per-week, per-month, per-year, or one-time calculations
- **Operational + Embodied toggle**: See operational-only or add manufacturing/datacenter-building impact
- **Extended thinking & reasoning modes**: Multiplier for advanced reasoning models (×30 energy multiplier)
- **Two view modes**: 
  - Simple: clean layout with everyday equivalencies
  - Detailed: full per-operation breakdown table + methodology
- **Comparison mode**: Snapshot scenario A, edit to create B, and see side-by-side deltas
- **Shareable links**: Encode your exact scenario (all slider values, models, region, frequency) into a URL
- **Responsive design**: Works on desktop, tablet, and mobile (with sticky results bar on mobile)

## Usage

1. **Open** `index.html` in a modern web browser
2. **Region**: Auto-detects via timezone; adjust as needed
3. **Subregion** (if available): US states, Canadian provinces, Australian states, or Chinese regional grids for finer accuracy
4. **Compute location**: Select where the AI compute likely runs (major cloud regions, AI-lab blends, or your local grid)
5. **Frequency**: Choose annualization (per-day ×365, per-week ×52, per-month ×12, per-year, or one-time)
6. **Model picker**: For inference operations, select a specific model for precise energy figures
7. **Reasoning mode**: For advanced reasoning models, toggle reasoning mode to apply ×30 energy multiplier
8. **Sliders**: Adjust quantities for each AI operation
9. **Results**: View annual (or one-time) energy, CO₂, and water; toggle between simple and detailed views
10. **Compare**: Click "📊 Compare" to freeze your current scenario and edit to see deltas
11. **Share**: Click "🔗 Copy share link" to generate a shareable URL

## Operations Included

### Everyday AI Use (12 operations)

| Operation | Description | Examples |
|-----------|-------------|----------|
| **AI-powered web search** | Search with AI summary | Google AI Overviews, Bing Copilot search, Perplexity |
| **Quick AI question** | Short reply from fast model | Claude Haiku, GPT-4o mini, Gemini Flash, Apple Intelligence |
| **Detailed AI answer** | Thoughtful reply from top-tier model | ChatGPT (GPT-4/5), Claude Sonnet/Opus, Gemini Pro/Ultra |
| **RAG-augmented answer** | AI searches docs, then answers | ChatGPT with knowledge files, internal chatbots, Notion Q&A |
| **Code suggestion** | In-IDE autocomplete | GitHub Copilot, Cursor, Tabnine, Amazon Q Developer |
| **Embedding / semantic search** | Convert text to vector for search | Algolia AI, ChatGPT custom GPT retrieval, recommendation engines |
| **AI voice / audio (per minute)** | Transcription, TTS, music gen | Whisper, ElevenLabs, Suno, Udio, ChatGPT voice mode |
| **AI-generated image** | Picture from text prompt | Midjourney, DALL·E, Stable Diffusion, Adobe Firefly |
| **AI-generated video (per second)** | Video from prompt or clip | OpenAI Sora, Google Veo, Runway Gen-3 |
| **AI agents (quick task)** | Multi-step autonomous task (~10 calls) | Inbox sorting, doc summarization, scheduling |
| **AI agents (complex task)** | Extended multi-step task (~100 calls) | Report writing, coding agent, web browsing operator |

### Custom AI for Your Data (2 operations)

| Operation | Description | Examples |
|-----------|-------------|----------|
| **Fine-tune small scale** | LoRA on ~7B-parameter model | Support ticket chatbot, branded writing assistant |
| **Fine-tune large scale** | Full fine-tune on ~70B-parameter model | Hospital clinical assistant, law firm contract reviewer |

### Building AI from Scratch (3 operations)

| Operation | Description | Examples |
|-----------|-------------|----------|
| **Small specialized AI** | BERT-base-scale (~110M params) from zero | Academic research, narrow industry tools |
| **ChatGPT-class AI** | GPT-3-scale (~175B params) from zero | Large corporate LLM effort (months on thousands of GPUs) |
| **Frontier/"edge" AI** | Latest cutting-edge model | GPT-4, Claude Opus, Gemini Ultra-class (only major labs) |

## Data & Methodology

### Sources

- **Inference energy (kWh/query)**: 
  - Open models: Hugging Face AI Energy Score (Dec 2025 leaderboard), measured on NVIDIA H100
  - Proprietary models: Anchored to public benchmarks and Google's 2025 Gemini disclosure (~0.24 Wh / median text prompt)
- **Training energy**: Patterson et al. (2021), Strubell et al., de Vries & Khanna, Microsoft sustainability reports
- **Grid carbon intensity (gCO₂/kWh)**: 
  - Countries: Ember Yearly Electricity Data 2024, IEA Electricity 2024
  - US states: Cornerstone eGRID 2024 community release (March 2026, pending official EPA eGRID2024)
  - Canadian provinces: Canada Energy Regulator / NIR 2023
  - Australian states: DCCEEW National Greenhouse Accounts 2023
  - China: Ministry of Ecology & Environment Regional Grid factors (2023)
- **Water usage**: 
  - On-site WUE (L/kWh): Ren et al. "Making AI Less Thirsty" (CACM 2025), climate-banded model (cold 0.2, cool 0.55, warm 0.85, hot-humid 1.4, hot-arid 1.75 L/kWh)
  - Off-site (electricity-generation) EWIF: Macknick et al. (NREL) technology factors + regional grid mix
  - Microsoft global average reference: 0.30 L/kWh (FY24, down from FY21's 0.49)
- **Equivalencies**: EPA Greenhouse Gas Equivalencies Calculator

### What's Included ✅

- **Operational compute energy** (CPU/GPU/TPU)
- **Datacenter cooling & overhead** (typical hyperscale PUE ≈ 1.12)
- **Carbon based on your grid mix** (country, sub-region, or specific cloud region)
- **Water**: on-site cooling at datacenter + scope-2 water from electricity generation
- **Embodied energy, carbon, and water** (when toggled on via "Scope → + Embodied"):
  - Manufacturing GPUs, servers, and datacenter buildings
  - End-of-line semiconductor fab water
  - Applied as: +12% energy, +15% carbon, +25% water (mid-range multipliers)
- **Reasoning model multiplier**: ×30 energy for extended thinking / reasoning modes

### What's Not Included ❌

- **Network transit & end-user device energy** — ISP, transit providers, your laptop/phone. Small per query but not modeled.
- **Training-cost amortization** — For ChatGPT (popular), training ÷ billions of queries ≈ negligible. For niche models, training cost can dominate.
- **Provider sustainability claims** — This tool uses physical grid intensity, not "as-reported net-zero" or renewable-energy credits.
- **End-of-life e-waste** — Retiring GPUs every 3–5 years creates waste streams beyond embodied figures.
- **Query-specific variations** — Output length, context window, and reasoning depth can swing per-query energy by 10–100×. Figures here are mid-range averages.

### Limitations

- **Order-of-magnitude estimates**: Useful for comparison; actual costs vary widely
- **Mid-range averages**: Per-query energy ±40% (measured), ±2× (derived), ±3× (rough/limited data)
- **Aggregated data**: Sub-national grids, seasonal variation, specific datacenter PUE not fully modeled
- **Model estimates**: Not vendor-confirmed; based on public benchmarks and AI Energy Score leaderboard
- **Embodied percentages**: Fixed multipliers; actual embodied share grows as operational decarbonizes
- **Reasoning multiplier**: ×30 is a rough estimate; actual overhead varies by model and implementation

## Models Available

### Small Models (Inference)

**Open models (measured on H100)**:
- Llama 3.1 8B, Mistral 7B, Gemma 2 2B, Microsoft Phi-4, SmolLM2 1.7B

**Proprietary (estimates)**:
- Claude Haiku, GPT-4o mini, Gemini Flash

### Large Models (Inference)

**Open models (measured on H100)**:
- Llama 3 70B, Qwen2.5 72B, Mixtral 8x7B, gpt-oss-120B reasoning

**Proprietary (estimates)**:
- Claude Sonnet, Claude Opus, GPT-4o, GPT-5, Gemini 2.5 Pro

### Image Generation

**Open models (measured)**:
- Stable Diffusion XL, SDXL Turbo, Stable Diffusion 2.1, Stable Cascade

**Proprietary (estimates)**:
- DALL·E 3, Midjourney v6, Adobe Firefly

## Quick Presets

Click a preset to populate all sliders with representative usage patterns:

- **Light user** — 3 searches, 5 quick Q&As, 2 detailed answers, 1 image per day; casual user
- **Typical** (default) — Moderate daily AI use (~10 searches, 20 quick Q&As, 10 detailed answers, 5 images)
- **Power user** — Heavy daily usage; writer, marketer, knowledge worker
- **Software dev** — In-IDE code assist, chat, embeddings, light agent tasks
- **Image creator** — Designer making AI images and short video clips
- **Researcher** — Long-form chat, RAG, embeddings, occasional fine-tuning

## Comparison & Sharing

- **Compare**: Click "📊 Compare" to freeze your current scenario as **A**. Edit anything to see **B** compared against it. Shows deltas in energy, CO₂, and water.
- **Share**: Click "🔗 Copy share link" to generate a URL encoding all your choices (sliders, models, region, frequency, scope). Paste to share your exact scenario.
- **Reset**: Click "↻ Reset" to restore all sliders and selections to defaults.

## View Modes

- **Simple**: Clean layout emphasizing totals and everyday equivalencies (gas miles, shower, flights, etc.)
- **Detailed**: Full per-operation breakdown table, extended methodology notes, all sources and caveats

## Technical Stack

- **Vanilla JavaScript** (no frameworks or build tools)
- **Chart.js 4.5.0** — for the energy comparison bar/doughnut chart
- **HTML5 + CSS3** — responsive design with mobile sticky results bar
- **Timezone-based geolocation** — auto-detect region

## Files

- `index.html` — Complete single-file application (HTML, CSS, JavaScript inline)
- `README.md` — This file

## Dependencies

- **Chart.js 4.5.0** (via CDN: jsdelivr)
- Modern web browser with ES6+ JavaScript support

## Browser Support

Tested on recent versions of:
- Chrome / Chromium / Edge
- Firefox
- Safari

## License

MIT License

## Built By

- **Copilot (Claude, Opus 4.7)** — AI assistant, implementation
- **Drew Wheadon** — Direction, concept, validation

## Feedback & Questions

- **GitHub**: [github.com/drewwheadon-hub](https://github.com/drewwheadon-hub)
- **This tool**: Estimation only, not for compliance reporting or contractual carbon accounting

---

**Last updated**: June 2026  
**Data currency**: 
- Electricity grid estimates: 2023 generation averages (US states updated to Cornerstone eGRID 2024 community release, March 2026)
- Model energy benchmarks: December 2025 (Hugging Face AI Energy Score)
- Water modeling: June 2026 (climate-banded on-site WUE refinement)
