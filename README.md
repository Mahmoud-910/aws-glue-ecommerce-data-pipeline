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


Local Data Generator
        │
        ▼
CSV Files
        │
        ▼
S3 Raw Layer
raw/ecommerce/
        │
        ▼
AWS Glue + PySpark
        │
        ├── Profiling
        ├── Cleaning
        ├── Type Transformation
        ├── Business Logic
        ├── Joins
        └── Aggregations
        │
        ▼
S3 Processed Layer
processed/ecommerce/
        │
        ├── fact_sales
        ├── customer_sales
        ├── product_sales
        ├── category_sales
        └── monthly_sales


## Architecture

```mermaid
flowchart TD
    A[Local Python Data Generator] --> B[12 CSV Files]
    B --> C[Amazon S3 Raw Layer]

    C --> D[AWS Glue PySpark Notebook]

    D --> E[Read and Profile]
    E --> F[Data Cleaning]
    F --> G[Data Type Transformation]
    G --> H[Business Transformations]
    H --> I[Window Functions]
    I --> J[Analytical Joins]
    J --> K[Aggregations and Advanced Analytics]

    K --> L[Parquet with Snappy Compression]
    L --> M[Amazon S3 Processed Layer]

    M --> N[customers]
    M --> O[products]
    M --> P[categories]
    M --> Q[orders]
    M --> R[order_details]
    M --> S[fact_sales]
    M --> T[customer_sales]
    M --> U[product_sales]
    M --> V[category_sales]
    M --> W[monthly_sales]


Local Python Generator
        |
        v
CSV Files
        |
        v
S3 Raw Layer
raw/ecommerce/
        |
        v
AWS Glue + PySpark
        |
        +-- Read and Profile
        +-- Data Cleaning
        +-- Type Transformation
        +-- Business Transformations
        +-- Window Functions
        +-- Joins
        +-- Aggregations
        |
        v
Parquet + Snappy
        |
        v
S3 Processed Layer
processed/ecommerce/



