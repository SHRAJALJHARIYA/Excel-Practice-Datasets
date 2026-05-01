# 🟢 Beginner Level — Sales Data

## About This Dataset

**File:** `sales_data.csv`

This dataset contains 30 rows of fictional office supply and electronics sales transactions across four regions over three months (January–March 2024). It is ideal for practising foundational Excel skills.

### Columns

| Column | Description |
|---|---|
| Date | Transaction date (YYYY-MM-DD) |
| Product | Product name |
| Category | Product category (Stationery or Electronics) |
| Units Sold | Number of units sold in the transaction |
| Unit Price | Price per unit (USD) |
| Total Sales | Total revenue for the transaction (Units Sold × Unit Price) |
| Region | Sales region (North, South, East, West) |
| Sales Rep | Name of the sales representative |

---

## 📥 How to Open

1. Download `sales_data.csv`.
2. Open Microsoft Excel or Google Sheets.
3. Import the CSV file (Excel: **Data → From Text/CSV**; Google Sheets: **File → Import**).
4. Ensure the data has headers in row 1.

---

## ✅ Tasks

Complete each task in your own spreadsheet. Attempt all tasks before checking the solutions.

### Task 1 — Basic Summation
Calculate the **total revenue** across all 30 transactions using the `SUM` function.

> **Hint:** Apply `SUM` to the `Total Sales` column.

---

### Task 2 — Averages
Find the **average number of units sold** per transaction and the **average unit price** across all products.

> **Hint:** Use the `AVERAGE` function.

---

### Task 3 — Counting
How many transactions were made in the **Electronics** category?

> **Hint:** Use `COUNTIF` with the `Category` column.

---

### Task 4 — Maximum and Minimum
Identify the **highest** and **lowest** single-transaction sale values.

> **Hint:** Use `MAX` and `MIN` on the `Total Sales` column.

---

### Task 5 — Sorting
Sort the dataset by **Total Sales** in descending order to see the most valuable transactions at the top.

> **Hint:** Use **Data → Sort** and choose the `Total Sales` column, largest to smallest.

---

### Task 6 — Filtering
Filter the data to show only transactions from the **North** region. How many rows appear?

> **Hint:** Use **Data → Filter**, then filter the `Region` column.

---

### Task 7 — Category Totals
Calculate the total sales for each category (**Stationery** and **Electronics**) separately.

> **Hint:** Use `SUMIF` with the `Category` column as the criteria range.

---

### Task 8 — Sales Rep Performance
Find the total sales made by each sales representative.

> **Hint:** Use `SUMIF` with the `Sales Rep` column as the criteria range.

---

### Task 9 — Simple Chart
Create a **bar chart** showing total sales by region.

> **Hint:** First use `SUMIF` to calculate total sales for North, South, East, and West. Then select those results and insert a bar (clustered column) chart.

---

### Task 10 — Percentage of Total
Add a new column called **% of Total Sales**. For each row, calculate that transaction's `Total Sales` as a percentage of the overall total.

> **Hint:** Divide each row's `Total Sales` by the grand total (using an absolute reference `$` to lock the total cell).

---

## 📂 Solutions

Worked solutions for all tasks are in the [`solutions/sales_data_solutions.md`](solutions/sales_data_solutions.md) file.

Try each task yourself first — you will learn much more that way!
