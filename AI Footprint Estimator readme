# AI Footprint Estimator

An interactive tool to estimate the energy consumption, carbon emissions, and water usage of various AI operations — adjusted to your local electricity grid and compute location.

## Overview

This tool helps you understand the environmental cost of using different AI services. Move sliders to match your actual AI usage patterns, select your region and compute location, and see estimates for:

- **Energy** (kWh)
- **CO₂ emissions** (kg CO₂e)
- **Water usage** (liters)

All numbers are **order-of-magnitude estimates** useful for comparison, not for compliance reporting.

## Features

- **Granular operation tracking**: 15+ AI tasks from simple searches to frontier model training
- **Region-aware**: Country and sub-national (state/province) electricity grid data
- **Compute location presets**: Major cloud provider regions (AWS, Azure, GCP)
- **Model selection**: Choose specific AI models (Claude, GPT-4o, Llama, etc.) for precise estimates
- **Multiple time scales**: Per-day, week, month, year, or one-time calculations
- **Comparison views**: Simple overview or detailed per-operation breakdown
- **Shareability**: Copy a link encoding your exact scenario

## Usage

1. Open `index.html` in a web browser
2. **Region**: Auto-detects your location; adjust if needed
3. **Compute location**: Select where the AI compute likely runs
4. **Operations**: Use sliders to set your usage frequency
5. **Models**: Pick specific AI models if available
6. **Results**: View annual footprint and equivalencies

### Frequency Options

- **Per day**: Annualized (×365)
- **Per week**: Annualized (×52)
- **Per month**: Annualized (×12)
- **Per year**: No scaling
- **One-time event**: Single calculation

## Operations Included

### Everyday AI Use
- AI-powered web search
- Quick AI question (small models)
- Detailed AI answer (large models)
- RAG-augmented queries
- Code completion / IDE autocomplete
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

- **Inference energy**: Luccioni et al. (2024), provider model cards, Hugging Face AI Energy Score
- **Training energy**: Patterson et al. (2021), Strubell et al., de Vries
- **Grid carbon intensity**: Ember Yearly Electricity Data 2024, EPA eGRID, IEA, CER, DCCEEW
- **Water usage**: Li et al. (2023)
- **Equivalencies**: EPA Greenhouse Gas Equivalencies Calculator

## What's Included

✅ Operational compute energy (CPU/GPU/TPU)  
✅ Datacenter cooling & overhead (PUE ≈ 1.12)  
✅ Carbon from your local electricity grid  
✅ Direct cooling water at the datacenter  
✅ Embodied energy, carbon, and water — manufacturing GPUs and servers, building the datacenter, end-of-line semiconductor fab water. Added as mid-range multipliers on top of operational: +12% energy, +15% carbon, +25% water.

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
- **Model estimates**: Not vendor-confirmed for every model; based on public benchmarks

## Technical Stack

- **Vanilla JavaScript** (no frameworks)
- **Chart.js** for visualizations
- **HTML5 + CSS3** for responsive design
- **Timezone-based geolocation** for region detection

## Files

- `index.html` — Complete application (HTML, CSS, JavaScript inline)

## Dependencies

- **Chart.js 4.5.0** (via CDN)
- Modern web browser (ES6+ JavaScript support)

## Browser Support

Tested on recent versions of:
- Chrome/Edge
- Firefox
- Safari

## Sharing

Click **"🔗 Copy share link"** to generate a URL that encodes your exact scenario (all slider values, model choices, region, frequency). Share with others to compare results.

## Reset

Click **"↻ Reset"** to return all sliders, models, and selections to defaults.

## View Modes

- **Simple**: Clean view with equivalencies (e.g., "X car miles")
- **Detailed**: Full per-operation breakdown table and methodology

## Questions & Feedback

- **GitHub**: [github.com/drewwheadon-hub](https://github.com/drewwheadon-hub)
- **Built by**: Opus 4.7 with direction from Drew Wheadon

## License

MIT Licence 

## Methodology Note

All calculations assume mid-range public figures. Estimates reflect operational carbon and water only. See the **"What this tool does and doesn't include"** section in the tool itself for detailed caveats.

---

**Last updated**: May 2026 (electricity grid estimates current through November 2024)
