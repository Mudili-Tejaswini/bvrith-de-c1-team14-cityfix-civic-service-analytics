# Problem Charter

**Week:** 1  
**Owner(s):** M. Tejaswini, A. Usha, K. Sri Hasitha  
**Project:** CityFix – Civic Service Analytics

---

## 1. Problem Context

Explain the domain in simple language.

CityFix is a Civic Service Analytics project based on a **synthetic Metrovale civic service request dataset**. It represents how municipal authorities manage public complaints and service requests.

The data includes request details, agency information, complaint categories, boroughs, request status, ZIP codes, and timestamps.

Raw data alone is not reliable because it may contain duplicate records, missing values, invalid agency codes, and incorrect timestamps. These issues can affect reporting, operational efficiency, and decision-making.

The final dashboard will help Civic Operations Leads, Agency Coordinators, Borough Managers, and Public Service Analysts monitor service performance, identify trends, and make informed decisions.

---

## 2. Engineering Problem

Write the data engineering problem clearly.

The project converts multiple synthetic civic service datasets into trusted Bronze, Silver, Data Quality, Gold, and dashboard-ready outputs using Databricks, PySpark, Spark SQL, Delta Lake, and Power BI. The pipeline cleans, validates, transforms, and organizes the data to produce reliable analytics and support streaming simulation.

---

## 3. Users / Stakeholders

| User / Stakeholder | What they need from the data |
|--------------------|------------------------------|
| Civic Operations Lead | Monitor service request volume, backlog, and overall performance |
| Agency Coordinator | Track agency-wise performance and closure rates |
| Borough Manager | Analyze unresolved requests across boroughs |
| Public Service Analyst | Monitor live request activity and generate reports |

---

## 4. Scope Inclusions

The project includes:

- Raw source data ingestion
- Bronze layer implementation
- Silver layer transformations
- Data quality validation
- Gold metric generation
- Power BI dashboard creation
- Streaming data simulation
- GitHub documentation and weekly project evidence

---

## 5. Scope Exclusions

The project does not include:

- Production deployment
- Real customer or personal data
- Complaint registration website
- Mobile application
- Payment gateway integration
- AI-based complaint prediction
- Copied internet projects
- Fake screenshots or undocumented AI-generated work

---

## 6. Success Criteria

The project will be considered successful if:

- Raw data is successfully processed into Bronze, Silver, and Gold layers.
- Data quality checks are implemented and documented.
- Gold tables are used as the only source for the Power BI dashboard.
- Streaming simulation executes successfully.
- Dashboard KPIs match Gold layer metrics.
- GitHub repository contains complete weekly documentation, notebooks, screenshots, and evidence.
- The entire pipeline can be explained from source data to dashboard.
- All three team members can demonstrate and explain the complete project.
