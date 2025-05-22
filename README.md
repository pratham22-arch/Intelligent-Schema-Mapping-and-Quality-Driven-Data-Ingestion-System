# 🧠 Intelligent Schema Mapping and Quality-Driven Data Ingestion System

This project implements a complete data ingestion pipeline capable of handling **heterogeneous, multi-source data**, automatically mapping schemas, detecting errors and anomalies, and routing records based on quality for downstream use.

It simulates a realistic data ingestion scenario with vendors providing data in different formats (CSV, SQL, and nested JSON from an API), then applies a **multi-stage validation pipeline** that merges, standardizes, and evaluates the quality of each record.

---

## 🚀 Features

### 🔄 Multi-Source Data Ingestion
- Loads structured data from:
  - CSV (`vendor_A.csv`)
  - SQLite DB (`vendor_b_table`)
  - JSON API (nested format)

### 🧬 Schema Mapping & Harmonization
- Uses `sentence-transformers` (MiniLM) for semantic column name similarity
- Falls back to **Groq LLM (LLaMA-3)** when confidence is low or mapping is ambiguous
- Ensures all sources are aligned to a **unified target schema**

### 🧹 Validation & Cleaning
- **Rule-based checks** (e.g., invalid quantities, suspicious prices)
- **Missing value imputation** using **KNN Imputer**
- **Anomaly detection** using **Isolation Forest**

### 🏷️ Quality-Based Record Routing
- Classifies records into:
  - **Gold** – Fully clean, high-confidence records
  - **Silver** – Minor issues or imputed values
  - **Manual Review** – Low-quality or heavily anomalous data

### 📦 Outputs
- `validated_data.csv`: Full merged and cleaned dataset
- `gold_layer.csv`, `silver_layer.csv`, `manual_review.csv`: Stratified layers based on data quality
- Quality layer bar chart

---

## 📚 Target Schema
All ingested data is standardized to this schema:
- `invoice_id`
- `product_code`
- `product_name`
- `qty`
- `unit_price`
- `customer_id`
- `transaction_date`
- `customer_country`
- `source` *(indicates whether record came from CSV/SQL/API)*

---

## 🧠 Technologies Used
- **Python, Pandas, SQLite, Requests**
- **SentenceTransformers (MiniLM)** for semantic column matching
- **Groq LLM (LLaMA 3)** for fallback schema mapping
- **Scikit-learn** for imputation and anomaly detection
- **Matplotlib** for basic visualization

---


