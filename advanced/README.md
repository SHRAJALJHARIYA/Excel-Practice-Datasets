# 🔴 Advanced Level — Financial Data

## About This Dataset

**File:** `financial_data.csv`

This dataset contains 60 rows of monthly financial performance data for a fictional technology company across three regions and three product lines for the full year 2023. It is designed for practising advanced Excel formulas, what-if analysis, dynamic dashboards, and data modelling.

### Columns

| Column | Description |
|---|---|
| Date | Month-end date (YYYY-MM-DD) |
| Region | Sales region (North America, Europe, Asia Pacific) |
| Product Line | Product line (Software, Hardware, Services) |
| Revenue | Monthly revenue (USD) |
| Cost of Goods Sold (COGS) | Direct costs of products/services sold |
| Gross Profit | Revenue minus COGS |
| Operating Expenses | Indirect costs (salaries, rent, marketing, etc.) |
| Net Income | Gross Profit minus Operating Expenses |
| Units Sold | Number of units sold |
| Customer Count | Number of unique customers |
| Return Rate (%) | Percentage of units returned |
| Prior Year Revenue | Same month revenue from the prior year |
| YoY Growth (%) | Year-over-year revenue growth percentage |

---

## 📥 How to Open

1. Download `financial_data.csv`.
2. Open Microsoft Excel or Google Sheets.
3. Import the CSV file (Excel: **Data → From Text/CSV**; Google Sheets: **File → Import**).
4. Ensure the data has headers in row 1.

---

## ✅ Tasks

Complete each task in your own spreadsheet. Attempt all tasks before checking the solutions.

### Task 1 — Dynamic Lookup with INDEX/MATCH
Build a lookup tool on a separate sheet where you can type any combination of **Month**, **Region**, and **Product Line** into three input cells, and a formula automatically returns the corresponding **Net Income**.

> **Hint:** Use `INDEX` with nested `MATCH` calls, or use `SUMPRODUCT` with multiple criteria:
> `=SUMPRODUCT((Region_range=region_cell)*(ProductLine_range=pl_cell)*(Month_range=month_cell)*NetIncome_range)`

---

### Task 2 — Gross Margin Analysis
Add a calculated column **Gross Margin (%)** = Gross Profit / Revenue × 100. Then create a summary table showing the average Gross Margin % for each Region and each Product Line.

> **Hint:** Use `AVERAGEIF` for the summary table. Format the column as a percentage.

---

### Task 3 — Year-to-Date Totals
Create a summary table that shows the **year-to-date (YTD) Revenue**, **YTD COGS**, and **YTD Net Income** for each combination of Region and Product Line.

> **Hint:** Use `SUMIFS` with the Region and Product Line as the criteria columns.

---

### Task 4 — Running Total
Add a new column **Cumulative Revenue** that calculates the running total of Revenue ordered by Date (i.e., the cumulative sum up to and including each row).

> **Hint:** Use `SUMIF` with a helper column of row numbers, or use `OFFSET` + `SUM` for a dynamic running total.

---

### Task 5 — What-If Analysis: Data Table
On a new sheet, build a **two-variable data table** that shows projected **Net Income** for North America Software at different combinations of:
- Revenue growth rates: 5%, 8%, 10%, 12%, 15%
- Operating expense reduction rates: 0%, 2%, 5%, 8%

Use the December 2023 North America Software figures as the base values.

> **Hint:** Set up formulas in a grid layout, then use **Data → What-If Analysis → Data Table**.

---

### Task 6 — Scenario Manager
Using the Scenario Manager (Excel: **Data → What-If Analysis → Scenario Manager**), create three scenarios for the North America Software product line's annual Net Income:

| Scenario | Revenue Change | OpEx Change |
|---|---|---|
| Pessimistic | −10% | +5% |
| Base Case | 0% | 0% |
| Optimistic | +15% | −8% |

Show a scenario summary report.

> **Hint:** Define changing cells for the Revenue and Operating Expenses input cells, then add each scenario. Use **Summary** to generate the report.

---

### Task 7 — Dynamic Dashboard
Build a one-page dashboard on a new sheet that includes:
1. A **slicer** or drop-down to filter by Region
2. A **line chart** showing monthly Revenue over time
3. A **stacked bar chart** showing Revenue breakdown by Product Line per month
4. **KPI tiles** displaying total Revenue, total Net Income, average Gross Margin %, and average YoY Growth % for the selected region

> **Hint:** Use `SUMIF`/`AVERAGEIF` driven by a drop-down (data validation list) to feed the charts. For slicers, insert a pivot table first, then add a slicer connected to pivot charts.

---

### Task 8 — Return Rate Impact
Calculate how much **revenue was lost** due to product returns each month. Assume returned units were sold at the average revenue per unit for that row.

Add a column **Estimated Return Loss** = (Return Rate % / 100) × Revenue.

Then find:
- The month and region with the highest total return loss
- The product line with the highest average return rate

> **Hint:** Use `MAXIFS` (Excel 2019+) to find the maximum return loss by month/region combination.

---

### Task 9 — Profitability Ranking
Rank each row by **Net Income** using the `RANK` function (or `RANK.EQ`). Then use conditional formatting to highlight:
- Top 10 rows (by Net Income) in green
- Bottom 10 rows in red

Also create a pivot table showing the **average rank** by Region and Product Line.

> **Hint:** `=RANK.EQ(NetIncome_cell, NetIncome_range, 0)` ranks from highest (1) to lowest.

---

### Task 10 — Power Query (Excel only)
Using **Power Query** (Excel: **Data → Get Data → From File → From CSV**):
1. Import `financial_data.csv`
2. Add a calculated column **Profit Margin (%)** = Net Income / Revenue
3. Filter to keep only rows where Profit Margin > 25%
4. Group the results by Region, summing Revenue and Net Income
5. Load the result to a new sheet

> **Hint:** In Power Query, use **Add Column → Custom Column** for the calculated field, then **Home → Group By** for aggregation.

---

## 📂 Solutions

Worked solutions for all tasks are in the [`solutions/financial_data_solutions.md`](solutions/financial_data_solutions.md) file.

Try each task yourself first — you will learn much more that way!
