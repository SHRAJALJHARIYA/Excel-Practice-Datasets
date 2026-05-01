# Solutions — Advanced Financial Data

These are worked solutions for the tasks in the [Advanced README](../README.md).  
**Do not open this file until you have attempted each task yourself.**

Assume data begins in row 2 with headers in row 1. Column references:
- A = Date, B = Region, C = Product Line
- D = Revenue, E = COGS, F = Gross Profit
- G = Operating Expenses, H = Net Income
- I = Units Sold, J = Customer Count
- K = Return Rate (%), L = Prior Year Revenue, M = YoY Growth (%)

---

## Task 1 — Dynamic Lookup with INDEX/MATCH

Set up three input cells on a new sheet, for example:
- **B1** = Month-end date (e.g., `2023-06-30`)
- **B2** = Region (e.g., `North America`)
- **B3** = Product Line (e.g., `Software`)

Then use `SUMPRODUCT` to return Net Income (references assume data is on Sheet1):

```excel
=SUMPRODUCT(
  (Sheet1!$A$2:$A$61=B1) *
  (Sheet1!$B$2:$B$61=B2) *
  (Sheet1!$C$2:$C$61=B3) *
  Sheet1!$H$2:$H$61
)
```

**Verification example:**
- Date: 2023-06-30, Region: North America, Product Line: Software
- Expected Net Income: **$116,000**

**Alternative — nested INDEX/MATCH (array formula, press Ctrl+Shift+Enter):**
```excel
=INDEX(Sheet1!$H$2:$H$61,
  MATCH(1,
    (Sheet1!$A$2:$A$61=B1) *
    (Sheet1!$B$2:$B$61=B2) *
    (Sheet1!$C$2:$C$61=B3),
    0
  )
)
```

---

## Task 2 — Gross Margin Analysis

**Step 1:** Add column header `Gross Margin (%)` (column N). In N2:
```excel
=F2/D2
```
Format as Percentage (2 decimal places). Copy down to N61.

**Step 2:** Summary table by Region using `AVERAGEIF`:
```excel
=AVERAGEIF($B$2:$B$61, "North America", $N$2:$N$61)
=AVERAGEIF($B$2:$B$61, "Europe", $N$2:$N$61)
=AVERAGEIF($B$2:$B$61, "Asia Pacific", $N$2:$N$61)
```

**Summary table by Product Line:**
```excel
=AVERAGEIF($C$2:$C$61, "Software", $N$2:$N$61)
=AVERAGEIF($C$2:$C$61, "Hardware", $N$2:$N$61)
=AVERAGEIF($C$2:$C$61, "Services", $N$2:$N$61)
```

**Expected average gross margins (approximate):**
| Region | Avg Gross Margin |
|---|---|
| North America | ~72% |
| Europe | ~73% |
| Asia Pacific | ~55% |

| Product Line | Avg Gross Margin |
|---|---|
| Software | ~77% |
| Hardware | ~55% |
| Services | ~77% |

---

## Task 3 — Year-to-Date Totals

Use `SUMIFS` to aggregate by Region and Product Line.

Example for North America Software:
```excel
=SUMIFS($D$2:$D$61, $B$2:$B$61, "North America", $C$2:$C$61, "Software")
```

Build a full summary table with each of the 9 combinations (3 regions × 3 product lines).

**Expected YTD Revenue (approximate, full year 2023):**
| Region | Product Line | YTD Revenue |
|---|---|---|
| North America | Software | $3,393,000 |
| North America | Hardware | $3,692,000 |
| Europe | Software | $2,768,000 |
| Europe | Hardware | — |
| Europe | Services | $2,100,000 |
| Asia Pacific | Hardware | $3,965,000 |

*(Not all combinations exist in the dataset — `SUMIFS` will return 0 for missing combos.)*

---

## Task 4 — Running Total

Add column header `Cumulative Revenue` (column O). In O2:
```excel
=SUM($D$2:D2)
```

This uses a **mixed reference** — `$D$2` is locked, `D2` is relative. As the formula is copied down, it automatically expands the range.

In O3: `=SUM($D$2:D3)`, in O4: `=SUM($D$2:D4)`, etc.

Copy down to O61.

**Note:** This running total sums in the order rows appear in the file. If the data has been sorted by date and region in a fixed order, the cumulative total will reflect that ordering.

---

## Task 5 — What-If Analysis: Data Table

**Base values (December 2023, North America, Software):**
- Revenue: $325,000
- Operating Expenses: $110,000
- Net Income: $133,000

**Step 1:** On a new sheet, enter the base-case formula for Net Income in one cell (e.g., B1):
```excel
= base_revenue * (1 + growth_rate) - base_cogs - base_opex * (1 - reduction_rate)
```

Or simplified as an input-driven formula, with:
- **B2** = revenue growth rate (the row input cell)
- **A3** = opex reduction rate (the column input cell)

**Step 2:** Set up a table:

|   | 0% | 2% | 5% | 8% |
|---|---|---|---|---|
| 5% | formula | | | |
| 8% | | | | |
| 10% | | | | |
| 12% | | | | |
| 15% | | | | |

**Step 3:** Select the table range, go to **Data → What-If Analysis → Data Table**.
- Row input cell: the growth rate cell (B2)
- Column input cell: the opex reduction cell (A3)

**Example result (Revenue growth 10%, OpEx reduction 5%):**
Projected Net Income ≈ `$325,000 × 1.10 − $62,000 − $110,000 × 0.95` = **≈ $154,500**

---

## Task 6 — Scenario Manager

