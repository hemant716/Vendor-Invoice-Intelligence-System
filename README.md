# Vendor Invoice Intelligence System

##  Freight Cost Prediction & Invoice Risk Detection



## 📌 Overview

The **Vendor Invoice Intelligence System** is an end-to-end Machine Learning application that helps finance and procurement teams automate invoice auditing processes.



- Predict expected freight costs
- Detect suspicious or risky invoices
- Reduce manual invoice review effort
- Improve financial accuracy and fraud detection

The project combines:
- Machine Learning
- Feature Engineering
- Model Deployment
- Interactive Dashboards
- Business Analytics

Built using **Python, scikit-learn, SQLite, and Streamlit**.

---

## 🎯 Business Problem

Organizations process thousands of vendor invoices every month. Manual invoice verification is:

- Time-consuming
- Error-prone
- Expensive
- Difficult to scale

Common issues include:

- Freight overcharging
- Invoice amount mismatches
- Suspicious billing patterns
- Fraudulent transactions

This system automates invoice intelligence using Machine Learning to identify anomalies and improve operational efficiency.

---

## 💼 Business Value

- Reduce manual invoice review time by ~70%
- Detect potentially overcharged freight invoices
- Prioritize risky invoices for auditor review
- Improve invoice approval efficiency
- Minimize financial leakage and fraud risk

---

# 🏗️ System Architecture

```text
SQLite Database
       ↓
Data Preprocessing
       ↓
Feature Engineering
       ↓
Machine Learning Models
   ├── Freight Prediction
   └── Invoice Risk Detection
       ↓
Serialized .pkl Models
       ↓
Inference Layer
       ↓
Streamlit Web Application
       ↓
Live Deployment
```

---

# 🔑 Key Features

- 🧠 Freight Cost Prediction Model
- 🚨 Invoice Risk Detection Model
- 📊 Confidence Score Prediction
- 📈 Interactive Streamlit Dashboard
- ⚡ Real-Time Predictions
- 🚀 Live Cloud Deployment
- 🗂️ SQLite Data Integration
- 🔍 Business-Focused Analytics

---





# 💡 How the System Works

---

## 1️⃣ Freight Cost Prediction Model

### Objective
Estimate the expected freight cost for a vendor invoice.

### Inputs
- Invoice Quantity
- Invoice Amount

### Output
- Predicted Freight Cost

### Business Use Case
If the actual freight charged is significantly higher than the predicted value, the invoice may indicate:
- Overcharging
- Billing errors
- Vendor discrepancies

### Example

| Invoice Amount | Quantity | Predicted Freight |
|---|---|---|
| $18,500 | 420 | $1,120 |

If the vendor bills $1,500 freight instead of the expected $1,120, the invoice can be flagged for manual review.

---

## 2️⃣ Invoice Risk Detection Model

### Objective
Identify invoices requiring manual review before payment approval.

### Inputs
- Invoice Quantity
- Invoice Amount
- Freight Cost
- Purchase Order Totals
- Total Item Quantity

### Output
- Safe to Auto-Approve
- Requires Manual Review

### Detects
- Abnormal freight ratios
- Pricing mismatches
- Suspicious invoice patterns
- High-risk billing behavior

### Example

| Invoice Amount | PO Total | Result |
|---|---|---|
| $2,468 | $2,476 | Manual Review Required |

---

# 📊 Data & Feature Engineering

## Data Source

- SQLite Database containing:
  - Vendor invoices
  - Purchase order records
  - Receiving information

---

## Features Used

### Numerical Features
- Invoice Quantity
- Invoice Dollars
- Freight Cost
- Total Item Quantity
- Total Item Dollars

### Engineered Features
- Freight-to-Invoice Ratio
- Invoice Variance
- Purchase Order Matching Metrics

---

# 🤖 Machine Learning Models

## Freight Prediction

### Model Used
- Random Forest Regressor

### Other Models Tested
- Linear Regression
- Decision Tree Regressor

### Why Random Forest?
Random Forest performed best because it captures non-linear invoice pricing behavior while reducing overfitting.

---

## Invoice Risk Classification

### Model Used
- Random Forest Classifier

