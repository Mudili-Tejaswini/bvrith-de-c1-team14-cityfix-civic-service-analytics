# Project Requirements

**Week:** 1  
**Purpose:** Define what the project must produce.

---

## 1. Functional Requirements

| ID | Requirement | Priority |
|---|---|---|
| FR-01 | Ingest raw source files into Bronze tables using Databricks and PySpark | Must have |
| FR-02 | Create standardized Silver tables by cleaning and transforming the data | Must have |
| FR-03 | Implement data quality validation rules and generate quality reports | Must have |
| FR-04 | Create Gold tables containing business metrics and KPIs | Must have |
| FR-05 | Build a Power BI dashboard using only Gold tables | Must have |
| FR-06 | Simulate streaming JSON events and process them into the Bronze layer | Must have |

---

## 2. Data Requirements

| ID | Requirement |
|---|---|
| DR-01 | Raw source files must contain realistic civic service request data with valid keys |
| DR-02 | Synthetic Metrovale data assumptions must be documented |
| DR-03 | Data quality issues such as duplicates, null values, and invalid references should be included for validation |
| DR-04 | Sample data stored in GitHub must remain small and suitable for demonstration |

---

## 3. Dashboard Requirements

| ID | Requirement |
|---|---|
| BI-01 | Dashboard must use Gold tables only |
| BI-02 | Dashboard should include KPI cards, trend analysis, category comparison, borough analysis, and interactive filters |
| BI-03 | Dashboard insights must be documented in `docs/dashboard_insights.md` |
| BI-04 | Dashboard should display Total Requests, Open Requests, Closed Requests, Average Resolution Time, and Requests by Category |

---

## 4. Evidence Requirements

| ID | Requirement |
|---|---|
| EV-01 | Weekly logs must be committed to GitHub |
| EV-02 | Screenshots of notebooks, outputs, and dashboards must be stored in the `screenshots/` folder |
| EV-03 | External references must be listed in `docs/references.md` |
| EV-04 | AI usage must be disclosed in the weekly logs and documentation where applicable |
| EV-05 | All notebooks and documentation should be committed with meaningful Git commit messages |
