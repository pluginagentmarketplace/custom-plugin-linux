---
name: data
description: Data Engineering skill - ETL, pipelines, warehousing, streaming
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [pipeline, etl, warehouse, streaming, quality] }
    scale: { type: string, enum: [small, medium, large] }
  required: [task]

output_schema:
  type: object
  properties:
    architecture: { type: string }
    code: { type: string }
    tools: { type: array }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 60000
---

# Data Engineering Skill

## PURPOSE
Data pipelines, ETL processes, and data platform design.

## CORE COMPETENCIES
```
Data Processing:
├── Batch (Spark, Pandas)
├── Streaming (Kafka, Flink)
├── ETL/ELT patterns
└── Data quality

Storage:
├── Data lakes (S3, GCS)
├── Warehouses (Snowflake, BigQuery)
├── Databases (PostgreSQL, DuckDB)
└── File formats (Parquet, Delta)

Orchestration:
├── Airflow
├── Dagster
├── Prefect
└── dbt
```

## CODE PATTERNS

### Spark ETL
```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import col, when

spark = SparkSession.builder.appName("ETL").getOrCreate()

# Extract
df = spark.read.parquet("s3://data/raw/")

# Transform
transformed = df.filter(col("status") == "active") \
    .withColumn("category", when(col("value") > 100, "high").otherwise("low")) \
    .dropDuplicates(["id"])

# Load
transformed.write.mode("overwrite").partitionBy("date").parquet("s3://data/processed/")
```

### Airflow DAG
```python
from airflow import DAG
from airflow.operators.python import PythonOperator
from datetime import datetime, timedelta

default_args = {
    "retries": 3,
    "retry_delay": timedelta(minutes=5),
}

with DAG("etl_pipeline", default_args=default_args, schedule_interval="@daily") as dag:
    extract = PythonOperator(task_id="extract", python_callable=extract_data)
    transform = PythonOperator(task_id="transform", python_callable=transform_data)
    load = PythonOperator(task_id="load", python_callable=load_data)

    extract >> transform >> load
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| OOM in Spark | Partition skew | Repartition, salting |
| Slow queries | No partition pruning | Add partition filters |
| Data quality | Missing validation | Add checks, dbt tests |
