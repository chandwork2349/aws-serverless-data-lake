# 🚀 AWS Serverless Data Lake

## 📌 Overview
Built an end-to-end serverless data pipeline using AWS services to process and analyze data.

---

## 🧱 Architecture
![Architecture](architecture/architecture.png)

---

## ⚙️ Tech Stack
- AWS S3
- AWS Glue (ETL)
- AWS Athena
- Python (PySpark)

---

## 🔄 Pipeline Flow

1. Raw CSV data uploaded to S3
2. AWS Glue crawler creates metadata
3. Glue ETL job:
   - Cleans data
   - Removes duplicates
   - Converts to Parquet
   - Partitions data (year, month)
4. Data stored in curated layer
5. Athena queries for analytics

---

## 📊 Sample Queries

```sql
SELECT year, month, SUM(amount)
FROM curated_sales
GROUP BY year, month;
``
