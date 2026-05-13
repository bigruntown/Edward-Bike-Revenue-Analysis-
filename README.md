# Edward Bike Revenue Analysis

A Power BI report that breaks down hourly bike-rental revenue, profit, and rider counts across the working day, sliced by season, weekday, and rider type — surfacing the time-of-day and seasonality patterns that drive demand.

## Overview

Bike-rental businesses live and die by **when** people ride, not just how many ride. This report digs into the temporal structure of rentals so an operator can plan staffing, bike availability, and pricing around real demand patterns rather than assumptions.

## Tools

- **Microsoft Power BI Desktop**
- **DAX** — including a Profit Margin measure
- **Data modelling**

## Dataset

A bike-rental dataset (`Query1` table) with one row per hour:

- `dteday` — date
- `hr` — hour of day (0–23)
- `season` — categorical season
- `weekday` — day of week
- `rider_type` — categorical (casual / member / etc.)
- `price`, `revenue`, `profit`, `riders` — performance metrics
- `Years` — derived year column for time slicing

## What the report contains

### KPIs

- **Sum of revenue**, **Sum of profit**, **Sum of riders**
- **Average price**, **average profit**, **average revenue per ride**
- **Profit margin** — calculated DAX measure (profit / revenue)

### Visuals

- **Card visuals** for the KPIs
- **Combo chart** (line + clustered column) showing revenue against riders over time — exposing whether revenue tracks volume or whether higher pricing carries it
- **Donut chart** of revenue share by rider type
- **Clustered bar chart** for season / weekday comparison
- **Pivot table** with hour-level detail
- **Slicers** for season, weekday, rider type
- **Shapes / images** used for layout and polish

## Key technical work

- **Profit Margin measure** — built as `DIVIDE(SUM(profit), SUM(revenue))` so it stays correct under any filter context, rather than being stored as a precalculated column.
- **Hourly granularity** — kept the model at one-row-per-hour and let Power BI roll up dynamically, instead of pre-aggregating to daily and losing the ability to drill down.
- **Combo visualisation** — picked a line + clustered column combo to show two metrics on the same time axis, which is more honest than two separate charts because you can directly compare the shapes.

## Screenshots

![image alt](https://github.com/bigruntown/Edward-Bike-Revenue-Analysis-/blob/main/Screenshot.jpg?raw=true)

![image alt](https://github.com/bigruntown/Edward-Bike-Revenue-Analysis-/blob/main/season%20rider%20screenshot.jpg?raw=true)


## How to view this project

1. Download `Edward-bike-Revenue.pbix` from this repo.
2. Open it in **Power BI Desktop** (free download from Microsoft).
3. Use the slicers to filter by season,
