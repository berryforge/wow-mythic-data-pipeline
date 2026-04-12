# WoW Mythic+ Data Pipeline

<img src="https://github.com/berryForge/wow-mythic-data-pipeline/blob/main/mplus_datapipeline_logo.PNG" style="width:50%;" alt="Mythic+ Data Pipeline">

## Overview

This project is a **personal data engineering portfolio project** focused on building a complete data pipeline using real-world data.

The pipeline ingests **World of Warcraft Mythic+ dungeon data** from the Raider.IO API and processes it through a **Medallion Architecture (Bronze → Silver → Gold)** using PySpark in Databricks.

The goal of this project is to demonstrate the **end-to-end lifecycle of a modern data pipeline**, from raw ingestion to analytics-ready datasets.

---

## Project Goals

* Ingest data from an external API
* Work with deeply nested JSON data
* Transform and clean raw data using PySpark
* Design structured datasets for analytics
* Implement Medallion Architecture
* Organize and version control a data project using GitHub

---

## Data Source

Data is pulled from the **Raider.IO API**, which provides detailed statistics about Mythic+ dungeon runs.

This API returns **deeply nested JSON**, making it ideal for practicing:

* JSON parsing
* Data normalization
* Flattening nested structures

The pipeline currently collects data for:

* Drayfu
* Drayth
* Draythos

---

## Architecture

This project follows the **Medallion Architecture pattern**, commonly used in modern data platforms.

### Bronze Layer — Raw Data

The Bronze layer stores **raw API responses** with no transformations.

**Purpose:**

* Preserve original source data
* Enable reprocessing if logic changes
* Maintain a single source of truth

**What it does:**

* Reads JSON files from Databricks volume storage
* Writes raw data into a Delta table

---

### Silver Layer — Cleaned & Structured

The Silver layer transforms raw JSON into structured datasets.

**Transformations include:**

* Flattening nested JSON structures
* Exploding arrays (players, encounters)
* Cleaning character names
* Standardizing role values (Tank, Healer, DPS)
* Converting timestamps to proper formats
* Normalizing season names

**Output tables:**

* `dungeons`
* `players`
* `boss_encounters`

---

### Gold Layer — Analytics Ready

The Gold layer organizes data into **fact and dimension tables** for analysis.

**Fact Tables:**

* `fact_mythic_runs` → One row per player per run
* `fact_boss_encounters` → One row per boss encounter

**Dimension Tables:**

* `dim_characters`
* `dim_dungeons`
* `dim_bosses`

These tables are designed to support performance analysis and reporting.

---

## Repository Structure

```
wow-mythic-data-pipeline/
│
├── ingestion/
│   └── raiderio_api_ingest.py
│
├── bronze/
│   └── bronze_layer_ingestion.py
│
├── silver/
│   └── silver_layer_transformation.py
│
├── gold/
│   └── gold_layer_modeling.py
│
├── data/
│   └── sample_json/
│
├── docs/
│   └── (screenshots, diagrams)
│
├── README.md
└── .gitignore
```

---

## Example Data Flow

1. **Ingestion**

   * Pull Mythic+ run data from Raider.IO API
   * Store raw JSON files

2. **Bronze**

   * Load JSON into Delta table with no changes

3. **Silver**

   * Flatten nested data
   * Extract players, dungeons, encounters
   * Clean and standardize fields

4. **Gold**

   * Join datasets
   * Create fact and dimension tables
   * Prepare for analytics and reporting

---

## Current Status

This project currently includes a **working first-pass Medallion pipeline**:

### Completed

* API ingestion from Raider.IO
* Bronze layer raw data storage
* Silver layer transformations (players, dungeons, encounters)
* Gold layer fact and dimension modeling

### In Progress

* Refactoring notebooks into cleaner production-style scripts
* Improving documentation and repo organization
* Adding data quality checks
* Building analytics use cases

---

## Next Steps

Planned improvements:

* Add data quality validation checks
* Build character performance analytics
* Create a “best runs” dataset per character
* Add Power BI or Tableau dashboards
* Improve pipeline automation

---

## Technologies Used

* Databricks
* PySpark
* Delta Lake
* Python
* Git / GitHub

---

## Author

Amanda Berry
Systems Analyst → Data Engineering
