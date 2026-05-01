# Solutions — Beginner Sales Data

These are worked solutions for the tasks in the [Beginner README](../README.md).  
**Do not open this file until you have attempted each task yourself.**

---

## Task 1 — Basic Summation

**Formula (assuming data is in columns A–H with headers in row 1, data in rows 2–31):**

```excel
=SUM(F2:F31)
```

**Expected result:** `$14,876.37`

The `SUM` function adds all values in the `Total Sales` column (column F).

---

## Task 2 — Averages

**Average Units Sold:**
```excel
=AVERAGE(D2:D31)
```
Expected result: `≈ 135.3 units`

**Average Unit Price:**
```excel
=AVERAGE(E2:E31)
```
Expected result: `≈ $11.54`

---

## Task 3 — Counting Electronics Transactions

```excel
=COUNTIF(C2:C31,"Electronics")
```

**Expected result:** `15` transactions

There are 5 Electronics products × 3 months = 15 Electronics transactions in the dataset.

---

## Task 4 — Maximum and Minimum

**Highest single-transaction sale:**
```excel
=MAX(F2:F31)
```
Expected result: `$1,540.00` (Keyboard, March 2024, South region)

**Lowest single-transaction sale:**
```excel
=MIN(F2:F31)
```
Expected result: `$148.50` (Highlighter, January 2024, North region)

---

## Task 5 — Sorting

**Steps:**
1. Click any cell inside the data table.
2. Go to **Data → Sort**.
3. In the Sort dialog, set **Column** to `Total Sales`, **Order** to `Largest to Smallest`.
4. Click **OK**.

The Keyboard (South, March 2024, $1,540.00) should now appear at the top.

---

## Task 6 — Filtering the North Region

**Steps:**
1. Click any cell inside the data table.
2. Go to **Data → Filter** (the filter arrows will appear on all headers).
3. Click the drop-down arrow on the `Region` column.
4. Uncheck `(Select All)`, then check only `North`.
5. Click **OK**.

**Expected result:** `9 rows` (3 North transactions per month × 3 months).

---

## Task 7 — Category Totals

Set up a small summary table. In a free area of your sheet, enter:

| | A | B |
|---|---|---|
| 1 | Category | Total Sales |
| 2 | Stationery | `=SUMIF($C$2:$C$31,A2,$F$2:$F$31)` |
| 3 | Electronics | `=SUMIF($C$2:$C$31,A3,$F$2:$F$31)` |

**Expected results:**
- Stationery: `$4,464.90`
- Electronics: `$10,411.47`

---

## Task 8 — Sales Rep Performance

Create a summary table with each rep's name, then use `SUMIF`:

```excel
=SUMIF($H$2:$H$31, "Alice Johnson", $F$2:$F$31)
```

**Expected totals:**
| Sales Rep | Total Sales |
|---|---|
| Alice Johnson | $3,334.50 |
| Bob Smith | $4,509.75 |
| Carol Davis | $3,559.47 |
| David Lee | $3,472.65 |

*(Values are approximate — verify against your filtered data.)*

---

## Task 9 — Simple Chart

**Steps:**
1. Build a small SUMIF summary table for regions (North, South, East, West) as shown in Task 7.
2. Select the two-column summary table (region names and totals).
3. Go to **Insert → Charts → Clustered Column**.
4. Add a chart title such as "Total Sales by Region".

**Expected regional totals (approximate):**
| Region | Total Sales |
|---|---|
| North | $3,334.50 |
| South | $4,509.75 |
| East | $3,559.47 |
| West | $3,472.65 |

---

## Task 10 — Percentage of Total Sales

**Step 1:** In a free cell (e.g., H1 label cell or a nearby cell), calculate the grand total:
```excel
=SUM(F2:F31)
```
Suppose this is in cell `J1`.

**Step 2:** In a new column header, type `% of Total Sales`. In the first data row (e.g., `I2`):
```excel
=F2/$J$1
```
The `$` signs lock the reference to the grand total cell. Copy this formula down to I31.

**Step 3:** Format column I as **Percentage** (right-click → Format Cells → Percentage, 2 decimal places).

**Expected range:** Each row will show a value between roughly 1% and 10%, summing to exactly 100%.
