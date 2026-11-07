# Mega Supermart: Workforce Performance & Absenteeism Analysis

An exploratory data analysis (EDA) of an anonymised retail workforce dataset, built in Python. The project looks at workforce composition, age and tenure, absenteeism patterns and operational risk, and turns the findings into recommendations for HR, store managers and operations leadership.

**Author:** Keren Oyem
**Role:** Business Intelligence Consultant (practice engagement)
**Programme:** #RDAMP, Realcare Tech Mark LTD (Task 1)

---

## Project overview

Mega Supermart is a large Western Canadian retail organisation reviewing how it staffs its stores and how to reduce absenteeism. The dataset covers **1,200 employees across 11 stores in 4 provinces (AB, BC, MB, SK)**, with demographics, job attributes, length of service, scheduled hours and absent hours for 2025.

### Business questions

1. **Workforce composition:** how is the workforce spread across departments, job titles, stores, business units, divisions and gender, and are there staffing imbalances?
2. **Tenure and age:** what do the age and service distributions look like, and which segments are at risk of retirement or turnover?
3. **Absenteeism:** what is the distribution of absent hours, who is most affected, and what is it correlated with?
4. **Risk identification:** which outliers, data issues, absence clusters, tenure extremes and understaffed areas need attention?
5. **Strategic opportunities:** where can HR, store managers and operations leaders improve things?

---

## Key findings

- **Absence is concentrated, not company-wide.** The median employee misses 32 hours, but the mean is 47 because of a small group with very long absences. The top 10% of employees account for 36% of all absent hours.
- **Customer Service (63 h) and Sales (57 h)** average more than double Operations (26 h). They are 53% of staff but about 67% of absent hours.
- **Regina is the standout store:** 91 hours per employee, about 41 hours above what its department mix predicts. Brandon (+13 h) and Winnipeg (+11 h) also run above expectation.
- **Age and gender do not explain absence; early tenure does.** Gender and full-time versus part-time show no significant difference. Employees under 25 and first-year employees are the groups at risk, especially in Sales.
- **Retirement and turnover risk sit in different places.** About 8% of staff are 55+ (concentrated in HR and Operations), while about 17% have under one year of service (concentrated in Sales and Customer Service).
- **Small Prairie stores have thin coverage.** Brandon and Saskatoon each have one Customer Service employee, and Regina has no HR staff.
- **Data issues were found and handled:** duplicate employee IDs, label conflicts, missing values, and 55 suspect placeholder hire dates (30 to 31 Dec 2025). No rows were deleted; every issue was corrected, flagged or deliberately left alone.

---

## Methods

| Step | What was done |
|---|---|
| Data quality | Missing values, duplicates, outliers (IQR and z-score), inconsistent labels, logical checks on dates, age, tenure and absence rate |
| Descriptive analytics | Summary statistics, frequency tables, demographic profile |
| Visualisation | 22 charts: bar charts, histograms, boxplots, correlation heatmaps, store-by-department heatmaps, a geographic bubble map, a risk scorecard |
| Statistical testing | Kruskal-Wallis (with effect size), Spearman correlation, Mann-Whitney U |
| Confounding checks | Store absence compared with what each store's department mix would predict; sensitivity tests with and without extreme-absence employees and suspect hire dates |
| Risk and opportunity | Absence clusters, tenure extremes, observed versus expected staffing, a composite store risk scorecard, and opportunity sizing in hours and FTE |

---

## Repository contents

```
.
├── README.md
├── notebook/
│   └── Keren_Oyem_Workforce_Absenteeism_EDA.ipynb   # full analysis, with interpretations after key outputs
├── report/
│   └── Keren_Oyem_Analysis_Report.pdf               # 13-page EDA report
├── outputs/
│   ├── Keren_Oyem_Analysis_Tables.xlsx              # supporting tables
│   └── charts/                                      # all 22 charts (PNG)
└── data/
    └── (place the Excel file here, see below)
```

---

## How to run

1. Clone or download this repository.
2. Install the requirements:

   ```bash
   pip install pandas numpy matplotlib seaborn scipy openpyxl jupyter
   ```

3. Place the dataset in the same folder as the notebook and name it `Mega_Supermart_Employee_Data.xlsx`, or edit the `FILE` path in the first code cell of the notebook.
4. Open the notebook in Jupyter and choose **Kernel > Restart & Run All**.

The notebook saves charts to a `charts` folder and writes the cleaned dataset and a workbook of key tables to the notebook folder.

> **Note on data:** the dataset was provided for a practice engagement and is **not included** in this repository. To reproduce the results, use the original file supplied with the task.

---

## Assumptions and definitions

The brief did not define these terms, so they are set explicitly in the notebook and can be changed in the setup cell:

- **Reference date:** 31 Dec 2025 (age and service are measured as at this date)
- **Retirement watch:** age 55+; **high retirement risk:** age 60+
- **Turnover watch:** under 1 year of service
- **Extreme absence:** above the IQR upper fence of absent hours (142 hours)
- **Absence rate:** absent hours divided by scheduled hours; **FTE** = 2,080 hours

---

## Limitations

- One year of data and current employees only, so turnover is inferred from short tenure rather than measured.
- No absence reason codes, so illness, injury and leave cannot be separated.
- Some stores and store-department teams are small, so their averages are volatile.
- Findings describe associations, not causes.
- Thresholds and the expected-staffing benchmark are analyst assumptions and should be validated with the client.

---

## Tools

Python, pandas, NumPy, Matplotlib, Seaborn, SciPy, Jupyter Notebook, ReportLab (for the PDF report)

