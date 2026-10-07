<div align="center">

# Vizboard: Modern Data Visualization Dashboard

**An interactive dashboard that showcases 15 chart types on synthetic data, with a dark theme and a single sidebar selector.**

Python · Streamlit · Plotly · Folium · WordCloud · pandas

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?logo=streamlit&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-3F4F75?logo=plotly&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?logo=pandas&logoColor=white)
![Gradio](https://img.shields.io/badge/Gradio-F97316?logo=gradio&logoColor=white)

<table>
  <tr>
    <td><img src="assets/screenshots/mordern-dashboard-line-chart.webp" width="430" alt="Dashboard with a line chart of a year of daily values, sidebar controls and quick stats" /></td>
    <td><img src="assets/screenshots/mordern-dashboard-bar-chart.webp" width="430" alt="Bar chart comparing seven industry sectors with a data summary panel" /></td>
  </tr>
  <tr>
    <td colspan="2" align="center"><img src="assets/screenshots/mordern-dashboard-gauge-chart.webp" width="430" alt="Four gauge indicators for system metrics" /></td>
  </tr>
</table>
<sub>Screenshots are real captures of a local build running on fictional demo data.</sub>

</div>

---

## Product at a Glance

| | |
|---|---|
| **What it is** | A dashboard of 15 interactive chart types, switched from one sidebar dropdown |
| **Charts** | Line, bar, scatter, pie, heatmap, 3D scatter, area, box, histogram, violin, word cloud, map, gauge, funnel, radar |
| **Front ends** | Streamlit app (run for this portfolio) and a parallel Gradio app (not run) |
| **Data** | Generated synthetic data with a fixed seed; no database, login or external API |
| **Per chart** | Description, data summary and quick stats beside the figure |
| **AI** | None; this is rule-based visualization only |

## Product Showcase

<table>
  <tr>
    <td align="center"><img src="assets/screenshots/mordern-dashboard-area-chart.webp" width="300" alt="Area chart of revenue, costs and profit"/><br/><sub><b>Area chart</b><br/>Revenue, costs and profit over time</sub></td>
    <td align="center"><img src="assets/screenshots/mordern-dashboard-heatmap.webp" width="300" alt="Correlation matrix heatmap"/><br/><sub><b>Heatmap</b><br/>8x8 correlation matrix</sub></td>
    <td align="center"><img src="assets/screenshots/mordern-dashboard-3d-scatter.webp" width="300" alt="3D scatter plot in three colors"/><br/><sub><b>3D scatter</b><br/>Rotatable three-axis view</sub></td>
  </tr>
  <tr>
    <td align="center"><img src="assets/screenshots/mordern-dashboard-funnel-chart.webp" width="300" alt="Five-stage conversion funnel"/><br/><sub><b>Funnel</b><br/>Five-stage conversion flow</sub></td>
    <td align="center"><img src="assets/screenshots/mordern-dashboard-radar-chart.webp" width="300" alt="Radar chart comparing three products"/><br/><sub><b>Radar</b><br/>Three products across six attributes</sub></td>
    <td align="center"><img src="assets/screenshots/mordern-dashboard-pie-chart.webp" width="300" alt="Donut chart of device share"/><br/><sub><b>Donut</b><br/>Device share breakdown</sub></td>
  </tr>
  <tr>
    <td align="center"><img src="assets/screenshots/mordern-dashboard-word-cloud.webp" width="300" alt="Word cloud of analytics terms"/><br/><sub><b>Word cloud</b><br/>Term frequency by size</sub></td>
  </tr>
</table>

## Key Features

- **15 chart types** in one app, selected from a sidebar dropdown.
- **Per-chart context.** Each view shows a description, a data summary (ranges, counts, top category and similar) and quick stats.
- **Refresh Data** button to regenerate the synthetic dataset.
- **Consistent dark theme** with a shared palette across Plotly figures.
- **Interactive charts.** Plotly hover, zoom and, for the 3D view, rotation.
- **Zero setup data.** Everything is generated at runtime.

## Architecture

- `data_generator.py` produces synthetic data per chart type with a fixed random seed.
- `visualizations.py` holds a `VisualizationGenerator` with 15 builders and a registry (`get_all_visualizations`) that both front ends use.
- `streamlit_app.py` renders the selector, quick stats and the chosen figure; `gradio_app.py` is a parallel interface over the same registry.
- `utils.py` has shared helpers (theme, chart enhancements, export, timing).

Details: [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md).

## Engineering Highlights

- **One chart engine, two front ends.** A single registry of builders feeds both Streamlit and Gradio.
- **Centralised styling.** A shared dark theme keeps 15 different Plotly chart types visually consistent.
- **Self-contained data.** Per-chart synthetic generators remove the need for a database or API.
- **Mixed rendering paths.** Plotly figures, a Folium map and an image-based word cloud sit behind the same selector.
- **Dependency drift handled.** The original version pins do not install on Python 3.13; the chart code ran unchanged on current library versions.

More: [docs/ENGINEERING_CHALLENGES.md](docs/ENGINEERING_CHALLENGES.md).

## Status & Scope

- **Demo-mode showcase.** All data is generated and fictional; there is no backend, authentication or persistence.
- **No AI or ML.** The app is rule-based visualization. scikit-learn appears in the requirements but is not used.
- **Gradio app not run.** Only the Streamlit app was installed and exercised for this portfolio.
- **Map page.** The map uses CARTO tiles, which now show an API-key watermark, so it is not shown here.
- **Presentation layer.** The screenshots use an updated visual layer (branding, styling and chart colors); chart logic and data generation are unchanged.

## Documentation

- [Product overview](docs/PRODUCT_OVERVIEW.md)
- [Architecture](docs/ARCHITECTURE.md)
- [Technical case study](docs/TECHNICAL_CASE_STUDY.md)
- [Engineering challenges](docs/ENGINEERING_CHALLENGES.md)
- [Privacy and source](docs/PRIVACY_AND_SOURCE.md)

## Rights

See [RIGHTS.md](RIGHTS.md).
