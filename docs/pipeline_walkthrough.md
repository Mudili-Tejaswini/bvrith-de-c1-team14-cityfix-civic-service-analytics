# Pipeline Walkthrough

**Week:** 11  
**Purpose:** Explain the full end-to-end project flow.

---

## 1. Pipeline Run Order

| Step | Notebook / File | Output |
|---:|---|---|
| 1 | `src/generate_synthetic_data.py` | Raw and streaming sample data |
| 2 | `notebooks/01_data_exploration.ipynb` | Exploration and profiling evidence |
| 3 | `notebooks/02_bronze_ingestion.ipynb` | Bronze tables |
| 4 | `notebooks/03_silver_transformations.ipynb` | Silver tables |
| 5 | `notebooks/04_data_quality_checks.ipynb` | Data quality validation results |
| 6 | `notebooks/05_gold_aggregations.ipynb` | Gold metric tables |
| 7 | `notebooks/06_powerbi_export.ipynb` | Gold data exported for Power BI |
| 8 | `notebooks/07_streaming_simulation.ipynb` | Streaming Bronze tables and live metrics |

---

## 2. Architecture Explanation

The CityFix Civic Service Analytics project follows the Medallion Architecture. Synthetic raw datasets and streaming events are generated and loaded into the project. The raw files are explored to understand their structure, quality, and relationships. During Bronze ingestion, the raw data is stored without modification to preserve the original records. The Silver layer cleans, validates, standardizes, and enriches the data by removing duplicates, handling missing values, and applying business rules. Data quality checks ensure that only reliable records continue through the pipeline. The Gold layer creates aggregated business metrics and KPI tables for reporting. These Gold tables are exported to Power BI to build interactive dashboards for analysis. Finally, a streaming simulation processes live request events to demonstrate real-time data ingestion and analytics.
---

## 2.1 Week 7 – Gold Layer

The Week 7 Gold layer is built from the Trusted Silver data and provides the business-ready dimensional, fact, and summary tables required for analytics and Power BI reporting.

### Gold Dimensions

The Gold layer contains the following 8 dimensions:

- `dim_date`
- `dim_time_band`
- `dim_agency`
- `dim_complaint_category`
- `dim_geography_borough_zip`
- `dim_request_status`
- `dim_channel`
- `dim_location_type`

### Gold Fact Tables

The Gold layer contains the following 4 fact tables:

- `fact_service_request` – one row per trusted service request.
- `fact_request_resolution` – one row per valid resolved request.
- `fact_request_backlog_snapshot` – one row per open request per snapshot date.
- `fact_request_event_stream` – schema-ready event fact for future streaming events.

### Gold Summary Tables

The Gold layer contains the following 5 summary tables:

- `agency_sla_summary`
- `category_volume_summary`
- `borough_backlog_summary`
- `request_resolution_trend_summary`
- `channel_and_location_summary`

### Gold Validation Results

The Week 7 Gold layer was validated using reconciliation, uniqueness, chronology, and summary checks.

- Trusted Silver distinct requests: **179,701**
- Gold service requests: **179,701**
- Gold resolution requests: **165,200**
- Backlog snapshot rows: **2,314,218**
- Snapshot duplicate groups: **0**
- Resolution chronology invalid rows: **0**
- Agency SLA summary total: **179,701**
- Category volume summary total: **179,701**
- Channel and location summary total: **179,701**

All required Gold dimensions passed key uniqueness validation, and the Gold service request fact reconciled with the Trusted Silver request population.

The Gold layer is therefore ready for the Week 8 Power BI reporting stage.

---

## 3. Known Limitations

- The dataset is synthetic and intended for educational purposes only.
- Streaming events are simulated and do not represent live production data.
- Some location fields may contain missing values.
- Dashboard accuracy depends on successful completion of all notebook stages.
- The project is designed for Databricks Community Edition and may require changes for other environments.

---

## 4. How to Reproduce

1. Clone or open the project repository.
2. Review the README and project documentation.
3. Upload or generate the required raw datasets.
4. Execute all notebooks in the specified sequence.
5. Verify Bronze, Silver, and Gold outputs.
6. Review the data quality validation results.
7. Export Gold tables and open the Power BI dashboard.
8. Execute the streaming simulation notebook and verify live event processing.
9. Review screenshots and weekly logs for supporting evidence.
