# Week 03 Log — Data Exploration

**Week:** 3  
**Date range:** 21 July 2026 – 27 July 2026  
**Team:** Team 14  
**Project:** CityFix – Civic Service Analytics

---

## 1. Sprint Goal

Load the CityFix raw datasets into Databricks, inspect the schemas, explore the data using PySpark and Spark SQL, and perform basic data profiling before starting the Bronze ingestion layer.

---

## 2. Work Completed

| Task | Owner | Status | Evidence |
|---|---|---|---|
| Created Databricks Volume | A. Usha | Done | Databricks Volume |
| Uploaded sample CSV files | A. Usha | Done | Volume screenshots |
| Loaded complaints_sample.csv | A. Usha | Done | 01_data_exploration.ipynb |
| Loaded departments_sample.csv | A. Usha | Done | 01_data_exploration.ipynb |
| Loaded wards_sample.csv | A. Usha | Done | 01_data_exploration.ipynb |
| Displayed sample records | A. Usha | Done | Notebook screenshot |
| Inspected dataset schemas | A. Usha | Done | Schema screenshot |
| Counted dataset rows | A. Usha | Done | Row count screenshot |
| Generated summary statistics | A. Usha | Done | Summary statistics screenshot |
| Checked missing values | A. Usha | Done | Missing values screenshot |
| Created temporary SQL view | A. Usha | Done | Notebook |
| Executed SQL exploration query | A. Usha | Done | SQL output screenshot |

---

## 3. Key Decisions

- Used Databricks Volume to store and access the raw datasets.
- Performed initial data exploration only and postponed Bronze ingestion activities to Week 4.

---

## 4. Blockers / Risks

| Blocker | Impact | Help Needed |
|---|---|---|
| Initial uncertainty while creating the Databricks Volume | Delayed notebook setup | Resolved using mentor and documentation guidance |
| SQL query failed due to incorrect column name | Minor delay during exploration | Verified the dataset schema and updated the query |

---

## 5. Evidence Added to GitHub

- Updated `notebooks/01_data_exploration.ipynb`
- Added Week 3 screenshots
- Updated `weekly_logs/week03_log.md`

---

## 6. AI Transparency Note

| Question | Response |
|---|---|
| Where AI helped | AI helped with writing PySpark code, Spark SQL queries, and explaining each exploration step. |
| What we changed after AI suggestion | Updated SQL queries to match the actual dataset columns and adjusted file paths for the Databricks Volume. |
| What we verified manually | Verified data loading, schemas, row counts, summary statistics, missing values, and SQL query results in Databricks. |
| What we can explain without AI | We can explain the notebook workflow, dataset structure, schema inspection, row counts, SQL exploration, and basic data quality checks. |

---

## 7. Next Week Preparation

- Build the Bronze ingestion notebook (`02_bronze_ingestion.ipynb`).
- Create the Week 4 Bronze demonstration table and validate the ingestion process.
