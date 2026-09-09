# Gold Metrics Definition

**Week:** 7  
**Purpose:** Define dashboard-ready Gold tables, KPI formulas, grains, sources, exclusions, and validation requirements.

---

## 1. Gold Table Catalog

| Gold Table Name | Grain | Source Table(s) | Purpose |
|---|---|---|---|
| `dim_date` | One row per calendar date | `cityfix.silver.trusted_service_requests` | Date dimension for time-based analysis |
| `dim_time_band` | One row per time band | `cityfix.silver.trusted_service_requests` | Time-of-day analysis |
| `dim_agency` | One row per agency | `cityfix.silver.trusted_service_requests` | Agency analysis |
| `dim_complaint_category` | One row per complaint category | `cityfix.silver.trusted_service_requests` | Complaint category analysis |
| `dim_geography_borough_zip` | One row per borough/ZIP combination | `cityfix.silver.trusted_service_requests` | Geographic analysis |
| `dim_request_status` | One row per request status | `cityfix.silver.trusted_service_requests` | Request status analysis |
| `dim_channel` | One row per request channel | `cityfix.silver.trusted_service_requests` | Channel analysis |
| `dim_location_type` | One row per location type | `cityfix.silver.trusted_service_requests` | Location analysis |
| `fact_service_request` | One row per trusted service request | `cityfix.silver.trusted_service_requests` | Core request-level reporting |
| `fact_request_resolution` | One row per valid resolved request | `cityfix.silver.trusted_service_requests` | Resolution and SLA analysis |
| `fact_request_backlog_snapshot` | One row per open request per snapshot date | `cityfix.silver.trusted_service_requests` | Backlog and aging analysis |
| `fact_request_event_stream` | One row per request event | Event stream / future streaming source | Streaming-ready request events |
| `agency_sla_summary` | One row per agency | `fact_service_request`, `fact_request_resolution` | Agency SLA performance |
| `category_volume_summary` | One row per complaint category | `fact_service_request` | Complaint category volume analysis |
| `borough_backlog_summary` | One row per borough/snapshot date | `fact_request_backlog_snapshot` | Borough-level backlog analysis |
| `request_resolution_trend_summary` | One row per date/status trend | `fact_service_request`, `fact_request_resolution` | Resolution trend analysis |
| `channel_and_location_summary` | One row per channel/location combination | `fact_service_request` | Channel and location analysis |

---

## 2. KPI Definitions

### 2.1 Total Requests

**Definition:** Total number of distinct trusted service requests.

**Formula:**

```text
Total Requests = DISTINCTCOUNT(unique_key)
