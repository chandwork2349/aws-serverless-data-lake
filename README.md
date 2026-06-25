# 🚀 AWS Serverless Data Lake (Production-Grade Pipeline)

Designed and implemented a scalable serverless data engineering pipeline on AWS to ingest, process, and analyze transactional data efficiently.

✅ End-to-end ETL using AWS Glue (PySpark)  
✅ Config-driven architecture for flexibility  
✅ Partitioned data lake (year, month)  
✅ Optimized analytics using Parquet + Athena  

---

## 💡 Problem Statement

Organizations require scalable pipelines to process large transactional data efficiently for analytics and reporting.

This project demonstrates a cost-efficient serverless data pipeline for real-world analytics use cases.

---

## 🧱 Architecture

architecture/architecture.png

---

## ⚙️ Tech Stack

- Amazon S3 – Data Lake Storage  
- AWS Glue – ETL Processing  
- Glue Crawler – Metadata management  
- Amazon Athena – Query engine  
- Python (PySpark) – Data transformation  

---

## 🔄 Pipeline Flow

1. Raw CSV data uploaded to S3 (Raw Layer)
2. Glue Crawler creates metadata table
3. Glue ETL Pipeline:
   - Cleans data
   - Removes duplicates
   - Validates dataset
   - Casts datatypes
   - Adds partition columns (year, month)
4. Data stored in curated layer (Parquet format)
5. Athena queries optimized dataset

---

## ⚙️ Data Engineering Features

- Config-driven pipeline using JSON
- Data quality validation
- Logging for monitoring
- Partition-based optimization

---

## ⚙️ Design Decisions

- Used S3 as scalable data lake
- Used Glue for serverless ETL
- Implemented partitioning for query optimization
- Used Parquet for efficient storage

---

## 📈 Performance Optimization

- Reduced data scan using Parquet
- Improved query speed using partition pruning
- Optimized ETL for large datasets

---

## ✅ Data Quality

- Duplicate removal
- Data type validation
- Empty dataset checks
- Threshold-based validation

---

## 🔍 Data Lineage

Raw Data → S3 → Glue ETL → Curated Layer → Athena

---

## 📦 Scalability

- S3 handles large-scale storage
- Glue executes distributed processing
- Athena enables serverless querying

---

## ⚠️ Failure Handling

- Handles empty dataset scenarios
- Detects low-volume data
- Logs pipeline errors
- Handles schema mismatch issues

---

## 📊 Use Cases

- Sales analytics dashboards
- Business reporting
- Data warehousing pipelines
- Financial data analysis

---

## 📊 Sample Queries

```sql
SELECT year, month, SUM(amount)
FROM curated_sales
GROUP BY year, month;
