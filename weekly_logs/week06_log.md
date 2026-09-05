Week 06 Log — Data Quality, Quarantine & Replay

Week: 6
Date range: 31 August 2026 – 5 September 2026
Team: Team 14
Project: CityFix: Civic Service Analytics

1. Sprint Goal

Implement and validate the Week 06 Data Quality pipeline for CityFix by evaluating all eight approved DQ rules, routing failed records to Quarantine, and passing valid records to Trusted Silver.

Complete one end-to-end rework and replay of a quarantined record through correction, Candidate/DQ validation, Trusted insertion, and closure evidence.

2. Work Completed
Task	Owner	Status	Evidence
Implemented and validated the 8 DQ rules	Team 14	Done	04_data_quality_checks.ipynb, DQ scorecard
Implemented first-failure routing	Team 14	Done	DQ evaluation and Quarantine output
Created Trusted Silver output	Team 14	Done	silver_trusted_requests
Created Quarantine output with original evidence	Team 14	Done	quarantine_requests
Validated Candidate → Trusted + Quarantine reconciliation	Team 14	Done	week06_count_reconciliation.png
Validated Candidate membership in physical outputs	Team 14	Done	week06_membership_reconciliation.png
Validated Trusted business-key uniqueness	Team 14	Done	week06_trusted_key_validation.png
Selected quarantined record for rework	Team 14	Done	CFX-2025-000000292
Corrected P14-DQ-06 longitude issue	Team 14	Done	week06_replay_closure_evidence.png
Replayed corrected record through DQ validation	Team 14	Done	week06_replay_all_dq_pass.png
Closed original quarantine record	Team 14	Done	week06_replay_quarantine_closed.png
Created replay closure evidence	Team 14	Done	replay_closure_evidence
3. Key Decisions
Used cityfix.cityfix as the project catalog/schema for Week 06 outputs.
Preserved the original quarantined record and its original payload instead of overwriting it.
Corrected the quarantined record upstream and replayed it through the DQ validation flow rather than directly inserting a corrected record into Trusted.
Used the ZIP geography reference to correct the longitude for CFX-2025-000000292 from 78.638941 to the valid boundary value 78.6385.
Kept the original quarantine record with rework_status = CLOSED and created separate replay closure evidence.
4. Blockers / Risks
Blocker	Impact	Help Needed
DQ flags were not present in silver_candidate_requests	Initial DQ scorecard query could not resolve dq01_fail–dq08_fail	Used the DQ flags retained in quarantine_requests for the scorecard
Temporary replay views are session-dependent	Replay evidence could be difficult to reproduce in a new session	Permanent replay_closure_evidence table was created
Multiple DQ rules can fail for the same record	Rule failure totals cannot be directly summed to calculate quarantine rows	Used physical quarantine count for reconciliation
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
Where AI helped	AI was used to help structure SQL validation queries, identify DQ evidence requirements, and troubleshoot Databricks column-resolution errors.
What we changed after AI suggestion	The team adjusted the DQ scorecard query after identifying that silver_candidate_requests did not contain the DQ failure columns. The scorecard was instead generated using the retained DQ flags in quarantine_requests.
What we verified manually	We manually verified the table schemas, DQ outputs, reconciliation counts, quarantine evidence, corrected longitude, replay result, Trusted route, and quarantine closure status in Databricks.
What we can explain without AI	We can explain the eight DQ checks, first-failure routing, Trusted/Quarantine separation, reconciliation logic, quarantine evidence retention, correction process, replay through DQ validation, and closure evidence.
7. Next Week Preparation
Review the completed Week 06 DQ, Quarantine, Trusted Silver, and Replay evidence.
Ensure all notebooks, documentation, screenshots, and weekly logs are committed to GitHub.
Review the validation results and prepare for the next project dependency.
Be prepared to explain the DQ rules, reconciliation, quarantine process, and replay workflow during the mentor review.