### Why Scaling?
Feature scaling improved model consistency and classification stability across invoice patterns.

---

# 📊 Model Performance

| Model | Metric | Score |
|---|---|---|
| Freight Prediction | MAE | 24.11 |
| Freight Prediction | R² Score | 96.99% |
| Invoice Risk Detection | Accuracy | 89% |
| Invoice Risk Detection | F1-Score | 87% |

---

# 🔍 Example Predictions

## Freight Cost Prediction

### Input
```python
{
    "invoice_quantity": 420,
    "invoice_dollars": 18500
}
```

### Output
```python
Predicted Freight Cost: 1120.45
```

---

## Invoice Risk Detection

### Input
```python
{
    "invoice_quantity": 150,
    "invoice_dollars": 2468,
    "freight": 580,
    "total_item_quantity": 148,
    "total_item_dollars": 2476
}
```

### Output
```python
Prediction: Requires Manual Review
Confidence Score: 89%
```

---

# 🖥️ Streamlit Dashboard Features

- Interactive input forms
- Real-time predictions
- Risk confidence scores
- Responsive dashboard UI
- Clean visualization interface
- Business-friendly workflow

---

# ⚙️ Project Workflow

```text
1. DATA LOADING → SQLite database
        ↓
2. PREPROCESSING → Missing value handling & feature engineering
        ↓
3. MODEL TRAINING → Regression & classification models
        ↓
4. MODEL EVALUATION → Performance metric validation
        ↓
5. SERIALIZATION → Save models using joblib/pickle
        ↓
6. INFERENCE API → Prediction scripts
        ↓
7. STREAMLIT UI → User interaction layer
        ↓
8. CLOUD DEPLOYMENT → Streamlit Cloud
```

---

# 📁 Project Structure

```text
vendor-invoice-intelligence-system/
│
├── Data/
│   └── inventory.db
│
├── freight_cost_prediction/
│   ├── data_preprocessing.py
│   ├── modeling_evaluation.py
│   ├── train.py
│   └── models/
│       └── predict_freight_model.pkl
│
├── invoice_flagging/
│   ├── data_preprocessing.py
│   ├── modeling_evaluation.py
│   ├── train.py
│   └── models/
│       └── predict_flag_invoice.pkl
│
├── inference/
│   ├── predict_freight.py
│   └── predict_invoice_flag.py
│
├── notebooks/
│
├── images/
│
├── app.py
├── requirements.txt
├── README.md
└── LICENSE
```

---

# ⚡ Quick Start

## 1️⃣ Clone Repository

```bash
git clone https://github.com/hemant716/Vendor-Invoice-Intelligence-System.git

cd vendor-invoice-intelligence-system
```

---

## 2️⃣ Create Virtual Environment

### Windows
```bash
python -m venv venv

venv\Scripts\activate
```

### macOS/Linux
```bash
python3 -m venv venv

source venv/bin/activate
```

---

## 3️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 4️⃣ Train Models

```bash
python freight_cost_prediction/train.py

python invoice_flagging/train.py
```

---

## 5️⃣ Run Streamlit App

```bash
streamlit run app.py
```

Open in browser:

```text
http://localhost:8501
```

---

# 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core Programming |
| Pandas | Data Manipulation |
| NumPy | Numerical Computing |
| scikit-learn | Machine Learning |
| Streamlit | Web Application |
| SQLite | Database |
| Joblib | Model Serialization |

---

# 📦 Requirements

```txt
streamlit==1.45.0
scikit-learn==1.5.1
pandas==2.2.2
numpy==1.26.4
joblib==1.4.2
plotly==5.22.0
```

---

# 🔮 Future Improvements

- Add SHAP Explainability
- Add Anomaly Detection Models
- Deploy REST API using FastAPI
- Dockerize Application
- CI/CD Deployment Pipeline
- Real-Time Invoice Monitoring
- Advanced Fraud Detection Analytics

---

# 📜 License

This project is licensed under the MIT License.

---

# 👨‍💻 Author

## Hemant vaidya


---



---

## Thank You

Building intelligent financial systems using Machine Learning 🚀
# Vendor-Invoice-Intelligence-System
