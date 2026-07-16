# Problem Charter

**Week:** 1
**Owner(s):** M. Tejaswini, A. Usha, K. Sri Hasitha
**Project:** CityFix – Civic Service Analytics
---

## 1. Problem Context

Explain the domain in simple language.

CityFix is a Civic Service Analytics project based on official NYC 311 service request data. It represents how municipal authorities manage public complaints and service requests.

The data includes request details, agency information, complaint categories, boroughs, request status, and timestamps.

Raw data alone is not reliable because it may contain duplicate records, missing values, invalid agency codes, and incorrect timestamps. These issues can affect reporting and decision-making.

The final dashboard will help Civic Operations Leads, Agency Coordinators, Borough Managers, and Public Service Analysts monitor service performance and make informed decisions.
---

## 2. Engineering Problem

Write the data engineering problem clearly.

The project must convert multiple raw NYC 311 service request datasets into trusted Bronze, Silver, Data Quality, Gold, and dashboard-ready outputs using Databricks, Spark SQL, and Power BI. The pipeline will clean, validate, transform, and organize the data to produce reliable analytics and support streaming simulation.
---

## 3. Users / Stakeholders

| User / Stakeholder     | What they need from the data                                     |
| ---------------------- | ---------------------------------------------------------------- |
| Civic Operations Lead  | Monitor service request volume, backlog, and overall performance |
| Agency Coordinator     | Track agency-wise SLA performance and closure rates              |
| Borough Manager        | Analyze unresolved requests across boroughs                      |
| Public Service Analyst | Monitor live request activity and generate reports               |

---

## 4. Scope Inclusions

List what the team will build.
- Raw source files
- Bronze ingestion
- Silver standardization
- Data quality checks
- Gold metrics
- Power BI dashboard
- Streaming simulation
- GitHub documentation and weekly evidence
---

## 5. Scope Exclusions

List what the team will not build.
- No production application
- No real customer or personal data
- No complaint registration website
- No payment gateway integration
- No copied internet project submission
- No fake screenshots or unexplained AI-generated work
---

## 6. Success Criteria

By the end of 12 weeks, the project is successful if:
- Power BI dashboard uses Gold tables only.
- Data quality checks are implemented and documented.
- GitHub repository contains complete weekly evidence and project documentation.

- The pipeline can be explained end to end.
- The team can show Bronze, Silver, DQ, Gold, dashboard, and streaming evidence.
- All three students can explain the full project at a high level.
- GitHub contains weekly evidence and final submission files.
