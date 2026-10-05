# NOTES.md

# BrewMetrics -- Copilot-Assisted DAX Development Notes

## Documentation note

During the final documentation stage, Power BI Desktop displayed
**"Connect to a workspace that supports Copilot"** and no compatible
workspace was available.

Therefore, the prompts below are **reconstructed development prompts**
based on the completed model and the assignment requirements. They are
not presented as a saved transcript of an actual Copilot chat.

## 1. Total Sales

**Purpose:** Calculate total sales from transaction-level data.

**Reconstructed Copilot prompt:** Create a DAX measure called
`Total Sales` that sums `Fact_Sales[sales_amount]` and respects report
filters.

**DAX:**

``` dax
Total Sales =
SUM(Fact_Sales[sales_amount])
```

**Validation:** Used in the monthly and city-level visuals and responds
to report filtering.

## 2. Total Quantity

**Purpose:** Calculate total units sold.

**Reconstructed Copilot prompt:** Create a DAX measure named
`Total Quantity` that sums `Fact_Sales[quantity]` and respects the
current filter context.

**DAX:**

``` dax
Total Quantity =
SUM(Fact_Sales[quantity])
```

## 3. Average Order

**Purpose:** Calculate average sales value per order.

**Reconstructed Copilot prompt:** Create an average order-value measure
using total sales divided by the number of distinct sale IDs, with safe
division.

**DAX:**

``` dax
Average Order =
DIVIDE(
    [Total Sales],
    DISTINCTCOUNT(Fact_Sales[sale_id])
)
```

**Validation/correction:** Using distinct sale IDs makes the denominator
represent orders rather than simply transaction rows.

## 4. Running Total

**Purpose:** Calculate cumulative sales over time.

**Reconstructed Copilot prompt:** Create a DAX running-total measure
based on `Total Sales` and the `Dim_Date` date field.

**DAX:**

``` dax
Running Total =
CALCULATE(
    [Total Sales],
    FILTER(
        ALLSELECTED(Dim_Date[date]),
        Dim_Date[date] <= MAX(Dim_Date[date])
    )
)
```

**Validation/correction:** The date context must be expanded so earlier
dates can be included in the cumulative calculation.

## 5. City Sales Rank

**Purpose:** Rank cities by total sales.

**Reconstructed Copilot prompt:** Create a `RANKX` measure that ranks
cities by `[Total Sales]`, with the highest-sales city receiving rank 1.

**DAX:**

``` dax
City Sales Rank =
RANKX(
    ALL(Dim_City[city]),
    [Total Sales],
    ,
    DESC,
    DENSE
)
```

**Validation/correction:** `ALL(Dim_City[city])` allows the measure to
compare all cities rather than only the currently selected city.

## 6. Sales YoY %

**Purpose:** Calculate year-over-year percentage change.

**Reconstructed Copilot prompt:** Create a DAX measure comparing current
`Total Sales` with the equivalent period in the previous year.

**DAX:**

``` dax
Sales YoY % =
VAR CurrentSales = [Total Sales]
VAR PreviousSales =
    CALCULATE(
        [Total Sales],
        SAMEPERIODLASTYEAR(Dim_Date[date])
    )
RETURN
DIVIDE(
    CurrentSales - PreviousSales,
    PreviousSales
)
```

**Validation/correction:** Time intelligence is applied through
`Dim_Date`, and `DIVIDE` safely handles a zero or blank previous-period
value.

## Overall

The assignment requirements are covered by the growth measure
(`Sales YoY %`), running total, RANKX-based ranking and additional
business metric (`Average Order`). `Total Sales` and `Total Quantity`
provide the base measures used throughout the report.
