# Big Data Analytics with Apache Spark on Databricks

A portfolio project showcasing large-scale data analysis with **Apache Spark** on **Databricks**, covering SQL, Graph Analytics, Machine Learning Pipelines, RDD/MapReduce, and Structured Streaming.

---

## 🧰 Tech Stack

- **Databricks** (workspace, clusters, repos, jobs)  
- **Apache Spark** (SQL, DataFrames, MLlib, Streaming, RDDs)  
- **GraphFrames** (graph analytics)  
- **Python** 3.10+  
- Optional local dev: `pyspark`, `pandas`, `numpy`, `matplotlib`, `scikit-learn`, `imbalanced-learn`

---

## 📦 Datasets

- **Car Rentals** – exploration + graph analysis  
- **Credit Card Approval** – ML classification  
- **E-commerce UK** – RDD/MapReduce, time series & streaming simulation  

---

## 📁 Repository Structure

~~~text
.
├─ notebooks/
│  ├─ 01_car_rentals_sparksql_graphframes.py
│  ├─ 02_credit_scoring_ml_pipeline.py
│  ├─ 03_ecommerce_rdd_mapreduce.py
│  ├─ 04_streaming_simulation.py
│  └─ utils/
│     └─ viz.py
├─ configs/
│  └─ streaming.yaml
├─ data/               # optional; in Databricks use DBFS
├─ docs/
│  └─ Report.pdf
├─ requirements.txt
├─ README.md
└─ LICENSE
~~~

---

## 🚀 Running on Databricks

1. **Import this repo** into Databricks Repos.  
2. **Install GraphFrames** on the cluster:  
   - *Compute → Libraries → Install New → Maven*  
   - Example coordinate (for Spark 3.x):  
     `graphframes:graphframes:0.8.3-spark3.0-s_2.12`  
   - Restart cluster.  
3. **Upload datasets** to `dbfs:/FileStore/<project>/...`.  
4. **Run notebooks** sequentially to reproduce the analyses.

---

## 🖥️ Running Locally (optional)

1. Create a virtual environment and install dependencies:
   ~~~bash
   python -m venv .venv
   source .venv/bin/activate   # Windows: .venv\Scripts\activate
   pip install -r requirements.txt
   ~~~
2. Start a local Spark session (`master("local[*]")`).  
3. Execute scripts from `notebooks/`.  
   ~~~bash
   python notebooks/01_car_rentals_sparksql_graphframes.py
   ~~~
> Note: GraphFrames requires adding the JAR via `spark.jars.packages` or skipping graph sections locally.

---

## 🔎 Results Overview

- **Car Rentals:** most active customers, top car types, Tesla popularity, correlation between trips & reviews, PageRank & communities.  
- **Credit Scoring:** complete ML pipeline with data cleaning, feature engineering, Random Forest; achieved baseline AUC ≈ 0.60; oversampling improved recall.  
- **E-commerce:** UK dominated sales; November = peak month; RDD/MapReduce used for metrics by country/product/customer.  
- **Streaming:** near real-time ingestion of CSV micro-batches (~10s triggers), windowed aggregations, watermarking, and Parquet sink.  

---

## ⚙️ Configuration

Common paths (adjust in each notebook):
~~~python
BASE_PATH = "dbfs:/FileStore/bigdata"  # or ./data locally
INPUT_PATH = f"{BASE_PATH}/raw"
OUTPUT_PATH = f"{BASE_PATH}/processed"
CHECKPOINT_PATH = f"{BASE_PATH}/checkpoints"
~~~

---

## ✅ Requirements

- Databricks Runtime 13.x/14.x (Spark 3.x)  
- GraphFrames library installed on the cluster  
- Python 3.10+  

For local development, use this `requirements.txt`:

---
