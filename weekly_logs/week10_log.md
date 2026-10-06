# Week 10 Log — Streaming Simulation

**Week:** 10  
**Date range:** Week 10 internship period  
**Team:** Team 14  
**Project:** CityFix Civic Service Analytics

---

## 1. Sprint Goal

The goal of Week 10 was to simulate CityFix service request event streaming using JSON event files, Databricks Auto Loader, and Structured Streaming.

The work focused on incremental event processing, event monitoring, live metrics, streaming documentation, and Kafka-style event schema awareness.

---

## 2. Work Completed

| Task | Owner | Status | Evidence |
|---|---|---|---|
| Created controlled JSON streaming input files | Team 14 | Done | `drop_01.json`, `drop_02.json`, `drop_03.json` |
| Configured Auto Loader for JSON events | Team 14 | Done | `07_streaming_simulation.ipynb` |
| Processed events using Structured Streaming | Team 14 | Done | `week10_streaming_output.png` |
| Verified Drop 03 event types | Team 14 | Done | Databricks notebook output |
| Created event-type live metric | Team 14 | Done | `week10_live_metric.png` |
| Updated Structured Streaming design | Team 14 | Done | `streaming/structured_streaming_design.md` |
| Updated Kafka-style event schema | Team 14 | Done | `streaming/kafka_event_schema.json` |

---

## 3. Key Decisions

- Used controlled JSON files to simulate incoming CityFix service request events.
- Used Databricks Auto Loader for incremental JSON file ingestion.
- Used Structured Streaming for processing the streaming events.
- Used `NEW_REQUEST` and `STATUS_UPDATE` as the event types.
- Used event count by event type as the simple streaming metric.
- Kafka was treated as design-only architecture awareness and was not installed.
- Used the supported `AvailableNow` trigger because the available Databricks serverless environment does not support the continuous `ProcessingTime` trigger.

---

## 4. Blockers / Risks

| Blocker | Impact | Help Needed |
|---|---|---|
| Public DBFS root was disabled in the Databricks environment | Streaming files could not be stored in the public DBFS location | Used the project Unity Catalog Volume instead |
| Continuous `ProcessingTime` trigger was not supported by the available serverless cluster | A continuously running trigger could not be demonstrated | Used the supported `AvailableNow` trigger for controlled incremental processing |

---

## 5. Evidence Added to GitHub

- `streaming/structured_streaming_design.md` updated.
- `streaming/kafka_event_schema.json` updated.
- `week10_streaming_output.png` added.
- `week10_live_metric.png` added.
- `notebooks/07_streaming_simulation.ipynb` updated and executed.
- Three controlled input drops were used: `drop_01.json`, `drop_02.json`, and `drop_03.json`.

---

## 6. AI Transparency Note

| Question | Response |
|---|---|
| Where AI helped | AI helped with step-by-step Databricks guidance, debugging streaming errors, explaining Auto Loader and Structured Streaming, and drafting the Week 10 documentation. |
| What we changed after AI suggestion | The streaming input location was changed from an unavailable public DBFS path to the project Unity Catalog Volume. The streaming trigger was also changed to `AvailableNow` because the available serverless environment did not support `ProcessingTime`. |
| What we verified manually | The JSON files, streaming input folder, processed event counts, event types, unique request count, notebook outputs, and screenshots were manually verified in Databricks. |
| What we can explain without AI | We can explain the JSON event structure, Auto Loader ingestion, Structured Streaming processing, checkpoint purpose, event-type metrics, controlled input drops, and the limitations of the student streaming simulation. |

---

## 7. Next Week Preparation

- Review the complete CityFix data engineering pipeline from Bronze through Gold and streaming simulation.
- Prepare for pipeline integration, documentation cleanup, final evidence review, and project demonstration.
