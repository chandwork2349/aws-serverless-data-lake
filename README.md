# 🚀 AWS Serverless Data Lake (Production-Grade Pipeline)

Designed and implemented a scalable **serverless data engineering pipeline** on AWS to ingest, transform, and analyze transactional data efficiently.

✅ End-to-end ETL pipeline using AWS Glue (PySpark)  
✅ Config-driven architecture for flexibility and scalability  
✅ Partitioned data lake design (year, month)  
✅ Optimized query performance using Parquet + Athena  

---

## 💡 Problem Statement

Organizations need scalable and cost-efficient solutions to process large volumes of transactional data for analytics and reporting.

This project demonstrates how to build a **serverless data pipeline** that transforms raw data into structured, query-ready datasets.

---

## 🧱 Architecture

architecture/architecture.png

---

## ⚙️ Tech Stack

- **Amazon S3** – Data Lake storage
- **AWS Glue** – ETL processing (PySpark)
- **AWS Glue Crawler** – Metadata cataloging
- **Amazon Athena** – Query engine
- **Python (PySpark)** – Data transformation

---

## 🔄 Pipeline Flow

1. Raw CSV data uploaded to **S3 (Raw Layer)**
2. Glue Crawler extracts metadata and creates tables
3. Glue ETL Pipeline:
   - Cleans data (removes duplicates)
   - Validates dataset
   - Casts data types
   - Adds partition columns (year, month)
4. Processed data stored in **S3 (Curated Layer)** in Parquet format
5. Athena queries optimized dataset for analytics

---

## ⚙️ Data Engineering Features

- Config-driven pipeline using JSON configuration
- Data quality validation integrated
- Logging for monitoring and debugging
- Partitioned data lake design

---

## ⚙️ Design Decisions

- Used **S3 as a data lake** for scalability and cost efficiency
- Used **AWS Glue (serverless ETL)** to avoid infrastructure management
- Implemented **partitioning (year, month)** to optimize queries
- Used **Parquet format** for faster analytics and reduced data scan

---

## 📈 Performance Optimization

- Reduced data scan using Parquet format
- Improved query performance using partition pruning
- Enabled efficient analytics on large datasets

---

## ✅ Data Quality

- Removed duplicate records
- Enforced correct data types (amount, quantity)
- Validated dataset before writing to curated layer
- Added threshold check for minimum data volume

---

## 🔍 Data Lineage

Raw Data → S3 → Glue ETL → S3 Curated → Athena

Ensures full traceability from ingestion to analytics layer.

---

## 📦 Scalability

- S3 scales for large datasets
- Glue uses distributed Spark processing
- Athena enables serverless querying without infrastructure

---

## ⚠️ Failure Handling

- Logs errors during ETL execution
- Fails pipeline for invalid or empty datasets
- Detects low data volume scenarios

---

## 📊 Use Case

This pipeline can be used for:

- Sales analytics dashboards
- Business intelligence reporting
- Data warehousing pipelines
- Financial transaction analysis

---

## 📊 Sample Queries

```sql
-- Monthly sales aggregation
SELECT year, month, SUM(amount) AS total_sales
FROM curated_sales
GROUP BY year, month
ORDER BY year, month;

-- Region-wise sales
SELECT region, SUM(amount) AS revenue
FROM curated_sales
GROUP BY region;

-- Top products
SELECT product, SUM(amount) AS revenue
FROM curated_sales
GROUP BY product
ORDER BY revenue DESC;
