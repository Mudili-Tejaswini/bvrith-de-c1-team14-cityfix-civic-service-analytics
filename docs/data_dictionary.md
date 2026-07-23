# Data Dictionary

**Week:** 2  
**Purpose:** Define raw, reference, Silver, and streaming fields.

---

## 1. Source File Catalog

| File Name | Grain | Purpose | Approx. Rows | Notes |
|---|---|---|---:|---|
| `requests.csv` | One row per service request | Stores synthetic civic service requests | ~10,000 | Main raw dataset |
| `agencies.csv` | One row per agency | Agency reference information | ~25 | Lookup table |
| `categories.csv` | One row per complaint category | Complaint category reference | ~30 | Lookup table |
| `new_request_event.json` | One row per event | Streaming simulation | ~500 | JSON event files |

---

## 2. Raw File Schema: `requests.csv`

| Field Name | Data Type | Required? | Example | Description |
|---|---|---|---|---|
| `physical_record_key` | string | Yes | `PRK-000001` | Unique physical source record ID |
| `unique_key` | string | Yes | `REQ-000001` | Unique service request ID |
| `created_date` | timestamp | Yes | `2026-07-01 09:15:00` | Request creation date |
| `closed_date` | timestamp | No | `2026-07-03 14:30:00` | Request closure date |
| `agency_code` | string | Yes | `PWD` | Agency code |
| `agency_name_raw` | string | Yes | `Public Works Department` | Agency name |
| `complaint_category` | string | Yes | `Road Repair` | Complaint category |
| `complaint_type` | string | Yes | `Pothole` | Complaint type |
| `borough` | string | Yes | `North` | Borough name |
| `zip_code` | string | No | `500001` | ZIP code |
| `latitude` | double | No | `17.3850` | Latitude |
| `longitude` | double | No | `78.4867` | Longitude |

---

## 3. Raw File Schema: `agencies.csv`

| Field Name | Data Type | Required? | Example | Description |
|---|---|---|---|---|
| `agency_code` | string | Yes | `PWD` | Unique agency code |
| `agency_name` | string | Yes | `Public Works Department` | Agency name |
| `agency_type` | string | Yes | `Government` | Agency classification |

---

## 4. Reference File Schema

| Field Name | Data Type | Required? | Example | Description |
|---|---|---|---|---|
| `category_code` | string | Yes | `CAT-001` | Complaint category code |
| `category_name` | string | Yes | `Road Repair` | Complaint category name |
| `category_group` | string | Yes | `Infrastructure` | Complaint group |

---

## 5. Canonical Silver Table Design

Final Silver table name:

```text
silver_service_requests
```

| Silver Field | Data Type | Source Mapping | Business Meaning |
|---|---|---|---|
| `record_id` | string | `unique_key` | Canonical request ID |
| `event_date` | date | `created_date` | Date used for analytics |
| `agency_code` | string | `agency_code` | Agency responsible |
| `agency_name` | string | `agency_name_raw` | Standardized agency name |
| `complaint_category` | string | `complaint_category` | Complaint category |
| `complaint_type` | string | `complaint_type` | Complaint type |
| `borough` | string | `borough` | Borough location |
| `zip_code` | string | `zip_code` | ZIP code |
| `status` | string | `status` | Request status |

---

## 6. Streaming Event Schema

| Field Name | Data Type | Required? | Example | Description |
|---|---|---|---|---|
| `event_id` | string | Yes | `EVT-0001` | Unique event ID |
| `event_timestamp` | timestamp | Yes | `2026-07-03T10:15:00+05:30` | Event time |
| `event_type` | string | Yes | `REQUEST_CREATED` | Event category |
| `request_id` | string | Yes | `REQ-000001` | Related request ID |
| `agency_code` | string | Yes | `PWD` | Responsible agency |
| `complaint_category` | string | Yes | `Road Repair` | Complaint category |
| `borough` | string | Yes | `North` | Borough |
