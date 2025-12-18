# 🛒 Spark Online Retail Sales Prediction (End‑to‑End ML Project)

## 📌 Project Overview

This project demonstrates an **end‑to‑end Spark ML pipeline** using the **Online Retail dataset**. It covers **data sampling, feature engineering, Spark SQL, ML modeling, and evaluation**, designed as a **portfolio‑ready, recruiter‑friendly project**.

The goal is to **predict product Quantity sold** using transactional, temporal, and pricing features — all processed at scale using **PySpark**.

---

## 🧠 Key Skills Demonstrated

* PySpark DataFrames & SparkSession
* Window functions & random sampling
* Data cleaning & filtering
* Feature engineering (time‑based & business logic)
* Spark SQL transformations
* Categorical encoding (StringIndexer)
* ML pipeline with **RandomForestRegressor**
* Model evaluation (RMSE & R²)
* Visualization (Actual vs Predicted & Residuals)

---

## 📂 Dataset

* **Source**: Online Retail (CSV)
* **Type**: Transactional E‑commerce data
* **Main Columns**:

  * InvoiceDate
  * Country
  * Quantity (Target)
  * UnitPrice

> ⚠️ To make the project laptop‑friendly, **stratified random sampling** is applied (500 rows per country).

---

## 🔧 Project Workflow

### 1️⃣ Spark Session & Data Loading

* Create SparkSession
* Load CSV with schema inference
* Basic exploration (schema, columns, distinct countries)

---

### 2️⃣ Country‑Wise Sampling (Big‑Data Friendly)

* Use **Window functions** with `row_number()`
* Randomly sample **500 records per country**

**Why?**

* Maintains country distribution
* Reduces memory usage
* Simulates big‑data processing logic

---

### 3️⃣ Data Cleaning

* Drop non‑useful columns:

  * InvoiceNo
  * CustomerID
  * Description
  * StockCode
* Remove invalid rows:

  * Quantity ≤ 0
* Null value check across all columns

---

### 4️⃣ Feature Engineering

#### 🕒 Time‑Based Features

Extracted from `InvoiceDate`:

* InvoiceMonth
* InvoiceWeekDay
* InvoiceHour

#### 🏷️ Business Logic Features (Spark SQL)

```sql
HighPriceFlag   → UnitPrice > 50
LowPriceFlag    → UnitPrice < 5
IsWeekend       → Saturday / Sunday
IsMorning       → Hour < 12
IsEvening       → Hour ≥ 18
```

---

### 5️⃣ Categorical Encoding

* Encode **Country** using `StringIndexer`
* Handle unseen categories with `handleInvalid='keep'`

---

### 6️⃣ ML Preparation

* **Target Variable**: `Quantity`
* **Features**: All remaining columns
* Assemble features using `VectorAssembler`
* Train/Test split: **80% / 20%**

---

### 7️⃣ Model Training

* Algorithm: **RandomForestRegressor**
* Configuration:

  * Trees: 100
  * Max Depth: 8
  * Max Bins: 40

**Why Random Forest?**

* Handles non‑linearity
* Robust to noise
* No feature scaling required

---

### 8️⃣ Model Evaluation

**Metrics Used:**

* RMSE (Root Mean Squared Error)
* R² Score

```text
RMSE → Measures prediction error magnitude
R²   → Measures explained variance
```

---

### 9️⃣ Visualization (Post‑Spark Analysis)

📊 **Actual vs Predicted Scatter Plot**

* Validates prediction accuracy

📉 **Residual Plot**

* Detects bias and heteroscedasticity

> Visualizations are generated after converting Spark output to Pandas for interpretability.

---

## 📈 Final Output

* Trained Random Forest regression model
* Evaluation metrics (RMSE & R²)
* Visual diagnostics
* Clean, reproducible Spark ML pipeline

---

## 🚀 How to Run

```bash
pip install pyspark pandas matplotlib seaborn
```

Run the notebook or script in:

* Google Colab
* Local Spark environment
* Any Spark‑enabled platform

---

## 🎯 Why This Project Matters 

✅ Real‑world transactional dataset
✅ Spark + SQL + ML combined
✅ Scalable design with sampling strategy
✅ Clear business‑driven feature engineering
✅ Production‑style ML workflow

---

## 👤 Author

**Zahraa Rubaie**
Data Scientist | Spark | ML | SQL | Power BI

---

⭐ If you find this project useful, consider starring the repository!
