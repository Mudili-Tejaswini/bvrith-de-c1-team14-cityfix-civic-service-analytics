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
