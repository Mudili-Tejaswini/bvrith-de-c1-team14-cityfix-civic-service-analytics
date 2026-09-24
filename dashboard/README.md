Copy-paste this **entire content** into `dashboard/README.md`:

````markdown
# CityFix Power BI Dashboard

## Overview

This folder contains the Week 8 Power BI dashboard for the CityFix Civic Service Analytics project.

The dashboard uses approved Gold-layer outputs from the Databricks `cityfix.gold` schema.

Expected Power BI file:

```text
dashboard/powerbi_dashboard.pbix
````

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

The selected Gold sources used for the dashboard are:

| Gold Table                         | Purpose                          | Dashboard Use    |
| ---------------------------------- | -------------------------------- | ---------------- |
| `agency_sla_summary`               | Agency SLA performance           | SLA Dashboard    |
| `borough_backlog_summary`          | Backlog by borough               | Civic Operations |
| `category_volume_summary`          | Request volume by category       | Category Trends  |
| `channel_and_location_summary`     | Requests by channel and location | Civic Operations |
| `request_resolution_trend_summary` | Request resolution trends        | SLA / Trends     |

Power BI dashboard sources are intended to come from the approved Gold layer only. Raw, Bronze, Silver, Candidate Silver, Trusted Silver detail, and Quarantine data are not used as dashboard sources.

## Gold Table Grain and Keys

### 1. agency_sla_summary

**Rows:** 12

**Grain:** Agency-level SLA summary

**Key:**

* `agency_key`

**Main fields:**

* `total_requests`
* `sla_eligible_requests`
* `sla_met_requests`
* `avg_resolution_hours`
* `sla_compliance_rate`

---

### 2. borough_backlog_summary

**Rows:** 15,800

**Grain:** Snapshot date and geography

**Composite key:**

* `snapshot_date`
* `geography_key`

**Main field:**

* `open_backlog`

---

### 3. category_volume_summary

**Rows:** 32

**Grain:** Complaint category

**Key:**

* `complaint_category_key`

**Main fields:**

* `total_requests`
* `mapped_requests`

---

### 4. channel_and_location_summary

**Rows:** 41

**Grain:** Channel and location type

**Keys:**

* `channel_key`
* `location_type_key`

**Main fields:**

* `total_requests`
* `avg_resolution_hours`
* `sla_met_requests`

---

### 5. request_resolution_trend_summary

**Rows:** 392

**Grain:** Resolution date

**Key:**

* `resolution_date`

**Main fields:**

* `resolved_requests`
* `avg_resolution_hours`
* `min_resolution_hours`
* `max_resolution_hours`

## Relationships

The selected Gold tables have different grains and are treated as separate summary-level datasets.

Relationships are created only where the Gold design and cardinality are understood.

The dashboard does not directly join two summary or fact Gold tables merely because they contain a similarly named column.

Where a safe relationship is not required, the Gold tables remain independent.

## Measures

The following measures were created for the first working Power BI dashboard.

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

## Dashboard Pages

### Civic Operations

The first working dashboard page contains operational KPIs and visuals including:

* Total Requests
* Open Backlog
* SLA Compliance Rate
* Total Requests by Channel
* Open Backlog by Borough
* Total Requests by Location Type
* Resolved Requests Over Time

### Category Trends

A dashboard page was created for category-level request analysis using the `category_volume_summary` Gold source.

Further visual refinement and detailed insight storytelling are part of Week 9.

## Validation

The selected Gold tables were validated in Databricks before Power BI use.

| Gold Table                         |   Rows | Columns | Duplicate Rows |
| ---------------------------------- | -----: | ------: | -------------: |
| `agency_sla_summary`               |     12 |       6 |              0 |
| `borough_backlog_summary`          | 15,800 |       3 |              0 |
| `category_volume_summary`          |     32 |       3 |              0 |
| `channel_and_location_summary`     |     41 |       5 |              0 |
| `request_resolution_trend_summary` |    392 |       5 |              0 |

### Key Validation Results

| Table                              | Key                      | Distinct Values | Null Values |
| ---------------------------------- | ------------------------ | --------------: | ----------: |
| `agency_sla_summary`               | `agency_key`             |              12 |           0 |
| `borough_backlog_summary`          | `snapshot_date`          |             395 |           0 |
| `borough_backlog_summary`          | `geography_key`          |              40 |           0 |
| `category_volume_summary`          | `complaint_category_key` |              32 |           0 |
| `channel_and_location_summary`     | `channel_key`            |               6 |           0 |
| `channel_and_location_summary`     | `location_type_key`      |               8 |           0 |
| `request_resolution_trend_summary` | `resolution_date`        |             392 |           0 |

The composite key:

```text
snapshot_date + geography_key
```

for `borough_backlog_summary` was checked and found to be unique.

All five selected Gold tables were also checked for duplicate rows. The total row count and distinct row count matched for each selected table.

## Gold Reconciliation

The `channel_and_location_summary` Gold table was checked in Databricks.

The validated Gold total for `total_requests` was:

```text
179701
```

The Power BI `Total Requests` measure is owned by:

```text
channel_and_location_summary
```

and uses:

```DAX
SUM(channel_and_location_summary[total_requests])
```

Other dashboard measures are mapped directly to their respective Gold source tables.

## Power BI Connection and Refresh

The dashboard uses a Databricks connection to the `cityfix.gold` schema.

The Power BI model should be refreshed from the same governed Gold source.

During Week 8, an attempted DBFS-based temporary export route was not available because DBFS access was disabled in the Databricks environment. The controlled Databricks Gold connection was therefore used for the Power BI hand-off.

No manual correction of Gold values was performed.

## Evidence

Week 8 execution evidence is stored in:

```text
screenshots/
```

Expected naming pattern:

```text
screenshots/week08_*.png
```

Screenshots should contain genuine Databricks validation and Power BI execution evidence.

## Repository Files

The main Week 8 repository files are:

```text
notebooks/06_powerbi_export.ipynb
dashboard/powerbi_dashboard.pbix
dashboard/README.md
screenshots/week08_*.png
weekly_logs/week08_log.md
```

The Week 9 dashboard insights document is:

```text
docs/dashboard_insights.md
```

This document is reserved for Week 9 refinement and insight work.

## PBIX File-Size Rule

The preferred submission is the PBIX file together with the dashboard screenshots.

If the `.pbix` file becomes too large to manage cleanly in GitHub, retain the final screenshots and dashboard documentation in this repository and add a short note explaining where the PBIX is stored for mentor review.

Do not upload multiple heavy PBIX versions into GitHub.

## Week 8 Boundary

Week 8 establishes:

* Approved Gold source validation
* Gold hand-off to Power BI
* Working Power BI model
* Data type and model validation
* First working dashboard pages and visuals
* Dashboard measures
* Gold reconciliation
* Repository documentation
* Genuine execution evidence


