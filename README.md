# WoW Mythic+ Data Pipeline

<img src="https://github.com/berryForge/wow-mythic-data-pipeline/blob/main/mplus_datapipeline_logo.PNG" style="width:50%;" alt="Mythic+ Data Pipeline">

This project is a **personal data engineering learning project** focused on building a complete data pipeline from raw ingestion to analytics-ready datasets.

The goal of this project is to learn and practice the **full lifecycle of a modern data pipeline**, including:

- Ingesting data from an external API
- Working with nested JSON data
- Cleaning and transforming raw data
- Structuring datasets for analytics
- Organizing data using **Medallion Architecture (Bronze → Silver → Gold)**
- Using Git to version control data engineering work

The topic of **World of Warcraft Mythic+ dungeon data** was chosen simply to make the learning process more engaging while working with real-world style data.

This repository will continue to evolve as I experiment with transformations, improve the data model, and expand the pipeline.

---

# Project Status

🚧 **Work In Progress**

This project is actively being developed while I learn more about building scalable data pipelines.

Progress will be tracked below as features and stages of the pipeline are completed.

---

# Data Source

Data is pulled from the **Raider.IO API**, which provides detailed statistics about Mythic+ dungeon runs.

The API returns **deeply nested JSON data**, which makes it ideal for practicing:

- JSON parsing
- Data normalization
- Flattening nested structures
- Building structured datasets from raw API responses

The pipeline currently collects runs for the following characters:

- Drayfu  
- Drayth  
- Draythos  

---

# Architecture

This project follows the **Medallion Architecture pattern**, commonly used in modern data platforms.

Data moves through multiple layers where it becomes progressively cleaner and more structured.

---

## Bronze Layer — Raw Data

The Bronze layer stores **raw API response data** with minimal modification.

Purpose:

- Preserve the original source data
- Allow reprocessing if transformations change
- Capture ingestion data exactly as received from the API

Example data includes:

- Dungeon run metadata
- Player roster information
- Keystone level
- Dungeon affixes
- Completion timestamps

### Progress

- [x] Raider.IO API ingestion script
- [x] JSON run data collection
- [x] Bronze data ingestion into Databricks

---

## Silver Layer — Cleaned & Structured

The Silver layer focuses on **cleaning and transforming raw JSON data into structured datasets**.

Transformations include:

- Flattening nested JSON structures
- Extracting player information
- Separating dungeon run metadata
- Cleaning inconsistent values
- Preparing normalized datasets

### Progress

- [x] Initial Silver transformation notebook
- [ ] Player dataset transformation
- [ ] Dungeon run dataset
- [ ] Additional data cleaning

---

## Gold Layer — Analytics

The Gold layer will contain **analytics-ready datasets designed for reporting and insights**.

These tables will be optimized for answering questions about Mythic+ performance.

Planned datasets include:

- Player performance metrics
- Dungeon completion statistics
- Seasonal performance comparisons
- Character progression tracking

### Progress

- [ ] Gold transformation layer
- [ ] Aggregated player performance table
- [ ] Dungeon performance analysis
- [ ] Visualization-ready datasets

---

# Repository Structure

```
wow-mythic-data-pipeline
│
├── ingestion/
│   └── Python scripts used to pull data from the Raider.IO API
│
├── data/
│   └── Raw JSON files retrieved from the API
│
├── bronze/
│   └── Initial ingestion and raw storage of data
│
├── silver/
│   └── Data cleaning and transformation notebooks
│
├── gold/
│   └── (planned) Analytics-ready datasets and aggregations
│
├── mplus_datapipeline_logo.PNG
│
├── .gitignore
│
└── README.md
```

---

# Learning Goals

This project exists primarily to **learn how real-world data pipelines work**.

Key areas being explored:

- Working with API-based data sources
- Processing nested JSON datasets
- Data transformation using PySpark
- Medallion architecture design
- Organizing projects using Git
- Structuring datasets for analytics

---

# Author

Amanda Berry  
Systems Analyst learning Data Engineering

 Potential Power BI or Tableau dashboards

Author

Amanda Berry
Systems Analyst learning Data Engineering
