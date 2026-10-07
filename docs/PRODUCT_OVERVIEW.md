# Product Overview

## What it is

A Python data-visualization dashboard showcasing 15 interactive chart types with a consistent dark theme. Built as dual interfaces (Streamlit and Gradio) for instant comparison of visualization frameworks on the same underlying chart library.

## The 15 chart types

1. **Line chart** — temporal trends over a year of daily values
2. **Bar chart** — categorical comparison across industry sectors
3. **Scatter plot** — correlation detection across two continuous variables
4. **Pie chart** — composition at a glance
5. **Heatmap** — dense 2D patterns via colour intensity
6. **3D Scatter** — three-dimensional correlation analysis
7. **Area chart** — cumulative trends with filled regions
8. **Box plot** — distribution quartiles and outliers
9. **Histogram** — frequency distribution
10. **Violin plot** — probability density across ranges
11. **Word cloud** — term frequency visualized by size
12. **Map** — geographic markers via Folium
13. **Gauge chart** — progress toward a target metric
14. **Funnel chart** — stage-by-stage conversion drop-off
15. **Radar chart** — multi-dimensional capability comparison

## User experience

- **Dashboard.** A sidebar selector toggles between chart types. Each chart shows a description, a data summary and quick stats.
- **Theme.** Consistent dark mode across all charts, with a gradient header.
- **Data.** Fully synthetic, generated with a fixed seed — no setup, database or live API calls needed.
- **Dual delivery.** A Streamlit app and a Gradio app share the same visualization engine (only the Streamlit app was run for this portfolio).

## No AI/ML

This showcase is purely rule-based visualization. Scikit-learn appears in the requirements file but is not used by the app itself.

Continue with the [technical case study](TECHNICAL_CASE_STUDY.md).
