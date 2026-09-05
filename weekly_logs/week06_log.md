Week 06 Log — Data Quality, Quarantine & Replay

Week: 6
Date range: 31 August 2026 – 5 September 2026
Team: Team 14
Project: CityFix: Civic Service Analytics

1. Sprint Goal

The goal of Week 06 was to implement and validate the Data Quality pipeline for CityFix. This included evaluating all eight approved DQ rules, routing failed records to Quarantine, and routing valid records to Trusted Silver.

The week also focused on completing an end-to-end rework and replay of one quarantined record through correction, Candidate/DQ validation, Trusted insertion, and closure evidence.

2. Work Completed
Task	Owner	Status	Evidence
Implemented and validated the 8 DQ rules	Team 14	Done	notebooks/04_data_quality_checks.ipynb
Implemented first-failure routing	Team 14	Done	DQ evaluation and routing output
Created Trusted Silver output	Team 14	Done	silver_trusted_requests
Created Quarantine output	Team 14	Done	quarantine_requests
Retained original quarantine payload and lineage	Team 14	Done	Quarantine evidence
Validated Candidate = Trusted + Quarantine reconciliation	Team 14	Done	week06_count_reconciliation.png
Validated Candidate membership in physical outputs	Team 14	Done	week06_membership_reconciliation.png
Validated Trusted business-key uniqueness	Team 14	Done	week06_trusted_key_validation.png
Selected a quarantined record for rework	Team 14	Done	CFX-2025-000000292
Identified the P14-DQ-06 failure	Team 14	Done	Quarantine evidence
Corrected the invalid longitude value	Team 14	Done	Replay evidence
Replayed the corrected record through all 8 DQ rules	Team 14	Done	week06_replay_all_dq_pass.png
Inserted the successfully replayed record into Trusted	Team 14	Done	silver_trusted_requests
Closed the original quarantine record	Team 14	Done	week06_replay_quarantine_closed.png
Created permanent replay closure evidence	Team 14	Done	replay_closure_evidence
Validated final reconciliation after replay	Team 14	Done	Final validation query
3. Key Decisions
Used cityfix.cityfix as the catalog and schema for the CityFix Week 06 tables.
Followed the approved order of the eight Data Quality rules and retained first-failure routing information.
Preserved the original quarantined record and original payload instead of overwriting it.
Selected CFX-2025-000000292 for the replay demonstration.
The record originally failed P14-DQ-06 because its longitude was outside the valid ZIP/service-zone boundary.
Used the bronze_zip_geography reference data to identify the valid longitude boundary.
Corrected the longitude from 78.638941 to 78.6385.
Replayed the corrected record through the DQ validation process before inserting it into Trusted.
Confirmed that the replayed record passed all eight DQ rules.
Changed the original quarantine record to CLOSED while retaining its original payload.
Created separate replay_closure_evidence so that the correction and replay history remains traceable.
4. Blockers / Risks
Blocker	Impact	Help Needed
DQ failure columns were not present in silver_candidate_requests	The initial DQ scorecard query resulted in a column-resolution error	Used the DQ flags retained in quarantine_requests for the scorecard
Temporary replay views depend on the active notebook session	Replay evidence could be difficult to reproduce later	Created permanent replay_closure_evidence table
A record can fail more than one DQ rule	Individual rule failure counts cannot be added to calculate total quarantined records	Used the physical quarantine count for reconciliation
Replay required preserving the original quarantine evidence	Overwriting the original record could result in loss of lineage	Original payload was retained and closure evidence was stored separately
5. Evidence Added to GitHub
notebooks/04_data_quality_checks.ipynb
docs/data_quality_summary.md
weekly_logs/week06_log.md
screenshots/week06_dq_rule_scorecard.png
screenshots/week06_count_reconciliation.png
screenshots/week06_membership_reconciliation.png
screenshots/week06_trusted_key_validation.png
screenshots/week06_quarantine_evidence.png
screenshots/week06_replay_all_dq_pass.png
screenshots/week06_replay_quarantine_closed.png
screenshots/week06_replay_closure_evidence.png
6. AI Transparency Note
Question	Response
Where AI helped	AI was used to assist with SQL query preparation, DQ validation queries, troubleshooting Databricks errors, and organizing the Week 06 evidence and documentation.
What we changed after AI suggestion	After the initial scorecard query failed because dq01_fail through dq08_fail were not available in silver_candidate_requests, the query was changed to use the DQ failure flags stored in quarantine_requests.
What we verified manually	We manually verified the Databricks table schemas, DQ results, quarantine records, reference ZIP geography, corrected longitude, replay result, Trusted route, quarantine closure, and final reconciliation counts.
What we can explain without AI	We can explain the eight DQ rules, first-failure routing, Candidate/Trusted/Quarantine flow, quarantine evidence retention, reconciliation checks, business-key validation, upstream correction, replay through DQ validation, and replay closure process.
7. Next Week Preparation
Review and finalize all Week 06 notebooks, documentation, screenshots, and weekly logs.
Commit the completed Week 06 artifacts to GitHub.
Verify that all validation screenshots are clear and contain the required results.
Review the DQ, Quarantine, Trusted Silver, and Replay workflow before the mentor review.
Prepare to explain the eight DQ rules and the end-to-end replay process without relying on AI.
Continue with the next project dependency after completing the Week 06 validation and evidence requirements.
