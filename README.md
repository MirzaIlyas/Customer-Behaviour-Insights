# Customer-Behaviour-Insights
 Customer Behavior Insights Data Pipeline project.

It includes:

Project summary

Directory structure

Airflow & PySpark job overview

Setup instructions

Security & testing notes

Your author info with LinkedIn

Disclaimer to avoid legal issues



# 📦 Customer Behavior Insights Data Pipeline (PySpark + AWS + Airflow)

This repository contains a simulated version of a real-world data engineering pipeline project that reflects the structure, logic, and tooling described in Mirza Ilyas Ali Baig's resume and project summaries.

## 🚀 Project Summary
A PySpark-based data pipeline that ingests data from:
- Amazon S3 (CSV/Parquet data)
- Snowflake (customer transaction tables)
- Web API (real-time location data)

The pipeline performs transformations and writes the final output to:
- Amazon S3 (as Parquet)
- Snowflake (analytics tables)

All jobs are scheduled and monitored using **Apache Airflow**.

---

## 📂 Repository Structure
```bash
customer_behavior_insights/
│
├── dags/
│   ├── customer_behavior_dag.py        # Airflow DAG definition
│
├── jobs/
│   ├── extract_s3_data.py              # PySpark job to read from S3
│   ├── extract_snowflake_data.py       # PySpark job to read from Snowflake
│   ├── extract_webapi_data.py          # PySpark job to read from Web API
│   ├── master_aggregator.py            # Final job to combine and transform all sources
│
├── utils/
│   ├── spark_session.py                # Spark session creation logic
│   ├── secrets_manager.py              # AWS Secrets Manager utility
│   └── api_utils.py                    # API request logic
│
├── config/
│   └── pipeline_config.yaml            # Configuration and source metadata
│
├── README.md                           # Project documentation
└── requirements.txt                    # Python dependencies for local development
```

---

## ✅ Setup & Installation
```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate

# Install required packages
pip install -r requirements.txt
```

---

## ⚙️ Airflow DAG
- Scheduled to run at 9:00 AM EST daily
- Includes steps:
  1. Start EMR cluster (simulated)
  2. Run extract_s3_data.py
  3. Run extract_snowflake_data.py
  4. Run extract_webapi_data.py
  5. Run master_aggregator.py
  6. Terminate EMR cluster

---

## 📊 Transformations
Performed in PySpark:
- Filters, joins, UDFs
- Aggregations and window functions
- Schema validation and error handling

---

## 🛡️ Security
- Snowflake credentials stored in **AWS Secrets Manager**
- Retrieved securely in jobs via `boto3`

---

## 🧪 Testing
- Unit tests (in progress)
- PySpark logic tested on local mode using `SparkSession(master=\"local\")`

---

## 👨‍💻 Author
**Mirza Ilyas Ali Baig**  
Data Engineer | AWS | PySpark | Airflow | Power BI  
[LinkedIn](https://www.linkedin.com/in/mirzailyas/)  

---

## 📜 Disclaimer
This is a sample/simulated project meant for showcasing skills and project understanding. It does not contain real client data or credentials.