**Setup:**
1. On a calculation sheet, create input cells:
   - **B1** = Revenue multiplier (1.0 for base)
   - **B2** = OpEx multiplier (1.0 for base)
2. Create a result cell:
   ```excel
   = (3393000 * B1) - 1105000 - (1175000 * B2)
   ```
   *(Using approximate annual totals for North America Software.)*

**Scenario values:**
| Scenario | B1 (Revenue) | B2 (OpEx) |
|---|---|---|
| Pessimistic | 0.90 | 1.05 |
| Base Case | 1.00 | 1.00 |
| Optimistic | 1.15 | 0.92 |

**Steps:**
1. Go to **Data → What-If Analysis → Scenario Manager → Add**.
2. Name: "Pessimistic", Changing cells: B1:B2, Values: 0.90, 1.05.
3. Repeat for Base Case and Optimistic.
4. Click **Summary**, select the result cell as the output cell.

**Expected Net Income results (approximate):**
| Scenario | Net Income |
|---|---|
| Pessimistic | ~$907,000 |
| Base Case | ~$1,113,000 |
| Optimistic | ~$1,403,000 |

---

## Task 7 — Dynamic Dashboard

**Recommended structure:**

**Sheet: Dashboard**

1. **Drop-down (Data Validation):**
   - Select a cell (e.g., B1) → **Data → Data Validation → List**
   - Source: `North America,Europe,Asia Pacific`

2. **KPI formulas (driven by B1):**
   ```excel
   Total Revenue:    =SUMIF(data!$B$2:$B$61, B1, data!$D$2:$D$61)
   Total Net Income: =SUMIF(data!$B$2:$B$61, B1, data!$H$2:$H$61)
   Avg Gross Margin: =AVERAGEIF(data!$B$2:$B$61, B1, data!$N$2:$N$61)
   Avg YoY Growth:   =AVERAGEIF(data!$B$2:$B$61, B1, data!$M$2:$M$61)
   ```

3. **Monthly Revenue table for line chart:**
   Use a helper table listing the 12 month-end dates and `SUMIFS` for the selected region:
   ```excel
   =SUMIFS(data!$D$2:$D$61, data!$B$2:$B$61, $B$1, data!$A$2:$A$61, A_date_cell)
   ```

4. **Insert charts** based on these helper tables. Charts will update automatically when the drop-down value changes.

---

## Task 8 — Return Rate Impact

**Step 1:** Add column `Estimated Return Loss` (column P). In P2:
```excel
=D2 * (K2/100)
```
Copy down to P61.

**Step 2:** Find the month/region with the highest total return loss:
```excel
=MAX($P$2:$P$61)
```
Then use `INDEX/MATCH` to retrieve the date and region:
```excel
=INDEX($A$2:$A$61, MATCH(MAX($P$2:$P$61), $P$2:$P$61, 0))
=INDEX($B$2:$B$61, MATCH(MAX($P$2:$P$61), $P$2:$P$61, 0))
```

**Expected result:** Asia Pacific Hardware tends to have the highest return losses due to higher revenue and return rate.

**Step 3:** Average return rate by Product Line:
```excel
=AVERAGEIF($C$2:$C$61, "Hardware", $K$2:$K$61)
=AVERAGEIF($C$2:$C$61, "Software", $K$2:$K$61)
=AVERAGEIF($C$2:$C$61, "Services", $K$2:$K$61)
```

**Expected average return rates:**
- Hardware: ~3.0%
- Software: ~1.1%
- Services: ~0.8%

---

## Task 9 — Profitability Ranking

**Step 1:** Add column `Rank` (column Q). In Q2:
```excel
=RANK.EQ(H2, $H$2:$H$61, 0)
```
`0` = descending (rank 1 = highest Net Income). Copy down to Q61.

**Step 2:** Conditional formatting on Net Income column (H2:H61):
- **Green** (top 10): `=Q2<=10` → Green fill
- **Red** (bottom 10): `=Q2>=51` → Red fill

Apply via **Home → Conditional Formatting → New Rule → Use a formula**.

**Step 3:** Pivot table for average rank by Region and Product Line:
1. Insert PivotTable from the data.
2. Rows: Region, Columns: Product Line, Values: Rank (Average).

**Expected pattern:** Software and Services should average higher ranks (lower rank numbers = more profitable) than Hardware.

---

## Task 10 — Power Query (Excel only)

**Step-by-step:**

1. **Import:** Data → Get Data → From File → From CSV → select `financial_data.csv`.

2. **Add Profit Margin column:**
   In the Power Query Editor, go to **Add Column → Custom Column**.
   Name: `Profit Margin (%)`, Formula:
   ```powerquery
   = [Net Income] / [Revenue]
   ```

3. **Filter:** Click the drop-down on `Profit Margin (%)` → **Number Filters → Greater Than** → enter `0.25`.

4. **Group By:** Go to **Home → Group By**.
   - Group by: `Region`
   - New column name: `Total Revenue`, Operation: Sum, Column: `Revenue`
   - Add another: `Total Net Income`, Operation: Sum, Column: `Net Income`

5. **Load:** Click **Close & Load** → Load to new worksheet.

**Expected result after filtering (Profit Margin > 25%) and grouping:**

| Region | Total Revenue | Total Net Income |
|---|---|---|
| North America | (sum of qualifying rows) | (sum) |
| Europe | (sum of qualifying rows) | (sum) |
| Asia Pacific | (sum of qualifying rows) | (sum) |

*(The exact values depend on which rows pass the 25% margin threshold. Software and Services rows will dominate, as Hardware margins are lower.)*
