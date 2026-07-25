# Week 02 Log — Dataset Design & Data Dictionary

**Week:** 2  
**Date range:** 21-07-2026 to 27-07-2026  
**Team:** Team 14  
**Project:** CityFix – Civic Service Analytics

---

## 1. Sprint Goal

The goal of this sprint was to design the project dataset structure, prepare the data dictionary, define primary and foreign keys, document synthetic data assumptions, and organize sample datasets for the CityFix project.

---

## 2. Work Completed

| Task | Owner | Status | Evidence |
|---|---|---|---|
| Prepared Data Dictionary with fields, data types, and keys | Team 14 | Done | docs/data_dictionary.md |
| Documented synthetic data assumptions | Team 14 | Done | docs/synthetic_data_assumptions.md |
| Generated/updated synthetic sample datasets | Team 14 | Done | src/generate_synthetic_data.py |
| Added sample CSV files | Team 14 | Done | data_sample/ |
| Updated Week 02 project documentation | Team 14 | Done | weekly_logs/week02_log.md |

---

## 3. Key Decisions

- Created separate datasets for complaints, wards, and departments to maintain proper relationships.
- Used synthetic Metrovale data instead of real-world civic datasets to ensure privacy and consistency.

---

## 4. Blockers / Risks

| Blocker | Impact | Help Needed |
|---|---|---|
| Dataset relationships required verification | Minor delay in documentation | Verified field mapping and keys before finalizing |

---

## 5. Evidence Added to GitHub

- Updated `docs/data_dictionary.md`
- Updated `docs/synthetic_data_assumptions.md`
- Updated `src/generate_synthetic_data.py`
- Added sample CSV files in `data_sample/`
- Updated `weekly_logs/week02_log.md`

---

## 6. AI Transparency Note

| Question | Response |
|---|---|
| Where AI helped | Assisted in preparing the data dictionary, documenting assumptions, and formatting project documentation. |
| What we changed after AI suggestion | Reviewed field names, improved descriptions, and organized the documentation according to project guidelines. |
| What we verified manually | Verified dataset structure, primary/foreign keys, file names, and synthetic data assumptions. |
| What we can explain without AI | The complete dataset design, relationships between datasets, data dictionary, and project documentation. |

---

## 7. Next Week Preparation

- Upload sample datasets to Databricks.
- Begin Bronze layer data ingestion and initial data exploration notebook.
