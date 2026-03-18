# 🚖 Transportation Data Pipeline — cabs

> An analytics engineering pipeline that transforms raw cab data into city-level business intelligence using Databricks Lakeflow Spark Declarative Pipelines.

---

## 📌 Overview

This project simulates a production-grade analytics engineering workflow for a fictional cab company. Daily transportation data is ingested from AWS S3, processed through a **Medallion architecture**, and surfaced as analysis-ready datasets powering city-level performance dashboards.

---

## 🏗️ Architecture

<img width="14204" height="4628" alt="architecture" src="https://github.com/user-attachments/assets/2685b576-2579-4572-97a1-5674454c5414" />


| Layer | Technology |
|-------|-----------|
| **Source** | Daily CSV trip exports |
| **Storage** | AWS S3 |
| **Processing** | Databricks (PySpark + Lakeflow) |
| **Modeling** | Medallion Architecture (Bronze → Silver → Gold) |
| **Consumption** | City-level dashboards |

---

## 🧱 Data Layers

### 🥉 Bronze — Raw Ingestion
- Ingests raw data directly from S3
- Preserves source files with no transformation
- Adds metadata columns: `ingestion_timestamp`, `source_file_name`
- Handles schema evolution automatically

### 🥈 Silver — Cleansed & Standardised
- Applies data cleaning and type standardisation
- Runs data quality checks
- Implements CDC-style processing for trip records
- Produces business-ready structured tables:
  - `trips`
  - `city`
  - `calendar`

### 🥇 Gold — Analytical Layer
- Central analytical table: **`fact_trips`** (trips joined with city + calendar dimensions)
- Pre-built city-specific views: Jaipur, Surat, Kochi, and more
- Designed to support region-level dashboards for operations managers

---

## ⚙️ Key Design Decisions

### Incremental vs Batch Ingestion

| Dataset | Strategy | Rationale |
|---------|----------|-----------|
| **Trips** | Incremental (Auto Loader) | Daily files (`trip_export_YYYY-MM-DD.csv`) — optimised for high-volume, append-only data |
| **City** | Batch | Small static dimension (~10 rows) — streaming complexity not justified |

> This hybrid approach balances performance with simplicity, avoiding unnecessary streaming overhead for low-change data.

---

## 🚀 Features

- ⚡ **Incremental ingestion** via Databricks Auto Loader
- 🏅 **Medallion architecture** (Bronze → Silver → Gold)
- 🔁 **CDC-style processing** for trip data updates
- ✅ **Data quality validation** at the Silver layer
- 📋 **Metadata tracking** (timestamps, source files)
- 🗺️ **Business-aligned semantic views** per city

---

## 💼 Business Value

- Converts raw operational exports into trusted, analysis-ready datasets
- Enables city-level performance monitoring at scale
- Simplifies dashboard consumption through predefined semantic views
- Mirrors real-world analytics engineering patterns used in retail and logistics

---

## 🧠 Skills Demonstrated

`Data Engineering` &nbsp; `Analytics Engineering` &nbsp; `PySpark` &nbsp; `Databricks Lakeflow` &nbsp; `Data Modelling` &nbsp; `Incremental Processing` &nbsp; `Medallion Architecture` &nbsp; `AWS S3` &nbsp `SQL`

---

## 📁 Project Structure

```
goodcabs-pipeline/
├── bronze/          # Raw ingestion notebooks & Auto Loader config
├── silver/          # Cleansing, DQ checks, CDC logic
├── gold/            # fact_trips + city-level views
├── architecture.png # System architecture diagram
└── README.md
```

---

*Built to simulate production analytics engineering workflows in the transportation domain.*
