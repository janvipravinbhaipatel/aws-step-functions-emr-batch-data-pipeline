# AWS Step Functions EMR Batch Data Pipeline

## Project Overview

This project demonstrates an event-driven batch data processing pipeline built on AWS. The pipeline automatically processes stock market CSV files uploaded to Amazon S3 using Apache Spark on Amazon EMR. AWS Step Functions orchestrates the workflow, while AWS Lambda triggers execution, AWS Glue catalogs the processed data, Amazon Athena enables SQL querying, and Amazon SNS sends a completion notification.

---

## Architecture

```
Amazon S3
      │
      ▼
S3 Event Notification
      │
      ▼
AWS Lambda
      │
      ▼
AWS Step Functions
      │
      ▼
Amazon EMR (Apache Spark)
      │
      ▼
Processed Parquet Data (Amazon S3)
      │
      ▼
AWS Glue Data Catalog
      │
      ▼
Amazon Athena
      │
      ▼
Amazon SNS Notification
```

---

## AWS Services Used

- Amazon S3
- AWS Lambda
- AWS Step Functions
- Amazon EMR
- Apache Spark
- AWS Glue Data Catalog
- Amazon Athena
- Amazon SNS
- AWS Lake Formation

---

## Workflow

1. Upload a CSV file to Amazon S3.
2. S3 Event Notification invokes an AWS Lambda function.
3. Lambda starts an AWS Step Functions workflow.
4. Step Functions provisions an Amazon EMR cluster.
5. Apache Spark processes the stock data.
6. Processed data is stored in Parquet format in Amazon S3.
7. AWS Glue catalogs the output.
8. Amazon Athena queries the processed data.
9. Amazon SNS sends a completion notification.
10. The EMR cluster is terminated automatically to optimize cost.

---

## PySpark Logic

The Spark application:

- Reads stock market CSV files from Amazon S3.
- Filters records where trading volume is greater than 100,000.
- Selects the Trade_Date, Ticker, and Close columns.
- Writes the processed output to Amazon S3 in Parquet format.

---

## Sample Athena Query

```sql
SELECT *
FROM default.stock_summary
ORDER BY trade_date DESC
LIMIT 10;
```

---

## Skills Demonstrated

- Event-driven architecture
- ETL pipeline orchestration
- Apache Spark data processing
- AWS Step Functions
- Amazon EMR
- AWS Glue
- Amazon Athena
- Cloud automation
- Cost optimization

---

## Learning Outcome

This hands-on project strengthened my understanding of building automated batch processing pipelines on AWS using managed services for data ingestion, orchestration, processing, cataloging, analytics, and notification.
