# Financial-Forecasting-Frontier-Distributed-ML

A distributed machine learning pipeline built on Hadoop, Hive, and Apache Spark for large-scale banking data analysis, predictive modeling, and real-time transaction monitoring.

Overview
Traditional single-machine ML pipelines struggle with the volume and velocity of financial data. This project demonstrates how distributed computing technologies can be applied to banking data to enable scalable EDA, batch predictive modeling, and live transaction stream processing — all within a unified pipeline.

Using the Bank Marketing dataset, the project covers the full spectrum from raw data storage in Hadoop/Hive through to loan default prediction with Spark ML and real-time monitoring via Spark Streaming.

Tech Stack
Component	Technology
Distributed Storage	Hadoop HDFS, Apache Hive
Big Data Processing	Apache Spark (PySpark)
ML Framework	Spark MLlib
Real-Time Processing	Spark Streaming
Data Processing	MapReduce
Language	Python, HiveQL
Notebook	Jupyter
Architecture
Raw Banking Data (bank.csv)
        │
        ▼
Hadoop HDFS Storage
        │
        ▼
Hive — SQL Querying & Data Management
        │
        ▼
Apache Spark — Large-Scale EDA & Feature Engineering
(Data Parallelism across distributed nodes)
        │
        ├──────────────────────────────┐
        ▼                              ▼
Spark ML                        Spark Streaming
(Batch Predictive Modeling)     (Real-Time Transaction Monitoring)
(Loan Default Prediction)       (Anomaly Detection)
Dataset
Bank Marketing Dataset — direct marketing campaign data from a Portuguese banking institution.

Feature	Description
age	Client age
job	Type of job
balance	Average yearly balance
housing	Has housing loan?
loan	Has personal loan?
contact	Contact communication type
duration	Last contact duration (seconds)
campaign	Number of contacts during campaign
poutcome	Outcome of previous campaign
y	Target — has the client subscribed?
Model Performance
Combined ensemble prediction accuracy: 81.50%

Key Components
1. Data Management — Hadoop & Hive
Banking data is ingested into Hadoop HDFS for distributed storage. Apache Hive provides a SQL-like interface for querying and managing large volumes of structured banking records without moving data to a single machine.

2. Exploratory Data Analysis — Apache Spark
Large-scale EDA is performed using PySpark DataFrames, leveraging data parallelism to process the dataset across distributed partitions. Analysis covers feature distributions, correlations, and anomaly identification.

3. Predictive Modeling — Spark MLlib
A classification model is built using Spark MLlib to predict loan default probability and customer subscription behavior. The pipeline includes feature engineering, encoding, and model evaluation — all distributed across the Spark cluster.

4. Real-Time Monitoring — Spark Streaming
Spark Streaming is used to simulate and process a live stream of banking transactions, enabling real-time monitoring for unusual transaction patterns and anomaly detection.

5. MapReduce
Custom MapReduce jobs handle batch aggregation tasks — summarizing transaction volumes, computing branch-level statistics, and preprocessing data at scale.

Setup & Installation
Prerequisites
Java 8+
Hadoop 3.x
Apache Hive 3.x
Apache Spark 3.x
Python 3.8+
Installation
git clone https://github.com/Satyam-G-Kulkarni/Financial_Forecasting_Frontier.git
cd Financial_Forecasting_Frontier
pip install -r requirements.txt
Configure Hadoop & Spark
Ensure Hadoop, Hive, and Spark are installed and configured on your system. Place bank.csv in HDFS:

hdfs dfs -mkdir /banking_data
hdfs dfs -put bank.csv /banking_data/
Run the Notebook
jupyter notebook Financial_Forecasting_Frontier.ipynb
Project Structure
Financial_Forecasting_Frontier/
├── Financial_Forecasting_Frontier.ipynb           # Main pipeline notebook
├── Data Analysis and Management using Hadoop & Hive.pdf  # Detailed report
├── Mapreduce_files.rar                            # MapReduce job files
├── bank.csv                                       # Banking dataset
└── README.md
Future Work
Deploy on cloud cluster (AWS EMR or GCP Dataproc) for true distributed scale
Integrate MLflow for experiment tracking and model versioning
Build a real-time dashboard for transaction monitoring using Grafana or Streamlit
Extend Spark Streaming to consume from Kafka topics
