# AI Footprint Estimator

An interactive tool to estimate the energy consumption, carbon emissions, and water usage of various AI operations — adjusted to your local electricity grid and compute location.

## Overview

This tool helps you understand the environmental cost of using different AI services. Move sliders to match your actual AI usage patterns, select your region and compute location, and see estimates updated in real time for:

- **Energy** (kWh)
- **CO₂ emissions** (kg CO₂e)
- **Water usage** (liters)

All numbers are **order-of-magnitude estimates** useful for comparison, not for compliance reporting.

## Features

- **Granular operation tracking**: 17 AI tasks from simple searches to frontier model training
- **Region-aware**: Country and sub-national (state/province) electricity grid data
- **Compute location presets**: Major cloud provider regions (AWS, Azure, GCP) plus AI-specific blends
- **Model selection**: Choose specific AI models (Claude, GPT-4o, Llama, Mistral, Gemma, etc.) for precise estimates
- **Multiple time scales**: Per-day, week, month, year, or one-time calculations
- **Operational and embodied**: Toggle between operational-only or operational + embodied carbon/water
- **Comparison views**: Simple overview with equivalencies or detailed per-operation breakdown
- **Shareability**: Copy a link encoding your exact scenario
- **Responsive design**: Works on desktop, tablet, and mobile

## Usage

1. Open `index.html` in a web browser
2. **Region**: Auto-detects your location; adjust if needed
3. **Subregion**: For US, Canada, Australia, and China — select your state/province/grid for finer accuracy
4. **Compute location**: Select where the AI compute likely runs (major cloud regions or AI-lab blends)
5. **Frequency**: Choose how often you perform each operation (defaults to annualized)
6. **Model picker**: For inference operations, select a specific model if available
7. **Results**: View annual (or one-time) footprint and equivalencies; toggle between simple and detailed modes

### Frequency Options

- **Per day**: Annualized (×365)
- **Per week**: Annualized (×52)
- **Per month**: Annualized (×12)
- **Per year**: No scaling
- **One-time event**: Single calculation

## Operations Included

### Everyday AI Use (17 operations)

- AI-powered web search
- Quick AI question (small models)
- Detailed AI answer (large models)
- RAG-augmented queries
- Code suggestion / IDE autocomplete
- Embeddings / semantic search
- AI voice / audio (per minute)
- AI-generated images
- AI-generated video (per second)
- AI agents (quick & complex tasks)

### Custom AI for Your Data

- Fine-tune small scale (LoRA)
- Fine-tune large scale (full weights)

### Building AI from Scratch

- Small specialized AI
- ChatGPT-class model
- Frontier/"edge" AI model

## Data Sources

- **Inference energy**: Luccioni et al. (2024), provider model cards, Hugging Face AI Energy Score (Dec 2025 leaderboard)
- **Training energy**: Patterson et al. (2021), Strubell et al., de Vries
- **Grid carbon intensity**: Ember Yearly Electricity Data 2024, EPA eGRID 2022, IEA, CER, DCCEEW
- **Water usage**: Li et al. (2023), Ren et al. "Making AI Less Thirsty" (CACM 2025)
- **Equivalencies**: EPA Greenhouse Gas Equivalencies Calculator

## What's Included

✅ Operational compute energy (CPU/GPU/TPU)  
✅ Datacenter cooling & overhead (PUE ≈ 1.12)  
✅ Carbon from your local electricity grid  
✅ Direct cooling water at the datacenter  
✅ Embodied energy, carbon, and water (when toggled on) — manufacturing GPUs and servers, building the datacenter, end-of-line semiconductor fab water. Added as mid-range multipliers: +12% energy, +15% carbon, +25% water  

## What's Not Included

❌ Network transit and end-user device energy  
❌ Training-cost amortization across billions of users  
❌ Provider sustainability claims (focuses on physical grid mix)  
❌ End-of-life e-waste  
❌ Query-specific variations (output length, context size)  

## Limitations

- **Order-of-magnitude estimates**: Useful for comparison, not precise accounting
- **Mid-range averages**: Actual per-query energy varies 10–100× depending on output length, reasoning depth, and hardware
- **Aggregated data**: Sub-national grids, seasonal variation, and specific datacenter PUE not fully captured
- **Model estimates**: Not vendor-confirmed for every model; based on public benchmarks and Hugging Face AI Energy Score
- **Embodied assumptions**: Uses fixed percentage multipliers; actual embodied share grows as operational decarbonizes

## Technical Stack

- **Vanilla JavaScript** (no frameworks)
- **Chart.js 4.5.0** for visualizations
- **HTML5 + CSS3** for responsive design
- **Timezone-based geolocation** for region detection

## Files

- `index.html` — Complete application (HTML, CSS, JavaScript inline)

## Dependencies

- **Chart.js 4.5.0** (via CDN: jsdelivr)
- Modern web browser (ES6+ JavaScript support)

## Browser Support

Tested on recent versions of:
- Chrome/Chromium/Edge
- Firefox
- Safari

## Model Selection

The tool includes specific energy measurements for popular AI models, sourced from:

- **Open models (measured)**: Hugging Face AI Energy Score leaderboard (December 2025), measured on NVIDIA H100
  - Small: Claude Haiku, Llama 3.1 8B, Mistral 7B, Gemma 2 2B, Phi-4, SmolLM2
  - Large: Llama 3 70B, Qwen2.5 72B, Mixtral 8x7B, gpt-oss-120B
  - Images: Stable Diffusion XL, SDXL Turbo, Stable Diffusion 2.1, Stable Cascade

- **Proprietary models (estimates)**: Claude (Haiku, Sonnet, Opus), OpenAI (GPT-4o mini, GPT-4o, GPT-5), Google (Gemini Flash, Gemini 2.5 Pro), DALL·E 3, Midjourney, Adobe Firefly

## Sharing

Click **"🔗 Copy share link"** to generate a URL that encodes your exact scenario (all slider values, model choices, region, frequency, scope). Share with others to compare results.

## Reset

Click **"↻ Reset"** to return all sliders, models, and selections to defaults.

## View Modes

- **Simple**: Clean view with CO₂ equivalencies (e.g., "X car miles", "X gallons of gasoline")
- **Detailed**: Full per-operation breakdown table and extended methodology notes

## Questions & Feedback

- **GitHub**: [github.com/drewwheadon-hub](https://github.com/drewwheadon-hub)
- **Built by**: Opus 4.7 with direction from Drew Wheadon

## License

MIT License

## Methodology Note

All calculations assume mid-range public figures. Estimates reflect operational carbon and water only unless the **+ Embodied** scope is toggled on. See the **"What this tool does and doesn't include"** section in the tool itself for detailed methodology and limitations.

---

**Last updated**: May 2026 (electricity grid estimates current through November 2024; model energy benchmarks from December 2025)
