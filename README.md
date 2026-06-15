# E-Commerce Analytics Platform on Azure

## Project Overview
End-to-end data engineering pipeline built on Azure for an e-commerce analytics use case. Implements Medallion Architecture (Bronze/Silver/Gold) with automated orchestration, monitoring, and CI/CD.

## Architecture
Raw Data → Bronze (ADLS Gen2) → Silver (Databricks/Delta) → Gold (Aggregated) → Power BI

## Tech Stack
| Service | Purpose |
|---|---|
| Azure Data Lake Storage Gen2 | 3-layer data lake storage |
| Azure Data Factory | Data ingestion + orchestration |
| Azure Databricks | PySpark transformations |
| Delta Lake | ACID transactions, time travel |
| Power BI | Business dashboards |
| GitHub Actions | CI/CD deployment |
| Azure Monitor | Pipeline alerting |

## Pipeline Phases
- Phase 1 — Bronze: Raw CSV ingestion via ADF
- Phase 2 — Silver: PySpark cleaning via Databricks
- Phase 3 — Gold: Business aggregations via Databricks
- Phase 4 — Orchestration: ADF daily trigger at 6 AM
- Phase 5 — Monitoring: Azure Monitor alerts
- Phase 6 — CI/CD: GitHub Actions deployment

## Power BI Dashboard KPIs
- Total Revenue: 32.23M
- Total Orders: 1.30K
- Total Customer Spending: 204.7K

## Project Structure
azure-ecommerce-pipeline/
├── .github/workflows/deploy-adf.yml
├── ingestion/generate_data.py
├── sample_data/
├── pipeline/
├── dataset/
├── linkedService/
└── README.md

## Author
Anand — Senior Data Engineer
GitHub: https://github.com/Anand9891
