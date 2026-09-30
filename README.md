# Obesity Risk Intelligence System

## Overview

The **Obesity Risk Intelligence System** is a machine learning-based application that predicts obesity risk categories using health and lifestyle-related information.

The system integrates:

- Machine Learning prediction pipeline
- Flask REST API backend
- Streamlit interactive frontend
- SQLite database for prediction history
- SHAP-based Explainable AI for model interpretation

The application predicts one of seven obesity risk categories:

- Insufficient Weight
- Normal Weight
- Obesity Type I
- Obesity Type II
- Obesity Type III
- Overweight Level I
- Overweight Level II


---

# System Architecture

```
Streamlit Frontend
        |
        |
        v
Flask REST API Backend
        |
        |
        v
Machine Learning Model
        |
        |
        v
SQLite Database
```

---

# Project Structure

```
Obesity-Risk-Intelligence-System/

├── backend/
│   ├── routes/
│   ├── services/
│   ├── repositories/
│   ├── database.py
│   ├── production.py
│   └── run_production.py
│
├── frontend/
│   ├── components/
│   ├── services/
│   ├── app.py
│   ├── styles.py
│   └── config.py
│
├── models/
│   ├── obesity_risk_pipeline.joblib
│   └── model_metadata.json
│
├── database/
│   └── schema.sql
│
├── notebooks/
│
├── reports/
│
├── .streamlit/
│   └── config.toml
│
├── requirements.txt
└── README.md
```

---

# Technologies Used

## Machine Learning

- Python
- Pandas
- NumPy
- Scikit-learn
- SHAP
- Joblib


## Backend

- Flask
- Waitress
- SQLite


## Frontend

- Streamlit
- Python Requests


---

# Installation

## 1. Clone Repository

```bash
git clone <repository-url>

cd Obesity-Risk-Intelligence-System
```

---

## 2. Create Virtual Environment

Windows:

```powershell
python -m venv .venv
```

Activate environment:

```powershell
.venv\Scripts\activate
```

---

## 3. Install Dependencies

```powershell
pip install -r requirements.txt
```

---

# Running the Application

The application requires the backend API and frontend application to run separately.

---

# Backend Setup

Open a terminal inside the project root.

Activate the virtual environment:

```powershell
.venv\Scripts\activate
```

Start the backend server:

```powershell
python -m backend.run_production
```

The backend will run on:

```
http://127.0.0.1:5000
```

---

## Backend API Testing

### Health Check

Request:

```
GET /health
```

Example:

```powershell
curl.exe http://127.0.0.1:5000/health
```

Response:

```json
{
    "service": "obesity-risk-api",
    "status": "ok"
}
```

---

### Model Information

Request:

```
GET /model-info
```

Example:

```powershell
curl.exe http://127.0.0.1:5000/model-info
```

This returns:

- Selected model
- Model performance metrics
- Feature information
- Target classes

---

### Prediction API

Request:

```
POST /predict
```

Example input:

```json
{
    "Age":25,
    "Height":1.75,
    "Weight":85,
    "FCVC":2,
    "NCP":3,
    "CH2O":2,
    "FAF":1,
    "TUE":1,
    "CAEC":"Sometimes",
    "CALC":"Sometimes",
    "Gender":"Male",
    "family_history_with_overweight":"yes",
    "FAVC":"yes",
    "SMOKE":"no",
    "SCC":"no",
    "MTRANS":"Public_Transportation"
}
```

The API returns:

- Predicted obesity category
- Confidence score
- Class probabilities
- Prediction ID

---

# Frontend Setup

Open another terminal.

Activate the virtual environment:

```powershell
.venv\Scripts\activate
```

Run Streamlit:

```powershell
python -m streamlit run frontend/app.py
```

The frontend will open at:

```
http://localhost:8501
```

---

# Machine Learning Model

The final selected model:

```
Gradient Boosting - Tuned
```

Model files:

```
models/

├── obesity_risk_pipeline.joblib
└── model_metadata.json
```

The metadata file contains:

- Model configuration
- Feature information
- Evaluation metrics
- Target classes

---

# Model Performance

Final model evaluation:

```
Accuracy:
90.75%

Macro F1 Score:
89.73%
```

---

# Explainable AI

The system includes explainability features using SHAP.

Generated explanations include:

- Global feature importance
- Local prediction explanation
- Feature contribution analysis

Reports are generated inside:

```
reports/generated/
```

---

# Database

The application uses SQLite for storing prediction information.

Database schema:

```
database/schema.sql
```

The database supports:

- Prediction storage
- Prediction history
- Report generation


---

# Streamlit Configuration

The Streamlit appearance and theme are configured using:

```
.streamlit/config.toml
```

---

# Environment Configuration

Required dependencies are listed in:

```
requirements.txt
```

Install them using:

```powershell
pip install -r requirements.txt
```

---

# Application Flow

```
User Input
    |
    v
Streamlit Frontend
    |
    v
Flask Prediction API
    |
    v
Machine Learning Pipeline
    |
    v
Prediction Result
    |
    v
Database Storage
    |
    v
Explanation & Report Generation
```

---

# Future Improvements

Possible future enhancements:

- User authentication
- Cloud deployment
- Advanced monitoring dashboard
- Additional machine learning models
- Improved analytics features
