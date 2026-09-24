# Week 08 Log — Gold-to-Power BI Dashboard Handoff

**Week:** 8  
**Date range:** 18 September 2026 – 24 September 2026  
**Team:** Team 14  
**Project:** CityFix Civic Service Analytics

---

## 1. Sprint Goal

Prove the approved Gold-table hand-off, connect the required Gold outputs to Power BI, and build the first working dashboard.

Validate Gold table grains, keys, duplicates, and important dashboard values, then record genuine execution evidence for the Week 8 submission.

---

## 2. Work Completed

| Task | Owner | Status | Evidence |
|---|---|---|---|
| Reviewed and selected approved Gold tables for Power BI | Team 14 | Done | `06_powerbi_export.ipynb` |
| Validated Gold table row counts, columns, and data types | Team 14 | Done | `week08_gold_source_validation.png` |
| Validated Gold hand-off and sample data | Team 14 | Done | `week08_gold_handoff.png` |
| Checked Gold keys, nulls, and duplicate rows | Team 14 | Done | `week08_key_duplicate_validation.png` |
| Connected approved Gold tables to Power BI | Team 14 | Done | Power BI dashboard |
| Created Power BI measures and first dashboard visuals | Team 14 | Done | `dashboard/powerbi_dashboard.pbix` |
| Reconciled important Power BI values with Gold data | Team 14 | In progress | Databricks reconciliation output |
| Updated dashboard documentation | Team 14 | Done | `dashboard/README.md` |

---

## 3. Key Decisions

- Power BI dashboard sources were selected from the approved Gold outputs.
- The selected Gold tables were mapped to business questions instead of creating one visual for every Gold table.
- Gold tables were kept independent where a safe shared relationship was not required.
- Dashboard measures were created from the approved Gold tables.
- Week 8 focused on the first working dashboard and evidence; dashboard insight writing and refinement are carried into Week 9.

---

## 4. Blockers / Risks

| Blocker | Impact | Help Needed |
|---|---|---|
| Databricks DBFS public root was disabled, so the planned DBFS CSV export path could not be used | Physical CSV export could not be completed through that path | Use the supported direct Gold-to-Power BI connection route |
| Power BI initially loaded more Gold tables than the five selected tables | Required model cleanup/verification before final submission | Remove or exclude unused Gold tables and verify the final PBIX uses only approved sources |

---

## 5. Evidence Added to GitHub

- `notebooks/06_powerbi_export.ipynb` — Gold source validation and hand-off checks.
- `dashboard/powerbi_dashboard.pbix` — first working Power BI dashboard.
- `dashboard/README.md` — Gold source mapping, measures, dashboard structure, validation and refresh documentation.
- `screenshots/week08_gold_source_validation.png`
- `screenshots/week08_gold_handoff.png`
- `screenshots/week08_key_duplicate_validation.png`
- `screenshots/week08_gold_reconciliation.png`
- `screenshots/week08_powerbi_dashboard.png`
- `weekly_logs/week08_log.md` — completed Week 8 record.

---

## 6. AI Transparency Note

| Question | Response |
|---|---|
| Where AI helped | AI helped with the structure of the Week 8 validation notebook, Power BI measure syntax, dashboard documentation structure, and troubleshooting the Databricks export-path limitation. |
| What we changed after AI suggestion | We adapted the suggested export approach to the available Databricks environment and used the supported Gold-to-Power BI connection route when the DBFS/Volume paths were unavailable. |
| What we verified manually | Gold table names, row counts, columns, data types, keys, null counts, duplicate-row checks, dashboard measures, Power BI visuals, and reconciliation outputs were checked manually in Databricks and Power BI. |
| What we can explain without AI | We can explain the purpose and grain of each selected Gold table, why the tables are used for the dashboard, how the Power BI measures aggregate Gold values, and what the validation checks prove. |

---

## 7. Next Week Preparation

- Continue from the same Week 8 Power BI dashboard rather than rebuilding it.
- Refine dashboard pages and visual layout where required.
- Test filters and visual interactions.
- Reconcile important filtered Power BI values with their owning Gold tables.
- Prepare `docs/dashboard_insights.md` with traceable, evidence-based observations.
