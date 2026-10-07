# Technical Case Study

## Problem

Building a versatile data dashboard requires choosing a visualization library and a web framework. Plotly is powerful but framework-agnostic; Streamlit and Gradio both wrap it but serve different use cases. This project demonstrates:

1. **Unified chart engine:** 15 plot types under one API.
2. **Theme consistency:** Dark mode applied uniformly across all visualizations and interfaces.
3. **Framework portability:** Same charts work in Streamlit and Gradio with minimal glue code.

## Solution

### Modular data generation

Each chart type gets a dedicated generator in `data_generator.py` that produces synthetic data:

- Time-series (line, area): daily date ranges with trend and noise.
- Distributions (histogram, box, violin): random samples.
- Geospatial (map): fictional coordinates.
- Categorical (bar, pie, funnel): sector, device and funnel-stage values.

The generator sets a fixed random seed for reproducible output.

### ThemeManager abstraction

Plotly styling is verbose when scattered across 15 builders. The project centralises it: `visualizations.py` applies a shared dark theme to each figure, and `utils.py` provides a `ThemeManager` with a dark template and palette. This reduces per-chart duplication.

### Registry pattern

`get_all_visualizations()` returns a dictionary of all 15 plot builders keyed by name. Each framework (Streamlit, Gradio) iterates this registry without knowing plot-specific details:

The UI looks up a chart by name in this registry and renders the returned figure, so the front ends need no chart-specific code.

### Pinned vs. latest dependencies

Requirements pinned to Streamlit 1.29, Gradio 4.44 and Numpy 1.24. These versions do not install on Python 3.13+. The local build used the latest unpinned libraries with no changes to the chart code.

### Mapbox and CARTO fallback

The map chart uses Folium with CARTO dark basemap. CARTO now displays an "API KEY REQUIRED" watermark due to tile service changes; markers render correctly. The code requires no key for demo data, but a different tile provider or an API key would be needed to remove the watermark.

## Trade-offs

- **No state persistence:** there is no database or saved user preferences.
- **Demo scale:** the app is a single-process demo and has not been load tested.
- **Scikit-learn unused:** Included in requirements but not called. Future scope might add clustering or PCA overlays.

## Lessons learned

1. **Centralised styling** keeps 15 related visualizations consistent.
2. **A registry** reduces coupling between UI frameworks and chart logic.
3. **Synthetic data** makes a demo easy to share: no privacy concerns and no setup.

Continue with [engineering challenges](ENGINEERING_CHALLENGES.md).
