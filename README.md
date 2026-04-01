# Azure Data Engineering Portfolio

![Azure](https://img.shields.io/badge/Azure-Data%20Engineering-0078D4?style=flat&logo=microsoft-azure)
![Python](https://img.shields.io/badge/Python-3.9-3776AB?style=flat&logo=python)
![Apache Spark](https://img.shields.io/badge/Apache%20Spark-PySpark-E25A1C?style=flat&logo=apache-spark)
![Delta Lake](https://img.shields.io/badge/Delta%20Lake-Medallion%20Architecture-00ADD8?style=flat)

End-to-end Azure Data Engineering pipeline ingesting, transforming, 
and serving NYC Taxi data using Azure Data Factory, Databricks, 
and Delta Lake on ADLS Gen2.

---

## Architecture
```
NYC Taxi Data (Source)
        ↓
Azure Data Factory (Orchestration)
        ↓
ADLS Gen2 - raw/ (Bronze Layer)
        ↓
Databricks + PySpark (Transformation)
        ↓
ADLS Gen2 - processed/ (Silver Layer)
        ↓
Databricks + Delta Lake (Aggregation)
        ↓
ADLS Gen2 - curated/ (Gold Layer)
```

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| Azure Data Factory | Pipeline orchestration & scheduling |
| Azure Databricks | PySpark transformation & Delta Lake |
| ADLS Gen2 | Data Lake storage (Bronze/Silver/Gold) |
| Azure Key Vault | Secrets management |
| Delta Lake | ACID transactions & time travel |
| GitHub Actions | CI/CD pipeline |

---

## Project Structure
```
├── adf/                    # ADF pipeline definitions (auto-synced)
├── data/
│   ├── raw/                # Sample raw data
│   ├── processed/          # Sample processed data
│   └── curated/            # Sample curated data
├── notebooks/
│   ├── bronze/             # Ingestion notebooks
│   ├── silver/             # Transformation notebooks
│   └── gold/               # Aggregation notebooks
├── docs/                   # Architecture diagrams
└── README.md
```

---

## Pipeline Overview

### Bronze Layer — Raw Ingestion
- ADF copies NYC Taxi CSV from source to `raw/` container
- No transformation, raw data preserved

### Silver Layer — Cleaning & Transformation
- PySpark removes nulls, standardises data types
- Adds metadata columns (ingestion timestamp, source)
- Stored as Parquet in `processed/`

### Gold Layer — Aggregation
- Delta Lake tables for analytical queries
- Aggregated metrics: trips by zone, average fare, peak hours
- Stored in `curated/` ready for reporting

---

## Key Concepts Demonstrated

- Medallion Architecture (Bronze / Silver / Gold)
- Delta Lake ACID transactions & time travel
- ADF parameterised pipelines
- Secrets management via Azure Key Vault
- Git-based CI/CD with GitHub Actions

---

## Author
**Siu Cheung Lam**  
Azure Data Engineer  
[GitHub](https://github.com/chipsopenclaw-project)
