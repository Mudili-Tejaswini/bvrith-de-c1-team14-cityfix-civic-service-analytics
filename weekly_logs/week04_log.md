# Week 04 Log — Bronze Ingestion

**Week:** 4  
**Date range:** 28-07-2026 to 03-08-2026  
**Team:** Team 14  
**Project:** CityFix – Civic Service Analytics

---

## 1. Sprint Goal

The goal of this sprint was to ingest the raw CSV files into the Bronze layer using Delta tables. The data was loaded without modifying the original values, and metadata columns were added to track the ingestion process.

---

## 2. Work Completed

| Task | Owner | Status | Evidence |
|---|---|---|---|
| Created Week 4 notebook (02_bronze_ingestion.ipynb) | A. Usha | Done | Notebook |
| Loaded agencies.csv into Spark DataFrame | A. Usha | Done | Notebook |
| Loaded boroughs.csv into Spark DataFrame | A. Usha | Done | Notebook |
| Loaded categories.csv into Spark DataFrame | A. Usha | Done | Notebook |
| Loaded requests.csv into Spark DataFrame | A. Usha | Done | Notebook |
| Loaded zip_geography.csv into Spark DataFrame | A. Usha | Done | Notebook |
| Added metadata columns (source_file, ingestion_timestamp, ingestion_run_id) | A. Usha | Done | Notebook |
| Created Bronze Delta tables | A. Usha | Done | Databricks Tables |
| Verified row counts between source and Bronze tables | A. Usha | Done | Notebook Output |
| Validated Bronze tables and metadata | A. Usha | Done | Screenshots |

---

## 3. Key Decisions

- Used Delta tables as the Bronze storage format.
- Preserved all source data without applying transformations.
- Added metadata columns (`source_file`, `ingestion_timestamp`, `ingestion_run_id`) to improve data lineage and ingestion tracking.

---

## 4. Blockers / Risks

| Blocker | Impact | Help Needed |
|---|---|---|
| Metadata column issue while creating Bronze DataFrames | Bronze DataFrames could not be created initially | Resolved by replacing `input_file_name()` with the file name using `lit()` and successfully recreated the Bronze DataFrames |

---

## 5. Evidence Added to GitHub

- Updated `notebooks/02_bronze_ingestion.ipynb`
- Added `week04_bronze_table_created.png`
- Added `week04_bronze_counts.png`
- Updated `weekly_logs/week04_log.md`

---

## 6. AI Transparency Note

| Question | Response |
|---|---|
| Where AI helped | Assisted in implementing the Bronze ingestion pipeline, creating Delta tables, adding metadata columns, resolving the `input_file_name()` issue, and validating the Bronze layer. |
| What we changed after AI suggestion | Added metadata columns (`source_file`, `ingestion_timestamp`, `ingestion_run_id`) and created Bronze Delta tables for all five source datasets. |
| What we verified manually | Verified that all five source files loaded successfully, Bronze tables were created, metadata columns existed, and source and Bronze row counts matched. |
| What we can explain without AI | We understand the purpose of the Bronze layer, how Delta tables are created, why ingestion metadata is required, and how row-count reconciliation validates successful data ingestion. |

---

## 7. Next Week Preparation

- Create the `03_silver_transformations.ipynb` notebook.
- Read Bronze Delta tables.
- Perform basic data cleaning and validation.
- Handle null values and duplicate records.
- Create Silver layer Delta tables.
