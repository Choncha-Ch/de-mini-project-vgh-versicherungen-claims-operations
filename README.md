# DE-mini-project-vgh-versicherungen-claims-operations

A showcase of  a junior data engineer role at **VGH Versicherungen**. 
The claims operations team receives claim intake files during the day. 
Some files contain new claims, and some contain updates or corrections to existing claims.

## Task
Your task is to build a small but realistic **Bronze–Silver–Gold Delta pipeline** in Databricks Free Edition.

## Main flow
- raw claim files land in a Unity Catalog volume
- Auto Loader ingests the files into a bronze Delta table
- silver cleans, validates, standardizes, and deduplicates the claims
- a correction file is applied with MERGE
- gold tables provide business-ready reporting outputs

## Project structure
- `PROJECT_ASSIGNMENT.md` — full assignment
- `config/project_config.yml` — project settings used by the notebooks
- `docs/expected_outputs.md` — required outputs and reports
- `sample_data/` — small sample CSV files
- `sql/` — helper SQL
- `notebooks/` — notebooks with TODO sections
- `.github/workflows/repo_check.yml` — simple repository check

## Suggested notebook order
1. `01_bronze_ingestion.py`
2. `02_silver_preparation.py`
3. `03_delta_merge.py`
4. `04_gold_reporting.py`
5. `05_quality_and_reflection.py`

## Main tables
- Bronze: `vgh_dev.claims.bronze_claims`
- Silver: `vgh_dev.claims.silver_claims`
- Gold:
  - `vgh_dev.claims.gold_daily_claims_summary`
  - `vgh_dev.claims.gold_status_summary`
  - `vgh_dev.claims.gold_claim_type_summary`
  - `vgh_dev.claims.gold_region_summary`
  - `vgh_dev.claims.gold_channel_summary`
  - `vgh_dev.claims.gold_high_value_claims`
  - `vgh_dev.claims.gold_open_claims_summary`
  - `vgh_dev.claims.gold_handler_team_summary`
