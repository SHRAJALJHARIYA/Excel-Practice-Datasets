# Solutions — Intermediate Employee Data

These are worked solutions for the tasks in the [Intermediate README](../README.md).  
**Do not open this file until you have attempted each task yourself.**

Assume data begins in row 2 with headers in row 1. Column references:
- A = Employee ID, B = Full Name, C = Department, D = Hire Date
- E = Salary, F = Performance Score, G = Manager
- H = Employment Type, I = City

---

## Task 1 — Tenure Calculation

Add a column header `Years of Service` (e.g., column J). In cell J2:

```excel
=DATEDIF(D2, TODAY(), "Y")
```

Or alternatively:
```excel
=INT((TODAY()-D2)/365.25)
```

Copy down to J31.

**Expected examples (as of 2025):**
- E003 Michael Brown (Hired 2017-11-20): ~7 years
- E014 Karen Lewis (Hired 2015-03-30): ~10 years
- E019 Donald Young (Hired 2023-04-01): ~2 years

---

## Task 2 — Salary Classification

Add column header `Salary Band` (e.g., column K). In cell K2:

```excel
=IF(E2<50000,"Low",IF(E2<75000,"Mid","High"))
```

Copy down to K31.

**Expected distribution:**
| Band | Count | Employees |
|---|---|---|
| Low | 7 | E004, E005, E007, E011, E015, E017, E030 |
| Mid | 15 | E001, E002, E006 (edge cases), E008, E009 etc. |
| High | 8 | E003, E006, E012, E014, E018, E022, E026, E027 |

*(Exact counts depend on current salaries in the dataset.)*

---

## Task 3 — Performance Rating Label

Add column header `Performance Label` (e.g., column L). In cell L2:

```excel
=IF(F2>=4.5,"Excellent",IF(F2>=4.0,"Good",IF(F2>=3.5,"Average","Needs Improvement")))
```

Or using `IFS` (Excel 2019+):
```excel
=IFS(F2>=4.5,"Excellent",F2>=4.0,"Good",F2>=3.5,"Average",F2<3.5,"Needs Improvement")
```

Copy down to L31.

**Expected distribution:**
| Label | Count |
|---|---|
| Excellent | 7 (scores ≥ 4.5) |
| Good | 10 (scores 4.0–4.4) |
| Average | 8 (scores 3.5–3.9) |
| Needs Improvement | 5 (scores < 3.5) |

---

## Task 4 — VLOOKUP Practice

**Step 1:** Create the lookup table (for example, in columns K–L on a new area, or a separate sheet):

| K | L |
|---|---|
| Department | Cost Centre |
| Sales | CC-01 |
| Marketing | CC-02 |
| Engineering | CC-03 |
| HR | CC-04 |
| Finance | CC-05 |

Assume the lookup table is in `$K$2:$L$6`.

**Step 2:** Add a column header `Cost Centre` (column M). In cell M2:

```excel
=VLOOKUP(C2, $K$2:$L$6, 2, FALSE)
```

Copy down to M31.

**Expected results (examples):**
- E001 James Carter (Sales) → CC-01
- E003 Michael Brown (Engineering) → CC-03
- E008 Elizabeth Taylor (Finance) → CC-05

---

## Task 5 — Department Statistics

Create a summary table. Assume Department names are in column N, starting at N2:

| Department | Avg Salary | Headcount | Avg Performance |
|---|---|---|---|
| Sales | `=AVERAGEIF($C$2:$C$31,"Sales",$E$2:$E$31)` | `=COUNTIF($C$2:$C$31,"Sales")` | `=AVERAGEIF($C$2:$C$31,"Sales",$F$2:$F$31)` |

Repeat for Marketing, Engineering, HR, Finance.

