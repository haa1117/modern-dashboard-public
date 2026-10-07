# Engineering Challenges

## Challenge: Dependency pinning and Python version drift

**Problem:** Requirements pinned to Streamlit 1.29, Gradio 4.44 and Numpy 1.24 to match the original build. These versions predate Python 3.13 and fail to install on newer runtimes.

**Solution:** The local build used Python 3.13 with the latest unpinned libraries. The chart code ran without changes. Relaxing the version pins would make installs easier.

**Lesson:** Synthetic data and minimal external API usage insulated this project from breaking changes. Apps with heavy database or third-party dependencies face higher compatibility risk.

## Challenge: CARTO basemap deprecation

**Problem:** The map chart uses Folium with CARTO dark basemap. CARTO's tile service now requires an API key and displays a watermark on demo requests.

**Solution:** Markers still render; the watermark is cosmetic. Switching tile provider or supplying a key would remove it.

**Impact:** No functional break, but the map page is left out of the portfolio screenshots.

## Challenge: Dual-framework testing

**Problem:** Streamlit and Gradio have different event loops and rendering pipelines. Keeping the same chart consistent across both is a maintenance cost.

**Solution:** The registry pattern proved essential—one data source, one chart builder, two UI wrappers. Only the Streamlit app was run for this portfolio; the Gradio app was not installed or run.

**Lesson:** A shared registry keeps chart logic in one place.

## Challenge: Synthetic data realism

**Problem:** Demo charts need data that looks plausible without using real records.

**Solution:** Each chart has its own synthetic generator with a fixed seed, shaped for its type (trend and noise for time series, categories for bar and pie, stages for the funnel).

**Outcome:** Charts render with no live data pipeline and no privacy concerns.

## Challenge: Theme consistency across 15 plot types

**Problem:** Plotly charts have dozens of customizable properties. Keeping line, bar, scatter, heatmap, 3D and specialty plots (gauge, funnel, radar) visually consistent without a central theme would lead to duplication.

**Solution:** A shared dark-theme definition (colors, fonts, gridlines, background) applied to every figure, with chart-specific overrides where needed.

**Benefit:** New charts inherit the same look with little extra styling code.

Next: [Privacy and source](PRIVACY_AND_SOURCE.md).
