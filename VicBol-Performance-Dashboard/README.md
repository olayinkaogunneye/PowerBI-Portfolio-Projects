# VicBol Performance Analytics — Power BI Case Study

### Project Overview

VicBol Performance Analytics is a complete end‑to‑end Power BI project analyzing marketing performance across spend, traffic, and revenue from May–December 2025.
The goal was to build a clean, executive‑ready dashboard supported by:

A validated star schema

Clean and standardized Power Query transformations

Reusable and well‑structured DAX logic

Clear, audit‑ready documentation

A professional, reproducible project folder structure

This project demonstrates strong BI engineering practices and analytical storytelling.

### Business Problem

VicBol needed a unified view of how marketing spend translates into:

Exit clicks

Revenue

Profitability

Month‑over‑month performance

Channel‑level efficiency

The challenge was that data came from multiple sources, currencies, and structures — requiring cleaning, standardization, and modeling before meaningful insights could be produced.

### Dashboard Highlights

The Power BI dashboard provides:

Total Spend (CZK)

Total Revenue (CZK)

Profit & ROI

Exit Clicks

CPC (Cost per Click)

Month‑over‑Month indicators

Channel‑level contribution

Seasonal performance trends

It answers key questions such as:

Which channels drive the most value?

Is spend translating into proportional revenue?

How does performance shift across months?

Where are the biggest efficiency gaps?

### Data Model (Star Schema)

The model follows a clean star schema:

Fact Tables

FactCosts

FactExitClicks

Dimension Tables

DimDate

DimCountry

DimChannel

DimDevice

All relationships are single‑direction, many‑to‑one, ensuring predictable filtering and optimized DAX behavior.

A full breakdown is available in:

`/docs/04_Star_Schema_Relationships.md`

#### Data Cleaning & Transformation

Both fact tables were thoroughly cleaned in Power Query:

Standardized text fields

Validated numeric fields

Removed nulls and duplicates

Converted spend into CZK using daily exchange rates

Ensured consistent country, channel, and date values

Full cleaning steps:

`/docs/01_Data_Cleaning_Report.md`

### KPI Definitions

**Core KPIs include:**

- Total Spend (CZK)

- Total Revenue (CZK)

- Profit

- ROI

- Exit Clicks

- CPC

- Month‑over‑Month % Change

- MoM Display Indicators (arrows, colors, labels)

All KPI logic is documented in:

`/docs/05_KPI_Definitions.md`

### Key Insights

From the analysis:

- Spend fluctuates heavily month‑to‑month

- Revenue remains relatively stable

- Profit stays negative throughout the period

- November is the strongest month (Black Friday effect)

- Channel 22 dominates but shows a wide spend‑to‑revenue gap

- everal channels show high spend with low revenue contribution

Full insights summary:

`/docs/07_Insights_Summary.md`

### Project Structure

```
VicBol-Performance-Analytics/
│
├── pbix/
│   ├── VicBol_Performance.pbix
│   └── VicBol_Wireframe.pptx
│
├── data/
│   ├── raw/
│   ├── processed/
│
├── docs/
│   ├── 01_Data_Cleaning_Report.md
│   ├── 02_Dimension_Tables_Documentation.md
│   ├── 03_DimDate_and_Currency_Conversion.md
│   ├── 04_Star_Schema_Relationships.md
│   ├── 05_KPI_Definitions.md
│   ├── 06_Model_Diagram.png
│   ├── 07_Insights_Summary.md
│   └── 08_Project_Notes.md
│
├── screenshots/
│   ├── dashboard_overview.png
│   ├── spend_trends.png
│   ├── channel_performance.png
│   └── device_breakdown.png
│
├── assets/
│   ├── banner.png
│   ├── logo.png
│   └── theme.json
│
└── README.md

```

---

**Live Dashboard:** *[https://app.fabric.microsoft.com/view?r=eyJrIjoiNzQ1OTRmNWYtMDRjNC00ZjI1LThjN2MtMTQyMWEwMTRmNGIzIiwidCI6ImFjMDZkNWY1LTNiMWYtNGVkNy05NGY4LTRlODUzOGUwYjdlYSJ9]*

---

### Future Enhancements

Potential improvements include:

Channel‑level drill‑through pages

Device‑level deep dives

Forecasting models

Budget optimization scenarios

Automated data refresh pipeline

### Author: Olayinka Ogunneye

Role: Analytics Consultant 