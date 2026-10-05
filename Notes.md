# BrewMetrics BI – Project Notes

## Data Model

The Power BI project uses a star schema.

### Fact Table
- Fact_Sales

### Dimension Tables
- Dim_Date
- Dim_City
- Dim_Product

## Relationships

- Dim_Product → Fact_Sales
- Dim_City → Fact_Sales
- Dim_Date → Fact_Sales

The dimension tables provide descriptive fields, while Fact_Sales contains the sales transactions and measures.

## Key Measures

- Total Sales
- Total Quantity
- Average Order Value
- Sales YoY %
- Running Total Sales
- City Sales Rank

## Report Purpose

The dashboard is designed to analyze sales performance across:
- Time
- City
- Product
- Category
- Store format

## Development Notes

Power BI was used for data preparation, modeling, DAX measures, and visualization.

The project is maintained as a Power BI Project (PBIP) and tracked using Git/GitHub.