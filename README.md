# 🚀 AWS Serverless Data Lake (Production-Grade Pipeline)

Designed and implemented a scalable serverless data engineering pipeline on AWS to ingest, transform, and analyze transactional data.

✅ End-to-end ETL using AWS Glue (PySpark)  
✅ Config-driven architecture using JSON  
✅ Partitioned data lake (year, month)  
✅ Optimized analytics using Parquet + Athena  

---

## 💡 Problem Statement

Organizations need scalable and cost-efficient solutions to process large volumes of transactional data for analytics and reporting.

This project demonstrates a serverless data pipeline for transforming raw data into optimized, query-ready datasets.

---

## 🧱 Architecture

architecture/architecture.png

---

## ⚙️ Tech Stack

- Amazon S3 – Data Lake
- AWS Glue – ETL processing
- Glue Crawler – Metadata catalog
- Amazon Athena – Query engine
- Python (PySpark)

---

## 🔄 Pipeline Flow

1. Raw CSV data uploaded to S3 (Raw Layer)
2. Glue Crawler generates metadata
3. Glue ETL pipeline:
   - Cleans data
   - Removes duplicates
   - ✅ Performs data quality validation
   - Casts datatypes
   - Reads configuration dynamically
   - Adds partition columns (year, month)
4. Data stored in curated layer (Parquet format)
5. Athena queries optimized dataset

---

## ⚙️ Data Engineering Features

- Config-driven pipeline using JSON stored in S3
- Data quality validation integrated
- Logging for observability
- Partitioned data lake design

---

## ⚙️ Design Decisions

- Used S3 as scalable and cost-efficient data lake
- Used Glue for serverless ETL
- Partitioned data (year/month) to improve performance
- Used Parquet format for efficient analytics

---

## 🧠 Why This Design?

- Serverless approach reduces infrastructure overhead
- Partitioning minimizes Athena query cost
- Config-driven design improves flexibility
- Data quality ensures reliable analytics

---

## 📈 Performance Optimization

- Reduced data scan using Parquet
- Improved query performance via partition pruning
- Optimized ETL pipeline for large-scale data

---

## ⚡ Performance Note

Partition pruning ensures Athena scans only required partitions, reducing execution time and cost.

---

## ✅ Data Quality

- Duplicate removal
- Data type validation
- Threshold-based validation
- Empty dataset detection

---

## 🔍 Data Lineage

Raw Data → S3 → Glue ETL → Curated Layer → Athena

---

## 📦 Scalability

- S3 supports large-scale storage
- Glue uses distributed Spark processing
- Athena enables serverless analytics

---

## ⚠️ Failure Handling

- Detects empty or low-volume data
- Logs ETL failures
- Handles schema mismatch issues
- Validates pipeline inputs

---

## 🚨 Failure Scenarios Considered

- Empty dataset
- Incorrect S3 paths
- Schema mismatch between Parquet and Athena
- IAM permission issues

---

## 📊 Use Cases

- Sales analytics dashboards
- Business reporting
- Data warehousing pipelines
- Financial analytics

---

## 📊 Sample Queries

```sql
SELECT year, month, SUM(amount)
FROM curated_sales
GROUP BY year, month;
``
