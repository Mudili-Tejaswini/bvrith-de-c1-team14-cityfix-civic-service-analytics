# Data Quality Summary

**Week:** 6  
**Purpose:** Summarize data quality rules, failures and business impact.

---

## 1. Quality Rule Results

| Rule ID | Rule Name | Severity | Passed Count | Failed Count | Business Impact |
|---|---|---|---:|---:|---|
| DQ-01 | Required ID not null | High | 10000 | 0 | Records without IDs cannot be trusted |
| DQ-02 | Duplicate key check | High | 9998 | 2 | Duplicate keys distort metrics |
| DQ-03 | Valid reference key | Medium | 9995 | 5 | Invalid references affect joins |
| DQ-04 | Valid timestamp order | Medium | 9997 | 3 | Time-based metrics may be wrong |

---

## 2. Failed Record Examples

| Rule ID | Sample Record ID | Failure Reason | Action / Handling |
|---|---|---|---|
| DQ-02 | REQ-004521 | Duplicate Request ID | Removed duplicate record |
| DQ-03 | REQ-006318 | Invalid Agency Code | Flagged for reference validation |
| DQ-04 | REQ-008745 | Closed Date earlier than Created Date | Excluded from Gold metrics |

---

## 3. What Should Block Gold Metrics?

The following rules should block or flag Gold table generation:

- Missing or null Request ID should block Gold table generation because every record must have a unique identifier.
- Duplicate Request IDs should be removed before Gold metrics are calculated.
- Invalid Agency or Category reference values should be flagged and corrected before joins.
- Invalid timestamp order (Closed Date earlier than Created Date) should be excluded from KPI calculations.

---

## 4. Quality Summary

The overall quality of the dataset is good and suitable for analytical processing. Most validation rules passed successfully, with only a small number of failed records. Duplicate request IDs and invalid reference values were identified and handled before further processing. Records with incorrect timestamp order were excluded from Gold metrics to maintain reporting accuracy. Missing IDs were not observed in the dataset. The Silver layer applies validation and cleaning before data reaches the Gold layer. Mentors should review duplicate handling, reference validation, and timestamp quality checks to ensure the reliability of dashboard metrics.
