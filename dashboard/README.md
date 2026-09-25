# CityFix Power BI Dashboard

## Overview

This folder contains the Power BI dashboard for the CityFix Civic Service Analytics project.

The dashboard is being refined during Week 9 using the approved Gold-layer outputs from the Databricks `cityfix.gold` schema.

Expected Power BI file:

```text
dashboard/powerbi_dashboard.pbix
```

---

## Power BI Source

Power BI is connected to the Databricks Gold layer.

**Catalog:**

```text
cityfix
```

**Schema:**

```text
gold
```

The approved Gold sources identified for the dashboard are:

| Gold Table | Purpose | Dashboard Use |
|---|---|---|
| `agency_sla_summary` | Agency SLA performance | Agency/SLA analysis |
| `borough_backlog_summary` | Backlog by borough | Civic Operations |
| `category_volume_summary` | Request volume by category | Category analysis |
| `channel_and_location_summary` | Requests by channel and location | Civic Operations |
| `request_resolution_trend_summary` | Request resolution trends | Resolution Trends |

The dashboard is intended to use approved Gold-layer outputs rather than Raw, Bronze, Silver, Candidate Silver, Trusted Silver detail, or Quarantine data.

---

## Gold Table Grain and Keys

### 1. agency_sla_summary

**Rows:** 12

**Grain:** Agency-level SLA summary

**Key:**

- `agency_key`

**Main fields:**

- `total_requests`
- `sla_eligible_requests`
- `sla_met_requests`
- `avg_resolution_hours`
- `sla_compliance_rate`

---

### 2. borough_backlog_summary

**Rows:** 15,800

**Grain:** Snapshot date and geography

**Composite key:**

- `snapshot_date`
- `geography_key`

**Main field:**

- `open_backlog`

---

### 3. category_volume_summary

**Rows:** 32

**Grain:** Complaint category

**Key:**

- `complaint_category_key`

**Main fields:**

- `total_requests`
- `mapped_requests`

---

### 4. channel_and_location_summary

**Rows:** 41

**Grain:** Channel and location type

**Keys:**

- `channel_key`
- `location_type_key`

**Main fields:**

- `total_requests`
- `avg_resolution_hours`
- `sla_met_requests`

---

### 5. request_resolution_trend_summary

**Rows:** 392

**Grain:** Resolution date

**Key:**

- `resolution_date`

**Main fields:**

- `resolved_requests`
- `avg_resolution_hours`
- `min_resolution_hours`
- `max_resolution_hours`

---

## Relationships

The selected Gold tables have different grains and are treated as separate summary-level datasets.

Relationships are retained only where the Gold design and cardinality are understood.

The dashboard does not directly join summary-level Gold tables merely because they contain similarly named columns.

Where a safe relationship is not required, the Gold tables remain independent.

During Week 9, the existing model relationships were reviewed without changing their intended design.

---

## Measures

The following measures are used in the Power BI dashboard.

### Total Requests

```DAX
Total Requests =
SUM(channel_and_location_summary[total_requests])
```

### Open Backlog

```DAX
Open Backlog =
SUM(borough_backlog_summary[open_backlog])
```

### SLA Compliance Rate

```DAX
SLA Compliance Rate =
AVERAGE(agency_sla_summary[sla_compliance_rate])
```

### Resolved Requests

```DAX
Resolved Requests =
SUM(request_resolution_trend_summary[resolved_requests])
```

### Category Requests

```DAX
Category Requests =
SUM(category_volume_summary[total_requests])
```

---

## Dashboard Pages

### Civic Operations

The main Civic Operations page contains operational KPIs and visuals including:

- Total Requests
- Open Backlog
- SLA Compliance Rate
- Total Requests by Channel
- Open Backlog by Borough
- Total Requests by Location Type
- Resolved Requests Over Time

The page was refined during Week 9 for clearer visual hierarchy, titles, labels, spacing, and interaction behavior.

---

### Category Trends

A Category Trends page is available for category-level analysis using the `category_volume_summary` Gold source.

Further refinement is performed only where the visual is genuinely required for the dashboard's business questions.

---

## Week 9 Interaction Validation

Dashboard interactions were reviewed during Week 9.

The following behaviors were observed:

- Selecting a borough affects the channel visual through the existing dashboard interaction.
- Selecting a channel does not change the open backlog by borough visual.
- Selecting a location type does not produce an unintended change in the other reviewed visuals.
- Selecting a year on the resolution trend displays the corresponding value without an unintended cross-visual change.
- Interactions were reviewed without changing the intended meaning of the measures.

The interaction behavior is documented as part of the Week 9 dashboard refinement process.

---

## Gold Validation

