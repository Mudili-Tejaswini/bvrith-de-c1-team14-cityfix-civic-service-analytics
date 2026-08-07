# Week 05 Log — Silver Standardization

## 1. Sprint Goal

Transform Bronze CityFix data into clean Silver tables with standardized
field representations, appropriate data types, and retained lineage metadata.

## 2. Work Completed

- Verified Bronze complaints, departments, and wards tables.
- Created `silver_complaints`.
- Created `silver_departments`.
- Created `silver_wards`.
- Standardized complaint status using `TRIM` and `UPPER`.
- Standardized department names using `TRIM`.
- Standardized ward names using `TRIM`.
- Retained ingestion and source metadata for lineage.
- Validated Bronze-to-Silver row counts.
- Created raw-to-Silver mapping evidence.

## 3. Key Decisions

- Complaint `status` was standardized using `TRIM(UPPER(status))`.
- `department_name` was standardized using `TRIM(department_name)`.
- `ward_name` was standardized using `TRIM(ward_name)`.
- Bronze metadata fields were retained in the Silver layer.
- No unnecessary reference joins were introduced.
- The transformations preserved the Bronze record counts.

## 4. Validation Results

| Entity | Bronze Count | Silver Count | Result |
|---|---:|---:|---|
| Complaints | 5 | 5 | PASS |
| Departments | 3 | 3 | PASS |
| Wards | 4 | 4 | PASS |

## 5. Evidence

- `screenshots/week05_silver_schema.png`
- `screenshots/week05_raw_to_silver_mapping.png`
- `screenshots/week05_count_reconciliation.png`
- `screenshots/week05_silver_tables.png`

## 6. Blockers / Risks

No blockers were encountered during the Silver transformation.

The Silver transformations were tested in Databricks and the Bronze and
Silver row counts matched.

## 7. AI Transparency Note

### Where AI helped

AI was used to help write SQL transformation and validation queries,
identify the correct Bronze metadata column names, and structure the
raw-to-Silver mapping evidence.

### What was changed after AI suggestions

The SQL was adapted to the actual CityFix Bronze schemas observed in
Databricks. Column names were verified before creating the Silver tables.

### What was verified manually

The Silver schemas, sample Silver records, raw-to-Silver mapping, table
existence, and Bronze-to-Silver row counts were executed and checked
manually in Databricks.

### What we can explain without AI

We can explain the purpose of the Silver layer, the standardization
performed on status and reference names, the reason for retaining lineage
metadata, and how the count reconciliation validates that records were
not lost during transformation.

## 8. Next Week Preparation

The completed Silver tables will be used for the next stage of the
CityFix data engineering pipeline. Data-quality checks and related
validation activities will be handled in the appropriate next-week work.
