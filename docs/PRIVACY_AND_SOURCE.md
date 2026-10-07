# Privacy and Source

## Source code

The production source code repository is private and not included in this portfolio. This folder contains only:
- Portfolio documentation (this file and guides).
- Screenshots and diagrams for visual reference.
- Analysis notes and logs from portfolio preparation.

No secrets, API keys, configuration or credentials are present in the repository.

## Data and privacy

All data shown in screenshots and live demos is **fictional and synthetically generated**. No real user data, transactions, locations or personal information appears anywhere in the application.

Data is generated with a fixed random seed, so there is no database or third-party API involved.

## Screenshots

Screenshots use only fictional demo data. Examples:
- Product names are placeholders (e.g., "Product A", "Region 1").
- Geographic locations on the map are arbitrary coordinates.
- Prices, dates and quantities are synthetic.
- No real individuals, organizations or transactions are depicted.

## Third-party libraries and licences

The project depends on open-source libraries:

- **Streamlit** — BSD-style licence, open-source.
- **Gradio** — Apache 2.0, open-source.
- **Plotly** — MIT licence, open-source.
- **Folium** — MIT licence, open-source for map rendering.
- **WordCloud** — MIT licence.
- **Pandas, NumPy, Matplotlib, Seaborn** — BSD/Apache 2.0, open-source.


## No external APIs in demo mode

This build requires no network calls:
- Charts are generated from local synthetic data.
- The map page loads CARTO tiles (shows an API-key watermark).
- No authentication is used.
- Usage statistics were disabled in the local run.

## Gradio framework compatibility

The Gradio app is defined in code but was not installed or run for this portfolio. It shares the same chart registry as the Streamlit app.
