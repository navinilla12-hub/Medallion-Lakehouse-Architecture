# 🏗️ Medallion Lakehouse Architecture (PySpark + Delta Lake)

## 📌 Project Overview
This project implements a **Medallion Lakehouse Architecture** using **PySpark** and **Delta Lake** in Google Colab. It simulates real-world data engineering pipelines used in modern cloud data platforms.

The pipeline follows a structured **Bronze → Silver → Gold** architecture with support for:
- Schema evolution
- Incremental data processing (MERGE/UPSERT)
- Surrogate key generation
- Time travel (Delta Lake versioning)

---

## ⚙️ Tech Stack
- Apache Spark (PySpark)
- Delta Lake
- Google Colab
- Python
- Pandas (for optional validation)

---

## 📊 Dataset
Public Uber / Geospatial trip dataset (GitHub-hosted CSV)

---

## 🏛️ Architecture
Raw Data

↓

Bronze Layer (Raw ingestion)

↓

Silver Layer (Cleaned + deduplicated + surrogate key)

↓

Gold Layer (Aggregated analytics)


---

## 🔑 Key Features

### 🥉 Bronze Layer
- Raw ingestion with no transformation
- Stored in Delta format

### 🥈 Silver Layer
- Data cleaning (null handling, filtering)
- Deduplication using surrogate key
- Schema enrichment

### 🥇 Gold Layer
- Aggregated business metrics
- Time-based analytics

### ⚡ Advanced Features
- Surrogate key generation for uniqueness
- Delta Lake MERGE (incremental updates)
- Schema evolution (mergeSchema)
- Time travel queries (versioned data)

---

## 🔄 Example Transformations

- Trip data cleaned and standardized
- Duplicate records removed using surrogate key
- Aggregations created for analytical reporting

---

## ⏳ Time Travel Feature
Delta Lake enables querying previous versions of data:

```python
df = spark.read.format("delta") \
    .option("versionAsOf", 0) \
    .load("path")
