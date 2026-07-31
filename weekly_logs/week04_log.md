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
| Loaded complaints_sample.csv into Spark DataFrame | A. Usha | Done | Notebook |
| Loaded departments_sample.csv into Spark DataFrame | A. Usha | Done | Notebook |
| Loaded wards_sample.csv into Spark DataFrame | A. Usha | Done | Notebook |
| Added metadata columns (ingested_at, source_file, ingestion_run_id, schema_version) | A. Usha | Done | Notebook |
| Created Bronze Delta tables | A. Usha | Done | Databricks Tables |
| Verified row counts between source and Bronze tables | A. Usha | Done | Notebook Output |
| Validated Bronze tables and metadata | A. Usha | Done | Screenshots |

---

## 3. Key Decisions

- Used Delta tables as the Bronze storage format.
- Added metadata columns to improve data lineage and tracking without changing the original source data.

---

## 4. Blockers / Risks

| Blocker | Impact | Help Needed |
|---|---|---|
| Delta metadata mismatch while overwriting existing Bronze tables | Bronze tables could not be updated initially | Resolved by dropping the existing tables and recreating them with the new schema |

---

## 5. Evidence Added to GitHub

- Updated `notebooks/02_bronze_ingestion.ipynb`
- Added screenshots of Bronze tables and metadata columns
- Added screenshots of source count and Bronze count verification
- Updated Week 04 Log

---

## 6. AI Transparency Note

| Question | Response |
|---|---|
| Where AI helped | Assisted in implementing the Bronze ingestion pipeline, adding metadata columns, resolving Delta metadata mismatch errors, and verifying Bronze tables. |
| What we changed after AI suggestion | Added metadata columns (`ingested_at`, `source_file`, `ingestion_run_id`, `schema_version`) and recreated the Bronze tables after resolving schema mismatch issues. |
| What we verified manually | Verified that all three source files loaded successfully, Bronze tables were created, metadata columns were present, and source and Bronze row counts matched. |
| What we can explain without AI | We understand how the Bronze layer works, how Delta tables are created, why metadata columns are added, and how row-count reconciliation validates successful ingestion. |

---

## 7. Next Week Preparation

- Create the `03_silver_transformations.ipynb` notebook.
- Read Bronze tables, clean the data, handle null values and duplicates, and create the Silver layer.
