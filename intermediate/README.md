# 🟡 Intermediate Level — Employee Data

## About This Dataset

**File:** `employee_data.csv`

This dataset contains 30 fictional employee records for a mid-sized company with offices in five US cities. It is designed for practising lookup functions, conditional logic, pivot tables, and date-based calculations.

### Columns

| Column | Description |
|---|---|
| Employee ID | Unique identifier (E001–E030) |
| Full Name | Employee's full name |
| Department | Department (Sales, Marketing, Engineering, HR, Finance) |
| Hire Date | Date employee was hired (YYYY-MM-DD) |
| Salary | Annual salary in USD |
| Performance Score | Score from 3.0 to 5.0 (higher is better) |
| Manager | Name of direct manager |
| Employment Type | Full-Time, Part-Time, or Contract |
| City | Office city |

---

## 📥 How to Open

1. Download `employee_data.csv`.
2. Open Microsoft Excel or Google Sheets.
3. Import the CSV file (Excel: **Data → From Text/CSV**; Google Sheets: **File → Import**).
4. Ensure the data has headers in row 1.

---

## ✅ Tasks

Complete each task in your own spreadsheet. Attempt all tasks before checking the solutions.

### Task 1 — Tenure Calculation
Add a new column called **Years of Service** that calculates how many full years each employee has worked at the company (as of today's date).

> **Hint:** Use `=DATEDIF(Hire Date, TODAY(), "Y")` or `=INT((TODAY()-Hire Date)/365.25)`.

---

### Task 2 — Salary Classification with IF
Add a new column called **Salary Band** using the following rules:
- **Low** — salary below $50,000
- **Mid** — salary $50,000–$74,999
- **High** — salary $75,000 or above

> **Hint:** Use a nested `IF` formula: `=IF(salary<50000,"Low",IF(salary<75000,"Mid","High"))`.

---

### Task 3 — Performance Rating Label
Add a column called **Performance Label** using the following rules:
- Score ≥ 4.5 → **Excellent**
- Score ≥ 4.0 → **Good**
- Score ≥ 3.5 → **Average**
- Score < 3.5 → **Needs Improvement**

> **Hint:** Use nested `IF` or the `IFS` function (Excel 2019+).

---

### Task 4 — VLOOKUP Practice
Create a small lookup table on a separate sheet (or to the side) that maps **Department** to a **Cost Centre** code as follows:

| Department | Cost Centre |
|---|---|
| Sales | CC-01 |
| Marketing | CC-02 |
| Engineering | CC-03 |
| HR | CC-04 |
| Finance | CC-05 |

Add a new column **Cost Centre** to the employee table and populate it using `VLOOKUP`.

> **Hint:** `=VLOOKUP(Department_cell, lookup_table_range, 2, FALSE)`

---

### Task 5 — Department Statistics
Calculate the following for each department using `AVERAGEIF` and `COUNTIF`:
- Average salary per department
- Number of employees per department
- Average performance score per department

> **Hint:** Create a summary table to the side with each department listed, then use `AVERAGEIF` and `COUNTIF` referencing the Department column.

---

### Task 6 — Conditional Formatting
Apply conditional formatting to the **Performance Score** column:
- Red fill for scores below 3.5
- Yellow fill for scores 3.5–4.4
- Green fill for scores 4.5 and above

> **Hint:** Use **Home → Conditional Formatting → New Rule → Use a formula to determine which cells to format**.

---

### Task 7 — Pivot Table: Salary by Department
Create a pivot table that shows the **average salary** and **headcount** for each **Department**.

> **Hint:** Select the data, go to **Insert → PivotTable**. Place `Department` in Rows, `Salary` in Values (set to Average), and add `Employee ID` in Values (set to Count).

---

### Task 8 — Pivot Table: Headcount by City and Employment Type
Create a second pivot table that shows the number of employees broken down by **City** (rows) and **Employment Type** (columns).

> **Hint:** Place `City` in Rows, `Employment Type` in Columns, and `Employee ID` in Values (Count).

---

### Task 9 — Top Earners
List the **top 5 highest-paid employees** (Employee ID, Full Name, Department, Salary).

> **Hint:** Sort by Salary descending (or use `LARGE` to find the top 5 salary values, then `INDEX/MATCH` to retrieve names).

---

### Task 10 — Bonus Calculation
Add a column called **Annual Bonus** using the following logic:
- Excellent performers (score ≥ 4.5) receive **10%** of salary
- Good performers (score ≥ 4.0) receive **7%** of salary
- Average performers (score ≥ 3.5) receive **4%** of salary
- Needs Improvement (score < 3.5) receive **0%**

> **Hint:** Use a nested `IF` on the Performance Score column, multiplied by the Salary.

---

## 📂 Solutions

Worked solutions for all tasks are in the [`solutions/employee_data_solutions.md`](solutions/employee_data_solutions.md) file.

Try each task yourself first — you will learn much more that way!
