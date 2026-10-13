# Customer Churn Analysis — Business Analysis Internship (Tasks 1–4)

Analysis of customer churn in a telecommunications company, covering Tasks 1–4 of the
Business Analysis internship brief: dataset understanding, data cleaning, exploratory
data analysis and customer segmentation visualisation.

**Dataset:** Telco Customer Churn — 7,043 customers × 21 attributes
**Target:** `Churn` — 1,869 churned (26.54%) vs 5,174 retained (73.46%)

📄 **Full write-up:** [`Saiket_BA_Internship_Report_Tasks_1-4.pdf`](Saiket_BA_Internship_Report_Tasks_1-4.pdf)

---

## Deliverables

| File | Task | Contents |
|------|------|----------|
| [`Task_1_Understand_Dataset.ipynb`](Task_1_Understand_Dataset.ipynb) | 1 | Load, structure, data types, missing-value audit |
| [`Task 2 - Data Cleaning.ipynb`](Task%202%20-%20Data%20Cleaning.ipynb) | 2 | Column standardisation, missing values, duplicates → cleaned CSV |
| [`Task 3 - Exploratory Data Analysis.ipynb`](Task%203%20-%20Exploratory%20Data%20Analysis.ipynb) | 3 | Summary statistics, histograms, box plots, churn breakdowns |
| [`Task 4 - Customer Segmentation Visualization.ipynb`](Task%204%20-%20Customer%20Segmentation%20Visualization.ipynb) | 4 | Tenure donut charts, clustered bar of monthly charges (static + interactive) |
| [`Saiket_BA_Internship_Report_Tasks_1-4.pdf`](Saiket_BA_Internship_Report_Tasks_1-4.pdf) | 1–4 | 20-page report covering all four tasks |
| [`Task 5 - Advanced Analysis.ipynb`](Task%205%20-%20Advanced%20Analysis.ipynb) | 5 | *Not covered by the report above* — tenure-group statistics, churn by demographics / contract / payment, lifecycle trends. Delivered as a separate notebook per the brief. |

### Data files

| File | Description |
|------|-------------|
| `Telco_Customer_Churn_Dataset  (3).csv` | Raw source data, unmodified (7,043 × 21) |
| `Telco_Customer_Churn_Cleaned.csv` | Output of Task 2 — 0 nulls, 0 duplicates, numeric `totalcharges` |

---

## Key findings

- **Hidden missing data.** `isnull()` reported zero missing values, but 11 `totalcharges`
  cells held blank strings — all belonging to customers with `tenure = 0`. Filled with `0`
  on business grounds (`0 months × monthly plan = $0 billed`), documented against the
  rejected alternatives.
- **Churn is a first-year problem.** 47.44% churn at 0–12 months vs 11.93% at 37+ months.
  Newcomers are 31.04% of the base.
- **Churners pay more and leave earlier.** $74.44/month vs $61.27, but 17.98 months tenure
  vs 37.57 — roughly 40% less lifetime value ($1,531.80 vs $2,549.91).
- **Value rises with tenure.** Average monthly charges climb $56.10 → $63.25 → $72.01
  (+28.4% from newcomer to loyal), so early retention compounds.
- **Contract is the strongest lever.** Month-to-month 42.71% · one year 11.27% ·
  two year 2.83% — a 15× gap.
- **Payment friction flags dissatisfaction.** Electronic check 45.29% vs 15–17% for
  automatic methods.
- **Fiber optic carries outsized risk.** 41.89% churn vs DSL 18.96%, no-internet 7.40%.

---

## How to run

Requires Python 3.14 with `pandas`, `numpy`, `matplotlib`, `seaborn` and `plotly`.

```bash
# Run in order — Task 2 writes the cleaned CSV that Tasks 3 and 4 read
jupyter notebook "Task_1_Understand_Dataset.ipynb"
jupyter notebook "Task 2 - Data Cleaning.ipynb"
jupyter notebook "Task 3 - Exploratory Data Analysis.ipynb"
jupyter notebook "Task 4 - Customer Segmentation Visualization.ipynb"
```

Tasks 3 and 4 fall back to re-applying the Task 2 cleaning logic if the cleaned CSV is
missing, so either notebook also runs standalone. All four were executed end-to-end with
zero errors and zero warnings.

The submitted PDF report was generated from the executed notebook outputs, so every figure
and statistic in it is reproducible by re-running the notebooks.

---

## Environment

| Component | Version |
|-----------|---------|
| Python | 3.14.7 |
| pandas | 3.0.6 |
| NumPy | 2.5.3 |
| Matplotlib | 3.11.2 |
| Seaborn | 0.13.2 |
| Plotly | 7.1.0 |
