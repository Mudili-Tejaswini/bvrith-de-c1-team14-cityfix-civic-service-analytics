# Gold Metrics Definition

**Week:** 7  
**Purpose:** Define dashboard-ready Gold tables and KPI formulas.

---

## 1. Gold Table Catalog

| Gold Table Name | Grain | Source Table(s) | Purpose |
|---|---|---|---|
| `gold_service_requests` | One row per service request | `silver_service_requests` | Provides cleaned request-level data for reporting |
| `gold_complaint_summary` | One row per complaint category | `silver_service_requests` | Summarizes complaint trends and category-wise metrics |

---

## 2. KPI Definitions

| KPI Name | Formula | Grain | Dashboard Page | Notes |
|---|---|---|---|---|
| Total Requests | COUNT(record_id) | Daily | Overview | Total number of service requests received |
| Closed Requests | COUNT(status='Closed') | Daily | Overview | Total number of completed requests |
| Open Requests | COUNT(status='Open') | Daily | Overview | Total number of pending requests |
| Average Resolution Time | AVG(closed_date - created_date) | Weekly | Performance | Average time taken to resolve requests |
| Requests by Category | COUNT(record_id) GROUP BY complaint_category | Category | Complaint Analysis | Number of requests for each complaint category |
| Requests by Borough | COUNT(record_id) GROUP BY borough | Borough | Location Analysis | Distribution of requests across boroughs |
| Agency Performance | COUNT(record_id) GROUP BY agency_name | Agency | Agency Dashboard | Number of requests handled by each agency |

---

## 3. Validation Checks

Before using Gold tables in Power BI, verify:

- Gold row counts are reasonable.
- No unexpected nulls exist in key dashboard fields.
- KPI totals match manual spot checks.
- Power BI connects to Gold outputs only.
- Metric definitions are documented clearly.
- Gold tables contain only validated and cleaned records.
- Aggregated metrics match Silver layer calculations.