**Expected results:**
| Department | Avg Salary | Headcount | Avg Performance |
|---|---|---|---|
| Sales | $52,167 | 6 | 4.0 |
| Marketing | $52,833 | 6 | 3.4 |
| Engineering | $86,500 | 8 | 4.6 |
| HR | $46,000 | 5 | 3.6 |
| Finance | $67,400 | 5 | 4.3 |

*(Values are approximate.)*

---

## Task 6 — Conditional Formatting

**Steps:**
1. Select the Performance Score column (F2:F31).
2. Go to **Home → Conditional Formatting → New Rule**.
3. Choose **"Format only cells that contain"**.

**Rule 1 — Red (Needs Improvement):**
- Cell value < 3.5
- Fill: Red

**Rule 2 — Yellow (Average/Good):**
- Cell value between 3.5 and 4.49
- Fill: Yellow

**Rule 3 — Green (Excellent):**
- Cell value >= 4.5
- Fill: Green

Alternatively, use **"Use a formula to determine which cells to format"**:
- Red: `=F2<3.5`
- Yellow: `=AND(F2>=3.5, F2<4.5)`
- Green: `=F2>=4.5`

---

## Task 7 — Pivot Table: Salary by Department

**Steps:**
1. Select cells A1:I31 (the full dataset).
2. Go to **Insert → PivotTable** → New Worksheet.
3. In the PivotTable field list:
   - Drag `Department` to **Rows**
   - Drag `Salary` to **Values** → Change to **Average**
   - Drag `Employee ID` to **Values** → Change to **Count**

**Expected output:**
| Department | Average of Salary | Count of Employee ID |
|---|---|---|
| Engineering | $86,500 | 8 |
| Finance | $67,400 | 5 |
| HR | $46,000 | 5 |
| Marketing | $52,833 | 6 |
| Sales | $52,167 | 6 |

---

## Task 8 — Pivot Table: Headcount by City and Employment Type

**Steps:**
1. Insert another PivotTable from the same data.
2. In the PivotTable field list:
   - Drag `City` to **Rows**
   - Drag `Employment Type` to **Columns**
   - Drag `Employee ID` to **Values** → **Count**

**Expected output (approximate):**
| City | Contract | Full-Time | Part-Time |
|---|---|---|---|
| Austin | 0 | 5 | 1 |
| Chicago | 1 | 7 | 1 |
| New York | 0 | 8 | 2 |
| San Francisco | 0 | 8 | 0 |

---

## Task 9 — Top Earners

**Method 1 — Sort:**
1. Copy the data to a new sheet.
2. Sort by Salary descending.
3. The top 5 rows are your answer.

**Method 2 — LARGE + INDEX/MATCH:**
```excel
=LARGE($E$2:$E$31, 1)   ← Highest salary
=INDEX($B$2:$B$31, MATCH(LARGE($E$2:$E$31,1), $E$2:$E$31, 0))  ← Corresponding name
```

**Expected top 5:**
| Rank | Employee | Department | Salary |
|---|---|---|---|
| 1 | Karen Lewis | Engineering | $98,000 |
| 2 | Barbara Wilson | Engineering | $92,000 |
| 3 | Michael Brown | Engineering | $85,000 |
| 4 | Sandra Wright | Engineering | $89,000 |
| 5 | Betty Allen | Engineering | $81,000 |

---

## Task 10 — Bonus Calculation

Add column header `Annual Bonus` (column N or next available). In the first data row:

```excel
=IF(F2>=4.5, E2*0.10, IF(F2>=4.0, E2*0.07, IF(F2>=3.5, E2*0.04, 0)))
```

Copy down to the last row.

**Expected examples:**
- E003 Michael Brown (Score 4.7, Salary $85,000): `$85,000 × 10% = $8,500`
- E001 James Carter (Score 4.2, Salary $52,000): `$52,000 × 7% = $3,640`
- E004 Patricia Garcia (Score 3.5, Salary $47,000): `$47,000 × 4% = $1,880`
- E019 Donald Young (Score 3.0, Salary $52,000): `$0`
