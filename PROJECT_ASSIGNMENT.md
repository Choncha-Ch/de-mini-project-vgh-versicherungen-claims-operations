# Project Assignment

## Title
VGH Versicherungen Claims Operations Mini Project

## Business scenario
You are working as a junior data engineer at **VGH Versicherungen**.

The claims operations team receives new claim intake files during the day.
Some files contain new claims.
Some files contain updates or corrections to existing claims.

The team needs a small Databricks pipeline that:
1. lands raw files in a Unity Catalog volume
2. ingests the raw data into a bronze Delta table
3. cleans and standardizes the data into a silver Delta table
4. applies corrections with MERGE
5. produces multiple gold reporting tables for operations

## Main learning goals
By the end of the project, you should be able to:
- build an end-to-end Bronze–Silver–Gold Delta pipeline
- explain the purpose of each layer
- use Auto Loader or the fallback ingestion pattern
- clean and validate data in silver
- use MERGE for change handling
- create multiple gold business reports
- explain how medallion architecture supports debugging and reliability

## Your tasks

### Stage A — Understand the project
1. Read the repo structure and the student guide.
2. Review `config/project_config.yml`.
3. Identify the landing volume, checkpoint volume, bronze table, silver table, and gold tables.
4. Inspect the sample CSV files and identify the important business fields.

### Stage B — Bronze ingestion
5. Create or confirm the catalog, schema, and volumes.
6. Copy `claims_batch_1.csv` into the landing volume.
7. Ingest the file into the bronze Delta table using Auto Loader.
8. Inspect the bronze schema and sample rows.
9. Explain why bronze should not directly become reporting data.

### Stage C — Silver preparation
10. Read from the bronze table.
11. Select the useful columns.
12. Cast the correct data types.
13. Standardize `claim_status`, `claim_type`, `reported_channel`, `region`, and `handler_team`.
14. Filter invalid rows such as null `claim_id` or non-positive `claim_amount`.
15. Deduplicate by `claim_id` using the latest `last_updated_ts`.
16. Derive:
    - `claim_day`
    - `is_high_value_claim`
    - `is_open_claim`
17. Save the cleaned dataset as the silver Delta table.

### Stage D — Delta change handling
18. Copy `claim_corrections.csv` into the repo or read it directly from the repo sample folder.
19. Read the correction file.
20. Apply a MERGE into the silver table.
21. Inspect the silver table after the MERGE.
22. Inspect Delta history.
23. Optionally use time travel to inspect an earlier version.

### Stage E — Gold reporting outputs
24. Create `gold_daily_claims_summary`.
25. Create `gold_status_summary`.
26. Create `gold_claim_type_summary`.
27. Create `gold_region_summary`.
28. Create `gold_channel_summary`.
29. Create `gold_high_value_claims`.
30. Create `gold_open_claims_summary`.
31. Create `gold_handler_team_summary`.

### Stage F — Data quality checks
32. Check for duplicate `claim_id` values in silver.
33. Check for nulls in critical fields.
34. Check for invalid claim amounts.
35. Compare bronze row count with silver row count.
36. Check for unexpected status values.
37. Check for unexpected reported channel values.

### Stage G — Reflection
38. Explain the role of bronze in this project.
39. Explain why quality checks belong mainly in silver.
40. Explain why gold should be business-focused.
41. Identify which gold report is most useful for claims operations and why.
42. Explain how medallion architecture helps debugging.

## Required gold reports
You must create all of these:
- Daily Claims Summary
- Claim Status Summary
- Claim Type Summary
- Regional Claims Summary
- Reported Channel Summary
- High-Value Claims Report
- Open Claims Summary
- Handler Team Summary

## Deliverables
- completed notebooks
- created Delta tables
- all required gold reports
- short written reflection answers
- screenshots or previews of the final gold outputs
