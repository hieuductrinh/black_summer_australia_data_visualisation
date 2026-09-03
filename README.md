# The 2019–2020 Black Summer: When Australia Burned

An interactive data-visualisation essay reconstructing the causes, scale, and consequences of the 2019–2020 Australian bushfire season, built with [Vega-Lite](https://vega.github.io/vega-lite/) and [Vega](https://vega.github.io/vega/) on a [Tufte CSS](https://edwardtufte.github.io/tufte-css/) narrative layout.

**Live site:** https://hughtrinh05.github.io/black_summer_australia_data_visualisation/

## Overview

The Black Summer bushfires burned over 24 million hectares, destroyed thousands of homes, and released more than 630 million tonnes of CO₂ into the atmosphere. This project tells that story through six linked charts and maps, structured as a three-chapter narrative:

1. **A Nation in Flames** — where the fires burned and how much native forest was lost, state by state
2. **A Perfect Storm Six Years in the Making** — the climate anomalies (temperature, rainfall, wind, solar radiation) that preceded the fires
3. **The Vicious Cycle** — the feedback loop between bushfire emissions and climate change

The visualisations are interactive: readers can filter the fire-area and native-forest charts with sliders, and hover over marks for tooltips.

## Features

- **Geospatial fire extent map** of the 2019–2020 fires overlaid on an Australian basemap
- **Interactive sliders** to filter states/regions by minimum burnt area, with live-formatted value labels
- **Time-series climate anomaly charts** (temperature, rainfall, wind speed, solar radiation) from 2013–2020
- **Combined weather-vs-burnt-area comparison** to visualise the lead-up to the fire season
- **CO₂ emissions heatmap** showing the monthly emissions spike during the fires
- Fully static, dependency-light build — no bundler or build step required

## Tech Stack

| Layer | Technology |
|---|---|
| Charting | [Vega](https://vega.github.io/vega/) 6, [Vega-Lite](https://vega.github.io/vega-lite/) 5.16, [vega-embed](https://github.com/vega/vega-embed) 6 |
| Styling | [Tufte CSS](https://edwardtufte.github.io/tufte-css/) (customised) |
| Markup | Static HTML, vanilla JavaScript (no framework) |
| Hosting | GitHub Pages |

All chart libraries are loaded via CDN (jsDelivr) — there is no `package.json` or build pipeline.

## Project Structure

```
├── index.html                  # Narrative structure and chart mount points
├── css/
│   └── tufte.css                # Customised Tufte CSS theme
├── js/
│   ├── fire_map.vl.json                     # Fire extent map spec
│   ├── fire_area.vg.json                    # Burnt area by state (with slider)
│   ├── burnt_native_forest_area.vl.json     # Native forest loss (with slider)
│   ├── weather_data_anomaly.vg.json         # Climate anomaly time series
│   ├── weather_anomaly_vs_burnt_area.vg.json # Weather vs. burnt area comparison
│   └── co2_emission_heatmap.vl.json         # CO₂ emissions heatmap
├── data/                        # Source CSV/JSON/GeoJSON datasets
└── Five Design Sheet.pdf        # Design process documentation (FDS methodology)
```

Each chart is defined as a standalone Vega/Vega-Lite JSON specification in `js/`, embedded into its corresponding `<figure>` in `index.html` via `vegaEmbed`.

## Running Locally

This is a static site with no build step. Any local web server will work — for example:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

A local server is required (rather than opening `index.html` directly) so the browser can fetch the JSON data and chart specs without CORS restrictions.

## Data Sources

| Dataset | Source | License |
|---|---|---|
| Fire extent | [Department of Climate Change, Energy, the Environment and Water](https://fed.dcceew.gov.au/datasets/erin::national-indicative-aggregated-fire-extent-dataset/about) | CC-BY 3.0 |
| Basemap | [Natural Earth](https://www.naturalearthdata.com/) | CC0 1.0 |
| Burnt area / native forest loss | [Department of Agriculture, Fisheries and Forestry](https://www.agriculture.gov.au/abares/forestsaustralia/forest-data-maps-and-tools/data-by-topic/fire) | CC-BY 4.0 |
| Historical weather / climate anomalies | [Bureau of Meteorology](ftp://ftp.bom.gov.au/anon/gen/) | BOM copyright notice |
| CO₂ emissions | [Nature Scientific Reports](https://www.nature.com/articles/s41598-021-87721-x) (Springer Nature Limited) | CC-BY 4.0 |

Full citations and retrieval dates are included as footnotes under each chart in `index.html`.

## Design Process

The design and iteration process — including sketches, alternative encodings, and rationale for the final chart choices — is documented in [`Five Design Sheet.pdf`](./Five%20Design%20Sheet.pdf), following the [Five Design Sheet (FDS) methodology](https://www.fdsmethod.org/).

## Acknowledgements

- **AI assistance:** ChatGPT 5 and Claude Sonnet 4.5 were used to assist with debugging and refining Vega/Vega-Lite code, explaining syntax, and improving grammar/clarity. All data collection, data wrangling, and chart design were carried out independently by the author.
- **Frameworks:** Built on a modified version of [Tufte CSS](https://edwardtufte.github.io/tufte-css/) by Dave Liepmann and contributors, under the MIT License.

## Author

**Hugh Trinh**
Published 21 October 2025
