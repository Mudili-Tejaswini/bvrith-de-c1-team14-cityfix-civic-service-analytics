# Dashboard Insights

**Week:** 9  
**Purpose:** Document evidence-backed business insights from the refined Power BI dashboard.

---

## 1. Dashboard Pages

| Dashboard Page | Purpose |
|---|---|
| Civic Operations | Monitor overall service request volume, backlog, channel, borough, and location-type metrics |
| Agency Performance | Review agency-level SLA and performance metrics |
| Resolution Trends | Monitor resolved request trends over time |
| Category Trends | Analyze service request volume by complaint category |

---

## 2. Key Performance Indicators (KPIs)

| KPI | Description | Owning Gold Table |
|---|---|---|
| Total Requests | Total number of service requests | `channel_and_location_summary` |
| Open Backlog | Number of currently open requests in the backlog summary | `borough_backlog_summary` |
| SLA Compliance Rate | Average SLA compliance rate across agencies | `agency_sla_summary` |
| Resolved Requests | Number of resolved service requests | `request_resolution_trend_summary` |
| Category Requests | Total requests by complaint category | `category_volume_summary` |

---

## 3. Dashboard Visualizations

| Visualization | Purpose |
|---|---|
| KPI Cards | Display important business metrics |
| Column Chart | Show total requests by channel |
| Column Chart | Show open backlog by borough |
| Column Chart | Show total requests by location type |
| Line Chart | Show resolved requests over time |
| Agency Summary | Review agency-level SLA performance |
| Slicers/Filters | Support filtering and interaction where applicable |

---

## 4. Approved Gold Sources

The Week 9 dashboard uses the approved Gold-layer tables identified during Week 8 validation.

| Gold Table | Purpose |
|---|---|
| `agency_sla_summary` | Agency SLA performance |
| `borough_backlog_summary` | Backlog by borough |
| `category_volume_summary` | Request volume by category |
| `channel_and_location_summary` | Requests by channel and location |
| `request_resolution_trend_summary` | Request resolution trends |

---

## 5. Week 9 Evidence-Based Insights

### Insight 1 — Resolved Requests in 2026

- **Question:** How many requests were resolved in 2026?
- **Observation:** The dashboard shows 770 resolved requests for 2026.
- **Filter/Time Scope:** 2026
- **Visual/Page:** Page 8 — Resolved Requests by year
- **Owning Gold:** `request_resolution_trend_summary`
- **Measure/Field:** `resolved_requests`
- **Evidence:** The 2026 data point displays 770.
- **Interpretation:** The dashboard reports 770 resolved requests for the displayed 2026 period.
- **Limitation:** This is a descriptive observation and does not establish the reason for the reported value.

---

## 6. Dashboard Interaction Validation

The dashboard interactions were reviewed during Week 9.

- Selecting a borough affects the channel visual through the existing dashboard interaction.
- Selecting a channel does not change the open backlog by borough visual.
- Selecting a location type does not produce an unintended change in the other reviewed visuals.
- Selecting a year on the resolution trend provides the corresponding value without causing an unintended cross-visual change.
- Interactions were reviewed without changing the intended meaning of the measures.

---

## 7. Dashboard Validation

Before final submission, verify that:

- The dashboard uses the approved Gold-layer sources.
- Important KPI values are traceable to their owning Gold tables.
- Filters and visual interactions behave as intended.
- Visual titles and labels clearly describe the displayed metric.
- No unsupported causal conclusions are made from descriptive dashboard values.
- Final Power BI values are reconciled against the corresponding Gold-layer outputs.
- Required Week 9 screenshots and documentation are completed.
- The final PBIX file is saved at `dashboard/powerbi_dashboard.pbix`.

---

## 8. Limitations

- Dashboard insights are descriptive and should not be interpreted as causal explanations.
- Any value should be interpreted within the filter and time scope shown in the dashboard.
- Final KPI reconciliation should use the same filter state and the owning Gold table.
- Any unresolved difference between Power BI and Gold-layer values must be investigated and documented before final submission.

---

## 9. Week 10 Boundary

Week 9 focuses on dashboard refinement, interaction validation, reconciliation, and evidence-backed insights.

Streaming implementation is outside the Week 9 scope and belongs to the Week 10 boundary.