The selected Gold tables were validated in Databricks before Power BI use.

| Gold Table | Rows | Columns | Duplicate Rows |
|---|---:|---:|---:|
| `agency_sla_summary` | 12 | 6 | 0 |
| `borough_backlog_summary` | 15,800 | 3 | 0 |
| `category_volume_summary` | 32 | 3 | 0 |
| `channel_and_location_summary` | 41 | 5 | 0 |
| `request_resolution_trend_summary` | 392 | 5 | 0 |

### Key Validation Results

| Table | Key | Distinct Values | Null Values |
|---|---|---:|---:|
| `agency_sla_summary` | `agency_key` | 12 | 0 |
| `borough_backlog_summary` | `snapshot_date` | 395 | 0 |
| `borough_backlog_summary` | `geography_key` | 40 | 0 |
| `category_volume_summary` | `complaint_category_key` | 32 | 0 |
| `channel_and_location_summary` | `channel_key` | 6 | 0 |
| `channel_and_location_summary` | `location_type_key` | 8 | 0 |
| `request_resolution_trend_summary` | `resolution_date` | 392 | 0 |

The composite key:

```text
snapshot_date + geography_key
```

for `borough_backlog_summary` was checked and found to be unique.

All five selected Gold tables were checked for duplicate rows. The total row count and distinct row count matched for each selected table.

---

## Gold Reconciliation

The final Power BI dashboard values were reconciled against the owning Gold table using the same filter state.

- Gold source: `cityfix.gold.channel_and_location_summary`
- Gold `Total Requests`: **179701**
- Power BI `Total Requests` card on the **Civic Operations** page: **180K**
- The Power BI value is displayed in rounded form, so **180K corresponds to the Gold value of 179701**.
- Screenshot evidence: `screenshots/week09_05_filtered_reconciliation.png`

Reconciliation status: **Validated**

The reconciliation confirms that the Power BI Total Requests KPI is based on the approved Gold source and preserves the intended measure meaning.
---

## Power BI Connection and Refresh

The dashboard uses a Databricks connection to the `cityfix.gold` schema.

The Power BI model is intended to refresh from the same governed Gold source.

During Week 8, an attempted DBFS-based temporary export route was not available because DBFS access was disabled in the Databricks environment.

The controlled Databricks Gold connection was therefore used for the Power BI hand-off.

No manual correction of Gold values was performed.

---

## Dashboard Insights

Evidence-backed Week 9 insights are documented in:

```text
docs/dashboard_insights.md
```

The current documented insight is based on the Resolution Trends visual:

- 2026 resolved requests: 770
- Visual: Page 8 — Resolved Requests by year
- Owning Gold: `request_resolution_trend_summary`
- Measure/Field: `resolved_requests`

Insights are descriptive and do not claim unsupported causes.

---

## Evidence

Week 9 execution evidence is stored in:

```text
screenshots/
```

Expected Week 9 naming pattern:

```text
screenshots/week09_*.png
```

Required evidence includes:

```text
week09_01_final_model.png
week09_02_refined_page_01.png
week09_03_refined_page_*.png
week09_04_filter_interaction.png
week09_05_filtered_reconciliation.png
week09_06_insights_evidence.png
```

Additional page screenshots should only be included where the page is genuinely used.

Screenshots should contain genuine Databricks validation and Power BI execution evidence.

---

## Repository Files

The main dashboard-related files are:

```text
dashboard/powerbi_dashboard.pbix
dashboard/README.md
docs/dashboard_insights.md
notebooks/06_powerbi_export.ipynb
screenshots/week09_*.png
weekly_logs/week09_log.md
```

---

## PBIX File-Size Rule

The preferred submission is the final PBIX file together with dashboard screenshots and documentation.

If the `.pbix` file becomes too large to manage cleanly in GitHub, retain the final screenshots and dashboard documentation in the repository and add a short note explaining where the PBIX is stored for mentor review.

Do not upload multiple heavy PBIX versions into GitHub.

---

## Week 9 Scope

Week 9 focuses on:

- Reopening and refining the existing Power BI dashboard
- Reviewing page purpose and visual hierarchy
- Reviewing visual titles and labels
- Testing slicers, filters, and interactions
- Reviewing Gold-table relationships
- Preserving the meaning of existing measures
- Reconciling important Power BI values with owning Gold outputs
- Documenting evidence-backed dashboard insights
- Updating dashboard documentation
- Capturing final dashboard evidence

---

## Week 10 Boundary

Week 10 work is outside the Week 9 scope.

Streaming implementation and related live-event work should not be added as Week 9 dashboard work.

The Week 9 focus remains dashboard refinement, interaction validation, reconciliation, documentation, and evidence-backed insights.
