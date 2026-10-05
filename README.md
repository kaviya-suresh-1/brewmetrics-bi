# BrewMetrics BI -- Coffee Sales Analysis

## Project Overview

BrewMetrics BI is a Power BI mini-project for analysing coffee sales
across months, cities and store formats. The report combines a
fact-and-dimension model, DAX measures and interactive visuals.

## Objectives

-   Analyse total sales over time.
-   Compare sales across cities.
-   Compare store-format contribution.
-   Provide interactive filtering.
-   Demonstrate DAX analytical calculations.
-   Maintain the project in Git for traceable development.

## Data Model

The model contains `Fact_Sales`, `Dim_Date`, `Dim_City` and
`Dim_Product`.

`Fact_Sales` contains transaction-level fields such as date, city,
store_format, category, item, quantity, sale_id, sales_amount and
unit_price.

`Dim_Date` contains date, Year, Month and Month Name. The numeric Month
field is used to sort Month Name chronologically.

`Dim_City` provides city information and `Dim_Product` provides product
information.

## DAX Measures

The model contains `Total Sales`, `Total Quantity`, `Average Order`,
`Running Total`, `City Sales Rank` and `Sales YoY %`.

Detailed development documentation is provided in `NOTES.md`.

## Dashboard

The final dashboard contains: 1. Total Sales by Month Name line chart.
2. Total Sales by Month column chart. 3. Total Sales by City and Store
Format stacked column chart. 4. Total Sales by City column chart. 5.
Store-format/city slicer.

The displayed trend rises slightly from April to May and then declines
through June and July. Bengaluru and Chennai are the stronger-performing
cities, while Coimbatore is the lowest among the four shown.

## Tools

-   Microsoft Power BI Desktop
-   DAX
-   Power BI data modelling
-   GitHub
-   GitHub Desktop
-   GitHub Copilot / Copilot-assisted development documentation

## Repository

`brewmetrics-bi`

The completed dashboard work was committed with the message
`Complete final dashboard report`.
