# Structured Streaming Design

**Week:** 10  
**Project:** CityFix Civic Service Analytics  
**Purpose:** Document the Week 10 streaming simulation using JSON events, Auto Loader, and Structured Streaming.

---

## 1. Streaming Scenario

CityFix service-request events are simulated as JSON files arriving in a controlled streaming input folder. Databricks Auto Loader detects the available JSON files and Structured Streaming processes the events incrementally.

The simulation uses three controlled input drops:

- `drop_01.json`
- `drop_02.json`
- `drop_03.json`

The processed events contain CityFix request information such as request ID, unique request key, event type, timestamp, status, agency, complaint category, borough, channel, and priority.

---

## 2. Event Source

| Item | Description |
|---|---|
| Event file format | JSON |
| Input path | `/Volumes/cityfix/cityfix/cityfix-zenaiz/streaming/week10_input/` |
| Processing method | Databricks Auto Loader / Structured Streaming |
| Event types | `NEW_REQUEST`, `STATUS_UPDATE` |
| Schema handling | Auto Loader JSON schema inference |
| Checkpoint path | `/Volumes/cityfix/cityfix/cityfix-zenaiz/streaming/week10_checkpoint` |

---

## 3. Streaming Processing

The Week 10 notebook uses Auto Loader to read JSON files from the controlled input directory.

The first processing run successfully processed the available input events. A separate incremental run was then used to demonstrate streaming processing of the controlled event files.

The incremental processing result contained:

- **Total events:** 23
- **Unique requests:** 20
- **NEW_REQUEST events:** 12
- **STATUS_UPDATE events:** 11

The event-type counts provide a simple live metric for observing the processed streaming data.

---

## 4. Near-Real-Time Metric

The main streaming metric is the count of events by event type.

| Metric | Result |
|---|---:|
| NEW_REQUEST | 12 |
| STATUS_UPDATE | 11 |
| Total events | 23 |

This metric helps verify that streaming events are being processed and provides a simple view of the incoming event mix.

---

## 5. Event Flow

```text
Controlled JSON Event Files
          ↓
Week 10 Input Folder
          ↓
Databricks Auto Loader
          ↓
Structured Streaming
          ↓
Processed Streaming Events
          ↓
Event-Type Count Metric
