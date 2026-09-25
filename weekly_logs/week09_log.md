# Week 09 Log — Power BI Dashboard Refinement

**Week:** 9  
**Date range:** 22 September 2026 – 28 September 2026  
**Team:** Team 14  
**Project:** CityFix Civic Service Analytics

---

## 1. Sprint Goal

Refine the existing Week 8 Power BI dashboard using the approved Gold-layer datasets.

Validate dashboard visuals, interactions, relationships, measures, documentation, and evidence while preserving the intended meaning of the existing KPIs.

---

## 2. Work Completed

| Task | Owner | Status | Evidence |
|---|---|---|---|
| Reviewed existing Week 8 Power BI dashboard | Team 14 | Done | `dashboard/powerbi_dashboard.pbix` |
| Reviewed approved Gold-layer sources | Team 14 | Done | Databricks Gold validation |
| Reviewed Gold table grains, keys, and data types | Team 14 | Done | Week 8 validation screenshots |
| Reviewed Power BI model relationships | Team 14 | Done | `week09_01_final_model.png` |
| Refined Civic Operations dashboard page | Team 14 | Done | `week09_02_refined_page_01.png` |
| Reviewed dashboard visual titles and labels | Team 14 | Done | Power BI dashboard |
| Tested dashboard interactions | Team 14 | Done | `week09_04_filter_interaction.png` |
| Reviewed resolution trend visual | Team 14 | Done | Page 8 |
| Documented evidence-based dashboard insight | Team 14 | Done | `docs/dashboard_insights.md` |
| Updated dashboard README | Team 14 | Done | `dashboard/README.md` |
| Reviewed Power BI Gold reconciliation | Team 14 | In progress | `dashboard/README.md` |
| Prepared Week 9 evidence requirements | Team 14 | In progress | `screenshots/week09_*.png` |

---

## 3. Key Decisions

- The existing Week 8 Power BI dashboard was refined instead of rebuilding the dashboard from scratch.
- The approved Gold-layer tables were retained as the intended dashboard sources.
- Existing KPI measure meanings were preserved during dashboard refinement.
- Gold tables with different grains were not directly joined merely because they contained similarly named columns.
- Dashboard interactions were tested to identify intended and unintended cross-visual changes.
- Dashboard insights were documented using observed Power BI values and their corresponding owning Gold tables.
- Streaming implementation was kept outside the Week 9 scope and reserved for the Week 10 boundary.

---

## 4. Blockers / Risks

| Blocker | Impact | Help Needed |
|---|---|---|
| Power BI Total Requests card displayed approximately 45K while the validated Databricks Gold total was 179701 | Final reconciliation is not yet complete | Investigate Power BI source data, filters, aggregation, model, and refresh state |
| DBFS-based temporary export route was unavailable because DBFS access was disabled | Direct temporary export/re-read validation could not be used | Continue using the controlled Databricks Gold connection |
| Multiple Gold tables are present in the Power BI model | Final source-use verification is required | Confirm that only approved Gold sources are used by final dashboard visuals |

---

## 5. Evidence Added to GitHub

- `dashboard/README.md` updated with Week 9 dashboard documentation.
- `docs/dashboard_insights.md` updated with the Week 9 evidence-based insight.
- `dashboard/powerbi_dashboard.pbix` retained as the final dashboard file.
- Week 9 screenshot evidence is being prepared under `screenshots/`.
- `weekly_logs/week09_log.md` updated with the Week 9 work log.

---

## 6. AI Transparency Note

| Question | Response |
|---|---|
| Where AI helped | AI was used to provide step-by-step guidance for dashboard refinement, documentation structure, Power BI validation, and GitHub file updates. |
| What we changed after AI suggestion | Dashboard documentation, README content, insights documentation, and the Week 9 log were updated based on the actual project work and observed Power BI results. |
| What we verified manually | Gold table row counts, columns, keys, duplicate checks, Power BI visuals, dashboard interactions, displayed values, and model relationships were manually reviewed. |
| What we can explain without AI | The team can explain the selected Gold sources, dashboard measures, visual purposes, interaction behavior, validation checks, and the current reconciliation difference. |

---

## 7. Next Week Preparation

- Complete the reconciliation of important Power BI values with the owning Gold-layer outputs.
- Complete the remaining Week 9 dashboard evidence screenshots.
- Verify that the final dashboard uses only the approved Gold sources.
- Save and verify the final `dashboard/powerbi_dashboard.pbix`.
- Prepare for the Week 10 scope, including streaming-related work if required.
