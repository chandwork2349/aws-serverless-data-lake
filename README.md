# 🚀 AWS Serverless Data Lake (Production-Grade Pipeline)

Designed and implemented a scalable serverless data engineering pipeline on AWS to ingest, transform, and analyze transactional data.

✅ End-to-end ETL using AWS Glue (PySpark)  
✅ Partitioned data lake architecture (year, month)  
✅ Optimized query performance using Parquet + Athena  
✅ Serverless and cost-efficient data processing  

---

## 🧱 Architecture

![Architecture](architecture/architecture.png)

---

## ⚙️ Tech Stack

- Amazon S3 (Data Lake)
- AWS Glue (ETL Processing)
- AWS Glue Crawler (Metadata)
- Amazon Athena (Query Engine)
- Python (PySpark)

---

## 🔄 Pipeline Flow

1. Raw CSV data uploaded to S3 (Raw Layer)
2. AWS Glue crawler scans and creates metadata table
3. Glue ETL job:
   - Cleans data (removes duplicates)
   - Validates dataset
   - Transforms data
   - Converts to Parquet format
   - Adds partition columns (year, month)
4. Processed data stored in S3 Curated Layer
5. Athena queries partitioned data for analytics

---

## ⚙️ Design Decisions

- Used **S3 as data lake** for scalability and cost efficiency
- Used **AWS Glue (serverless ETL)** to avoid cluster management
- Implemented **partitioning (year, month)** to improve query performance
- Used **Parquet format** for columnar storage optimization

---

## 📈 Performance Optimization

- Reduced data scan size using Parquet format
- Improved query speed with partition pruning
- Optimized ETL pipeline for large dataset processing

---

## ✅ Data Quality

- Removed duplicate records
- Enforced data type casting
- Validated dataset before processing

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
SELECT year, month, SUM(amount) AS total_sales
FROM curated_sales
GROUP BY year, month
ORDER BY year, month;
