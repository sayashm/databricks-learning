# Azure Databricks Learning

Notebooks and notes from learning **Azure Databricks** with Apache Spark, Delta Lake, and Unity Catalog. The main project is a **Formula 1 data pipeline** built with the medallion architecture (bronze, silver, gold) and summarised into standings views.

## What's inside

| Topic | What it covers |
|---|---|
| Notebooks | Markdown and magic commands (`%sql`, `%md`, `%run`, `%fs`), Databricks Utilities, debugging |
| Delta Lake | Transaction log, table history, and time travel |
| Unity Catalog | Catalogs, schemas, managed locations, and access to cloud storage |
| Formula 1 pipeline | Ingestion (bronze), cleaning (silver), dimensions and fact tables (gold), and analytics views |
| Incremental load | Same pipeline with control tables that track which batch to process next |

## Pipeline layout

Each pipeline folder is numbered in the order it runs:

| Folder | Purpose |
|---|---|
| `00-common` | Shared config (catalog, schema, landing path) and helper functions |
| `01-setup` | Creates catalog, schemas, and volumes |
| `02-bronze` | Ingests raw files: circuits, races, constructors, drivers, results, sprints |
| `03-silver` | Cleans and standardises the bronze data |
| `04-gold` | Builds dimension tables and the results fact table |
| `05-analytics` | Driver and constructor standings views |

## Requirements

- An Azure subscription with an Azure Databricks workspace
- Unity Catalog enabled
- Compute that can reach your storage
- The source files uploaded to your landing volume

## How to run

1. Import the notebooks into your workspace, or connect this repo as a Databricks Git folder.
2. Replace the storage paths (`abfss://...dfs.core.windows.net/...`) with your own storage account or volume. The setup notebooks contain these paths.
3. Run the notebooks in folder order, starting with `01-setup`.

## Notes

- No secrets are stored in this repo. Credentials should come from Databricks secret scopes or Unity Catalog credentials.
- Some notebooks were written while following an online course, so the structure may follow the course's outline.
