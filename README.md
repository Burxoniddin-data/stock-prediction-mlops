# Stock Prediction MLOps Project

**A complete production-grade MLOps system for real-time stock price prediction** built with **PostgreSQL, Kafka, Airflow, MLflow, FastAPI, and Docker**.

This project is designed especially for **beginners** who want to learn how modern MLOps systems work in real life. It handles everything from data collection to model serving with automation.

---

## 🎯 Project Objective

Build an end-to-end system that:
- Collects historical and real-time stock data
- Stores data in PostgreSQL
- Streams live prices using Kafka
- Automates feature engineering, model training, and retraining using Airflow
- Tracks experiments and manages models with MLflow
- Serves predictions through a FastAPI REST API

**Target Ticker Example**: AAPL (Apple), TSLA, GOOGL, etc.

---

## 🛠 Tech Stack & Purpose

| Tool            | Purpose                                                                 |
|----------------|-------------------------------------------------------------------------|
| **PostgreSQL** | Stores historical stock data, features, predictions, and metadata      |
| **Kafka**      | Real-time data streaming (live stock prices)                           |
| **Airflow**    | Orchestrates daily/weekly pipelines (ETL, training, prediction)        |
| **MLflow**     | Tracks experiments, logs metrics, versions models                      |
| **FastAPI**    | Serves machine learning model predictions via REST API                 |
| **Docker**     | Containerizes everything for easy deployment and consistency           |
| **yfinance**   | Fetches free stock market data                                         |

---

## 📁 Full Project Structure

```bash
stock-prediction-mlops/
├── .env                          # Environment variables (secrets)
├── .gitignore
├── docker-compose.yml            # Orchestrates all services
├── Dockerfile                    # For FastAPI service
├── requirements.txt
├── README.md
│
├── data/                         # All data files
│   ├── raw/                      # Raw downloaded data
│   ├── processed/                # Cleaned and engineered features
│   └── predictions/              # Saved prediction results
│
├── dags/                         # Airflow DAGs (Workflows)
│   ├── data_ingestion_dag.py
│   ├── feature_engineering_dag.py
│   ├── train_model_dag.py
│   └── predict_dag.py
│
├── src/                          # Main application code
│   ├── __init__.py
│   ├── config.py                 # Configuration loader
│   ├── data_ingestion.py         # Fetch data from yfinance
│   ├── feature_engineering.py    # Create technical indicators
│   ├── models/
│   │   ├── train.py              # Model training + MLflow logging
│   │   ├── predict.py            # Inference logic
│   │   └── utils.py
│   ├── kafka/
│   │   ├── producer.py           # Send real-time prices to Kafka
│   │   └── consumer.py           # Consume and process live data
│   └── api/
│       ├── main.py               # FastAPI application
│       ├── routers/
│       │   └── prediction.py
│       └── dependencies.py
│
├── notebooks/                    # Jupyter notebooks for exploration
│   └── 01_eda.ipynb
│
├── mlruns/                       # MLflow tracking data (auto-generated)
├── logs/                         # Airflow and app logs
├── tests/                        # Test files
└── scripts/                      # Helper scripts
    └── init_db.sql               # Database schema