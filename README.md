🚀 Spotify Data Pipeline using Apache Airflow (MWAA)
📌 Overview

This project demonstrates a production-style data pipeline built using:

Amazon S3 → Data storage
Apache Airflow (MWAA) → Orchestration
Amazon Redshift → Data warehouse

The pipeline processes Spotify-like streaming data and computes daily and hourly KPIs.

🏗️ Architecture

🔄 Pipeline Flow
Data Ingestion (S3)
songs.csv
users.csv
streams/*.csv
Validation Step
Ensure required columns exist
Prevent pipeline from running on bad data
Branching Logic
If validation fails → stop DAG
If validation passes → continue processing
KPI Computation
Genre-level KPIs:
listen count
popularity index
average duration
most popular track
Hourly KPIs:
unique listeners
top artist
session behavior
diversity index
user engagement by age
Load to Redshift
Data is upserted into:
genre_level_kpis
hourly_kpis
Archiving
Processed stream files are moved to: spotify_data/streams/archived/
📊 Airflow Execution

✔ All tasks successfully executed:

Validation
Branching
KPI computations
Redshift ingestion
File archiving
⚙️ Technologies Used
Python (Pandas, boto3)
Apache Airflow (MWAA)
Amazon S3
Amazon Redshift
PostgreSQL Hook
🔐 Data Handling Strategy
Raw data stored in S3 data bucket
Processed data stored in Redshift
Historical data preserved via S3 archiving
📈 Key Features
Data validation before processing
Dynamic branching using Airflow
Batch processing of streaming data
Idempotent upsert into Redshift
Automated archival for data lifecycle management
🔧 How to Run
Upload DAG to MWAA S3 bucket
Configure Airflow connection (redshift_default)
Upload data to S3 data bucket
Trigger DAG manually (Single Run)