# Synthetic Data Assumptions

**Week:** 2  
**Purpose:** Document how educational data is created.

---

## 1. Synthetic Data Boundary

This project uses synthetic educational data only. It must not be presented as real company, customer, citizen, player, patient, government, or platform data.

---

## 2. Domain Assumptions

| Area | Assumption |
|---|---|
| Geography / scope | Synthetic Metrovale City with multiple boroughs and ZIP code regions |
| Time period | January 2026 to December 2026 |
| Source systems | Service Request System, Agency Management System, and Reference Data Files |
| Event types | Service request creation, request update, request closure, and streaming request events |
| Reference data | Agencies, Boroughs, Complaint Categories, and ZIP Geography |

---

## 3. Data Volume Assumptions

| File | Approximate Rows | Reason |
|---|---:|---|
| `requests.csv` | 10,000 | Main civic service request dataset |
| `agencies.csv` | 25 | Agency reference data |
| `categories.csv` | 30 | Complaint category reference data |
| `new_request_event.json` | 500 | Streaming event simulation |

---

## 4. Controlled Data Quality Issues

| Issue Type | Approx. Share | Why Include It |
|---|---:|---|
| Duplicate IDs | 0.2%–0.5% | Tests uniqueness |
| Missing values | 1%–3% | Tests completeness |
| Invalid reference keys | 0.5%–1% | Tests referential integrity |
| Negative / impossible values | 0.1%–0.5% | Tests range rules |
| Timestamp inconsistencies | 0.1%–0.3% | Tests chronology |

---

## 5. Manual Verification

Before using generated data, the team must check:

- Row counts are reasonable.
- Key fields exist.
- Dates and numeric values look realistic.
- Controlled defects exist but do not dominate the dataset.
- Source files are different enough to require real standardization.
- Bronze, Silver, and Gold outputs are generated successfully.
- Data quality validation passes before dashboard creation.
