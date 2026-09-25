# Week 09 Log — Power BI Dashboard Refinement

**Week:** 9
**Date range:** 22 September 2026 – 28 September 2026
**Team:** Team 14
**Project:** CityFix Civic Service Analytics

---

## 1. Sprint Goal

Refine the existing Week 8 Power BI dashboard using the approved Gold-layer datasets.

Validate dashboard visuals, interactions, relationships, measures, reconciliation, documentation, and evidence while preserving the intended meaning of the existing KPIs.

---

## 2. Work Completed

| Task                                             | Owner   | Status | Evidence                                |
| ------------------------------------------------ | ------- | ------ | --------------------------------------- |
| Reviewed existing Week 8 Power BI dashboard      | Team 14 | Done   | `dashboard/powerbi_dashboard.pbix`      |
| Reviewed approved Gold-layer sources             | Team 14 | Done   | Databricks Gold validation              |
| Reviewed Gold table grains, keys, and data types | Team 14 | Done   | Week 8 validation screenshots           |
| Reviewed Power BI model relationships            | Team 14 | Done   | `week09_01_final_model.png`             |
| Refined Civic Operations dashboard page          | Team 14 | Done   | `week09_02_refined_page_01.png`         |
| Reviewed dashboard visual titles and labels      | Team 14 | Done   | Power BI dashboard                      |
| Tested dashboard interactions                    | Team 14 | Done   | `week09_04_filter_interaction.png`      |
| Reviewed resolution trend visual                 | Team 14 | Done   | `week09_03_refined_page_08.png`         |
| Documented evidence-based dashboard insight      | Team 14 | Done   | `docs/dashboard_insights.md`            |
| Updated dashboard README                         | Team 14 | Done   | `dashboard/README.md`                   |
| Reconciled Power BI Total Requests with Gold     | Team 14 | Done   | `week09_05_filtered_reconciliation.png` |
| Prepared Week 9 evidence requirements            | Team 14 | Done   | `screenshots/week09_*.png`              |

---

## 3. Key Decisions

* The existing Week 8 Power BI dashboard was refined instead of rebuilding the dashboard from scratch.
* The approved Gold-layer tables were retained as the intended dashboard sources.
* Existing KPI measure meanings were preserved during dashboard refinement.
* Gold tables with different grains were not directly joined merely because they contained similarly named columns.
* Dashboard interactions were tested to identify intended and unintended cross-visual changes.
* Dashboard insights were documented using observed Power BI values and their corresponding owning Gold tables.
* The Power BI Total Requests value was reconciled against the owning Gold table.
* Streaming implementation was kept outside the Week 9 scope and reserved for the Week 10 boundary.

---

## 4. Blockers / Risks

| Blocker / Risk                                                                                        | Impact                                                       | Resolution / Status                                                             |
| ----------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------- |
| Power BI Total Requests card initially displayed approximately 45K during an earlier validation state | Required investigation before final reconciliation           | Resolved after verifying the correct Civic Operations page and final card value |
| Final Power BI Total Requests card displayed 180K while the validated Gold total was 179701           | Difference is due to Power BI rounded display                | Reconciled successfully; 180K corresponds to 179701                             |
| DBFS-based temporary export route was unavailable because DBFS access was disabled                    | Direct temporary export/re-read validation could not be used | Controlled Databricks Gold connection was used for Power BI                     |
| Multiple Gold tables are present in the Power BI model                                                | Source-use verification remains important                    | Approved Gold sources were reviewed against the dashboard visuals               |

---

## 5. Gold Reconciliation

The final Power BI dashboard value was reconciled against the owning Gold-layer output.

**Owning Gold source:**

```text
cityfix.gold.channel_and_location_summary
```

**Gold Total Requests:**

```text
179701
```

**Power BI Total Requests card on Civic Operations:**

```text
180K
```

The Power BI card displays the value in rounded form. Therefore, the displayed **180K** corresponds to the validated Gold value of **179701**.

The Power BI measure used was:

```DAX
Total Requests =
SUM(channel_and_location_summary[total_requests])
```

**Reconciliation status: Validated**

Evidence:

```text
screenshots/week09_05_filtered_reconciliation.png
```

No manual correction of Gold values was performed.

---

## 6. Evidence Added to GitHub

The following Week 9 documentation and evidence were completed:

* `dashboard/README.md`
* `docs/dashboard_insights.md`
* `dashboard/powerbi_dashboard.pbix`
* `weekly_logs/week09_log.md`

Week 9 screenshot evidence:

* `screenshots/week09_01_final_model.png`
* `screenshots/week09_02_refined_page_01.png`
* `screenshots/week09_03_refined_page_08.png`
* `screenshots/week09_04_filter_interaction.png`
* `screenshots/week09_05_filtered_reconciliation.png`
* `screenshots/week09_06_insights_evidence.png`

---

## 7. AI Transparency Note

| Question                            | Response                                                                                                                                                                               |
| ----------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Where AI helped                     | AI was used to provide step-by-step guidance for dashboard refinement, documentation structure, Power BI validation, reconciliation, and GitHub file updates.                          |
| What we changed after AI suggestion | Dashboard documentation, README content, insights documentation, reconciliation notes, and the Week 9 log were updated based on the actual project work and observed Power BI results. |
| What we verified manually           | Gold table row counts, columns, keys, duplicate checks, Power BI visuals, dashboard interactions, displayed values, model relationships, and reconciliation were manually reviewed.    |
| What we can explain without AI      | The team can explain the selected Gold sources, dashboard measures, visual purposes, interaction behavior, validation checks, reconciliation process, and documented insights.         |

---

## 8. Week 9 Completion Status

Week 9 dashboard refinement and validation activities have been completed.

The final reconciliation of the Total Requests KPI was validated against the owning Gold-layer output.

The required dashboard documentation, insight documentation, screenshots, and weekly log were prepared.

The final Power BI dashboard file is:

```text
dashboard/powerbi_dashboard.pbix
```

---

## 9. Week 10 Boundary

Week 9 focuses on Power BI dashboard refinement, interaction validation, Gold reconciliation, evidence, and documentation.

Streaming implementation is not included in Week 9.

Week 10 work will begin separately according to the internship roadmap and mentor guidance.
