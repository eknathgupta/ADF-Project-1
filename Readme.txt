Azure Data Factory & Databricks Retail Data Pipeline Project
 Project Overview

This project is a complete Retail Data Engineering pipeline built on Azure Cloud.
It covers data ingestion, storage, transformation, and cleaning using ADF, ADLS Gen2, and Databricks.

The goal is to extract retail transaction data from an API source, land it in Azure Data Lake (Bronze layer), clean and transform it in Databricks (Silver layer), and finally prepare it for analysis (Gold layer).
Step--

A[API (Retail Transactions)] -->|HTTP Connector| B[Azure Data Factory (ADF)]
B -->|Copy Activity| C[Azure Data Lake Storage (ADLS Gen2)]
C -->|Raw Data| D[Bronze Layer]
D -->|Read and Clean| E[Azure Databricks]
E -->|Filter / Transform / Type Casting / Dedup| F[Silver Layer]
F -->|Aggregate Metrics| G[Gold Layer]
G -->|Visualization| H[Power BI Dashboard]

Explain-
Step 1: Storage Account Setup

Created an Azure Storage Account named adfprojectstorage1

Enabled Hierarchical Namespace (for Data Lake Gen2)

Inside the storage, created three containers to follow the Medallion Architecture:

Step 2: Building ADF Pipeline (HTTP → ADLS)

Created a new pipeline in Azure Data Factory (ADF)

Used the HTTP connector to pull raw retail transaction data

Sink: Azure Data Lake Storage Gen2

Format: .parquet
------
Pipeline Flow:

HTTP Dataset: API endpoint as the data source

Copy Activity: Transfers the data from API to ADLS

Sink Dataset: Saves output in the Bronze layer
---
Databricks Integration with ADLS

Connected Databricks to ADLS using the account access key.
Step 4- Data Cleaning & Transformation (Bronze → Silver)
- Remove Null or Invalid Records
- Standardize String Columns
- Convert Data Types
- Apply Business Logic
- Drop Duplicates
 -Save Clean Data to Silver Layer
--------------------------------------------
 Key Learnings

Created a real-world data pipeline using Azure Data Factory & Databricks

Learned how to extract data from an API and store it in ADLS

Implemented Medallion Architecture (Bronze → Silver → Gold)

Performed end-to-end transformation using PySpark

Built a reusable and scalable data pipeline structure for retail analytics


Created by
- Eknath Gupta

