# Soccer Results Analytics: Spark Streaming & Machine Learning

## 📌 Project Overview
This project implements a complete, end-to-end data pipeline focused on analyzing soccer match results from the **Mauritanian League**. The pipeline integrates batch processing, real-time stream simulation, and machine learning to provide both historical insights and real-time analytics.

The system is designed to handle historical datasets, enrich them with live data via web scraping, simulate a real-time event stream using Apache Kafka, and perform predictive modeling using Spark MLlib.

## 🛠 Technology Stack
* **Language:** Python
* **Data Processing:** Apache Spark (PySpark)
* **Stream Processing:** Apache Kafka & Spark Structured Streaming
* **Machine Learning:** Spark MLlib (Random Forest Classifier)
* **Storage Format:** Apache Parquet
* **Environment:** Docker & Jupyter Notebooks
* **Scraping:** BeautifulSoup / Pandas

## 🏗 System Architecture
The pipeline follows a modern data engineering architecture:
1. **Batch Layer:** Cleans and prepares historical data (2007-2025) using Spark, saving it in optimized Parquet format.
2. **Enrichment Layer:** A web scraping workflow collects the latest results from the current season to enrich the dataset.
3. **Streaming Layer:** 
   - A **Kafka Producer** simulates a real-time match event stream.
   - A **Spark Structured Streaming** application consumes the stream, applies windowed aggregations (e.g., total goals per team), and uses watermarking for late-data handling.
4. **Machine Learning Layer:** A Random Forest model is trained on historical data and evaluated against the scraped current-season data to predict match outcomes.

## 📂 Project Structure
```text
mini-project-spark-football/
├── README.md
├── data/
│   ├── rim_championnat_results_2007-2025.csv  <-- Historical Dataset
│   └── current_season_scraped.csv            <-- Enriched Data
├── notebooks/
│   ├── prepare_data.ipynb                    <-- Data Cleaning & Enrichment
│   └── train_model.ipynb                     <-- ML Training & Evaluation
├── src/
│   ├── producer.py                           <-- Kafka Producer (Stream Simulator)
│   ├── stream_job.py                         <-- Spark Streaming Application
│   └── predict.py                            <-- Match Outcome Predictor
├── outputs/
│   ├── prepared/                             <-- Cleaned Parquet files
│   ├── streaming/                            <-- Real-time analytics output
│   └── models/                               <-- Trained ML Models
├── checkpoints/                              <-- Spark Checkpointing directory
└── report.pdf                                <-- Final Project Report

## 🚀 Getting Started
### Prerequisites
Ensure you have **Docker** installed and running. This project is designed to run within a Spark-Kafka Docker container environment.

### Installation & Setup
1. Clone this repository:
   ```bash
   git clone https://github.com/24042-AB7/Big-Data-prj.git
   cd mini-project-spark-football

