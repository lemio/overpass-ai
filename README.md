# Overpass AI

Ask geographic questions in plain language and see the results on a map, powered by OpenAI and the Overpass API for OpenStreetMap.

## Features

- Convert natural-language geographic questions into Overpass QL queries
- Generate up to 3 query variants highlighted in distinct colours (D3 schemeCategory10)
- Show results on an interactive Leaflet map and in a synchronized list panel
- Brush selection on the map and click selection in the list
- OSM wiki tag references with explanations for every tag used
- Export selected (or all) results to a GPX file
- Dark-mode professional UI

## Getting Started

### Prerequisites

- A modern web browser (Chrome, Firefox, Edge, Safari)
- An [OpenAI API key](https://platform.openai.com/api-keys)

### Running locally

**Option A — no install needed (Python)**
```bash
python3 -m http.server 3000
# then open http://localhost:3000
```

**Option B — using npm**
```bash
npm start
# then open http://localhost:3000
```

### First use

1. Click **Settings** in the top-right corner
2. Enter your OpenAI API key — it is stored only in your browser's `localStorage`
3. Type a geographic question in the **Query** panel, or click one of the example questions
4. Press **Generate Query** (or `Ctrl+Enter`)
5. The AI generates one to three Overpass QL variants, executes the first one, and renders the results on the map
6. Click additional variants to execute them (each appears in a different colour)
7. Use **Brush Select** to draw a rectangle on the map to select elements; click list items to select individually
8. Click **Export GPX** to download selected (or all) results as a GPX file

## Example questions

- What are all the chocolate stores in the Netherlands?
- Streets where cars are allowed 50 km/h and are less than 1 km from an elementary school with pedestrian crossings
- Streets with shared transport of bikes and cars where the maximum speed is 50 km/h or more
- Railway stations that do not have an OV-fiets within 1 km

## Architecture

The app is a **single HTML file** (`index.html`) with no build step required. All dependencies are loaded from CDN:

| Library | Purpose |
|---------|---------|
| [Leaflet 1.9](https://leafletjs.com/) | Interactive map |
| [OpenAI API](https://platform.openai.com/docs) | Natural-language → Overpass QL |
| [Overpass API](https://overpass-api.de/) | OSM data queries |

Colours follow the **D3 schemeCategory10** palette, hardcoded to avoid a full D3 dependency.
