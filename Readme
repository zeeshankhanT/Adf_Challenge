# Azure Data Ingestion Pipeline

A streamlined solution utilizing Azure Data Factory (ADF), Logic Apps, and Key Vault for secure, scalable, and maintainable data ingestion.

## Features
- Config-driven ingestion without code changes via JSON config files
- Structured ADLS Gen2 with raw container and logical segmentation
- Environment-aware design (Dev with LRS, Prod with GRS) with CI/CD pipelines
- Reliable scheduled ingestion with failure alerts and monitoring
- Supports daily zipped CSV downloads and REST API ingestion for users endpoint

## Architecture Overview
- Resource groups: `rg-lego-dev` (development) and `rg-lego-prod` (production)
- Core resources: ADLS Gen2, Azure Data Factory, Azure Key Vault, Logic Apps
- Managed identities for secure access and secrets handling

## Data Layout and Storage
- Raw container structured by domain and date partitioning:
  - `raw/rebrickable/lego/YYYY/MM/DD/`
  - `raw/rebrickable/users/YYYY/MM/DD/`
- Lifecycle policies for blob storage tiers (Hot, Cool, Archive)

## Security and Access
- Managed identity authentication for ADF
- RBAC roles assigned for secure data access
- Secrets stored and accessed via Azure Key Vault (API keys, user tokens)

## Pipelines
- `PL_Ingest_Rebrickable`: Master pipeline executing two child pipelines in parallel
  - `PL_Ingest_Downloads` (lego domain)
  - `PL_Ingest_API` (users domain)
- Resilient copy activities with retry policies and alerts on failure

## Scheduling and Monitoring
- Daily schedule trigger post data refresh window
- Logic Apps for failure notifications via email

## Continuous Integration & Deployment
- Git integration with feature branches and pull requests
- Automated CI/CD pipelines for Dev and Prod environments
- Parameterized deployments for environment-specific resources

## Adding New Data Sources
- Easily add new datasets to the config JSON without recoding pipelines

