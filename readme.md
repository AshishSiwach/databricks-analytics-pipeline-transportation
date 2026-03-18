📘 3. FINAL GITHUB README (copy-paste ready)
🚖 Transportation Data Pipeline (Goodcabs)
📌 Overview

This project simulates an analytics engineering pipeline for a fictional cabs company. The system processes daily transportation data and transforms it into analysis-ready datasets using Databricks Lakeflow Declarative Pipelines.

🏗️ Architecture
![alt text](architecture.png)

Source: Daily trip export files (CSV)

Storage: AWS S3

Processing: Databricks (PySpark + Lakeflow)

Modeling: Medallion architecture

Consumption: City-level dashboards

⚙️ Key Design Decisions
🔹 Incremental vs Batch Ingestion

Trips dataset:

Daily files (e.g. trip_export_YYYY-MM-DD.csv)

Ingested using Databricks Auto Loader for incremental processing

City dataset:

Small, static dimension (~10 rows)

Ingested using batch processing

👉 This approach optimizes performance and avoids unnecessary streaming complexity.

🧱 Data Layers
🥉 Bronze

Raw ingestion from S3

Metadata columns:

ingestion timestamp

file name

Schema evolution handled

🥈 Silver

Data cleaning and standardization

Data quality checks

CDC-style processing for trips

Business-ready structured tables:

trips

city

calendar

🥇 Gold

Central analytical table:

fact_trips (joined with city + calendar)

City-specific views:

Jaipur, Surat, Kochi, etc.

👉 Designed to support region-level dashboards for managers

💼 Business Value

Converts raw operational data into trusted analytical datasets

Enables city-level performance monitoring

Simplifies dashboard usage through predefined semantic views

Mimics real-world analytics engineering workflows used in retail and logistics

🚀 Features

Incremental ingestion using Auto Loader

Medallion architecture (bronze, silver, gold)

PySpark transformations

Data quality validation

Metadata tracking

Business-aligned data modelling

🧠 Key Skills Demonstrated

Data Engineering

Analytics Engineering

PySpark

Databricks Lakeflow

Data Modelling

Incremental Data Processing