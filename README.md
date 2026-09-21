# AWS Glue E-Commerce Data Pipeline

An end-to-end e-commerce data engineering pipeline built with AWS Glue, PySpark, Apache Spark, and Amazon S3.

## Project Overview

This project reads twelve raw e-commerce CSV datasets from Amazon S3, profiles and cleans the data, applies data type and business transformations, performs analytical joins and window functions, creates aggregated datasets, and writes the final outputs as Snappy-compressed Parquet files.

## Technologies

- AWS Glue
- PySpark
- Apache Spark
- Amazon S3
- Parquet
- Snappy compression
- Python

## Source Tables

- customers
- categories
- products
- departments
- employees
- suppliers
- orders
- order_details
- payments
- product_suppliers
- shippers
- shipments


## Pipeline Stages

1. Read and profile all CSV datasets.
2. Standardize column names and clean string values.
3. Validate nulls, duplicates, invalid emails, statuses, and prices.
4. Convert IDs, prices, dates, payments, and quantities to appropriate data types.
5. Create order totals and line-level sales metrics.
6. Build the `fact_sales` dataset.
7. Apply Spark window functions.
8. Perform analytical joins.
9. Create customer, product, category, and monthly aggregations.
10. Perform advanced analytics and date analysis.
11. Write final outputs as Snappy-compressed Parquet files.

## S3 Locations

Raw data:

```text
s3://mahmoud-sic-ecommerce-2026/raw/ecommerce/
