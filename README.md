# Obesity Risk Intelligence System

The **Obesity Risk Intelligence System** is a university group project developed by four members to classify obesity-risk categories using demographic, physical, nutritional, and lifestyle information. It combines a trained machine learning pipeline, a Streamlit interface, Flask backend services, SQLite prediction history, and downloadable PDF assessment reports.

**🌐 Live Demo:** [Obesity Risk Intelligence System](https://sm-obesity-risk-intelligence.streamlit.app/)

> This application is intended for educational and research purposes. Its predictions are not medical diagnoses and should not replace professional healthcare advice.

## Project Team

This project was developed collaboratively by the following four members:

| Member | Name |
|---|---|
| 1 | Sivamathuran |
| 2 | Thushanya |
| 3 | Mathuran |
| 4 | Pirushalini |

The team contributed to data analysis, preprocessing, model development, evaluation, explainability, application development, testing, and documentation.

## Overview

The application accepts 16 input features and predicts one of seven categories:

- Insufficient Weight
- Normal Weight
- Overweight Level I
- Overweight Level II
- Obesity Type I
- Obesity Type II
- Obesity Type III

The final model is a **tuned Gradient Boosting Classifier** packaged with its preprocessing steps in a Scikit-learn pipeline.

## Key Features

- Guided assessment covering physical profile, nutrition, and lifestyle
- Seven-class obesity-risk prediction
- Model confidence and class probability distribution
- BMI indicator alongside the prediction
- SQLite assessment storage and prediction history
- Saved assessment review
- Downloadable PDF assessment reports
- Flask REST API with input validation and error handling
- Sri Lanka time display
- Configurable history access, storage, and clearing
- Automated tests for backend, frontend helpers, and integration
- Notebook-based SHAP explainability and model evaluation

## Technology Stack

| Area | Technologies |
|---|---|
| Programming | Python |
| Data analysis | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn, Altair |
| Machine learning | Scikit-learn |
| Explainability | SHAP |
| Model persistence | Joblib |
| Backend | Flask, Waitress |
| Frontend | Streamlit |
| API communication | Requests |
| Database | SQLite |
| PDF reports | ReportLab |
| Testing | Pytest |
| Live demo hosting | Streamlit Community Cloud |

## System Architecture

In this repository, the Streamlit frontend communicates with a Flask REST API through the frontend API client.

The backend validates submitted inputs, passes them through the saved preprocessing and classification pipeline, and returns the predicted category, confidence, and class probabilities. When prediction storage is enabled, it saves the assessment in SQLite and supports history retrieval and PDF report generation.

| Component | Responsibility |
|---|---|
| Streamlit frontend | Assessment forms, results, history, and report downloads |
| Frontend API client | Communication with Flask endpoints |
| Flask routes | Health checks, predictions, model information, and history |
| Input validator | Required fields, types, ranges, and accepted categories |
| Model service | Model loading, version checking, and inference |
| Prediction repository | SQLite assessment storage and retrieval |
| PDF report service | Formatting saved assessments as downloadable reports |

## Dataset and Input Features

The model-development dataset contains **20,758 records** and seven target classes. The target column is `NObeyesdad`.

The predictive inputs are:

| Group | Features |
|---|---|
| Numerical | Age, Height, Weight, FCVC, NCP, CH2O, FAF, TUE |
| Ordinal | CAEC, CALC |
| Nominal | Gender, family_history_with_overweight, FAVC, SMOKE, SCC, MTRANS |

The identifier column is excluded from model inputs.

### Preprocessing

The shared preprocessing configuration includes:

- Median imputation and standard scaling for numerical features
- Most-frequent imputation and ordered encoding for ordinal features
- Most-frequent imputation and one-hot encoding for nominal features
- Handling of previously unseen categorical values

The 16 original inputs produce **25 transformed features**.

Preprocessing is included in the model pipeline so that training and inference apply the same transformations.

## Machine Learning Workflow

The project follows these stages:

1. Dataset understanding and quality checks
2. Exploratory data analysis
3. Feature preprocessing
4. Baseline model comparison
5. Hyperparameter tuning
6. Final model selection and independent test evaluation
7. Explainability analysis
8. Application integration and testing

### Data Splitting

The dataset is divided using stratified sampling and random seed `42`.

| Partition | Records | Approximate proportion |
|---|---:|---:|
| Training | 14,530 | 70% |
| Validation | 3,114 | 15% |
| Test | 3,114 | 15% |

Training data supports fitting and cross-validation. Validation data supports model comparison and the BMI experiment. The test set is reserved for final evaluation.

### Baseline Models

The baseline comparison includes:

- Dummy Classifier as a reference
- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting

### Hyperparameter Tuning

Random Forest and Gradient Boosting are tuned using:

- `RandomizedSearchCV`
- Five-fold stratified cross-validation
- 20 sampled parameter configurations per model
- Macro F1 as the primary selection metric
- Accuracy, balanced accuracy, and weighted F1 as supporting metrics
- Training scores to help assess generalisation gaps

The selected pipeline is refitted on the combined training and validation data before final test evaluation.

## Final Model Performance

The selected model is **Gradient Boosting - Tuned**.

| Independent test metric | Score |
|---|---:|
| Accuracy | 90.75% |
| Balanced Accuracy | 89.76% |
| Macro F1 | 89.73% |
| Weighted F1 | 90.72% |

The saved artifacts are:

- `models/obesity_risk_pipeline.joblib`
- `models/model_metadata.json`

The metadata records the selected model, hyperparameters, input features, class labels, evaluation metrics, and reproducibility settings.

**Scikit-learn `1.8.0` is required**, matching the saved model's version and the project's dependency configuration.

### BMI Ablation Experiment

The project compares the original 16-feature model with a version that adds BMI.

| Feature configuration | Validation Macro F1 |
|---|---:|
| Original 16 features | 89.78% |
| Original features + BMI | 89.46% |

Adding BMI slightly reduced validation performance in this experiment. The final prediction pipeline therefore retains the original 16 features.

The interface still displays BMI as supplementary assessment information.

## Model Explainability

Notebook 06 examines the saved model using:

- Built-in Gradient Boosting feature importance
- SHAP PermutationExplainer
- A training-data background reference
- Class-specific SHAP analysis across 100 test records
- A local explanation for an individual prediction

Generated tables include:

- `reports/generated/feature_importance.csv`
- `reports/generated/local_shap_explanation.csv`

SHAP analysis runs in the explainability notebook. The application displays predictions and probabilities; it does not calculate a new SHAP explanation for every submitted assessment.

Feature contributions describe model behaviour and do not establish causal relationships.

## Project Structure

| Path | Contents |
|---|---|
| `backend/` | Flask application, routes, validation, model service, database access, and PDF generation |
| `frontend/` | Streamlit application, components, API client, styling, and time utilities |
| `src/` | Shared preprocessing configuration |
| `models/` | Trained pipeline and model metadata |
| `data/raw/` | Source dataset |
| `data/processed/` | Exported test inputs and labels |
| `database/` | SQLite schema and runtime database location |
| `notebooks/` | Six stages of model development and analysis |
| `reports/generated/` | Model comparisons, tuning results, evaluation tables, and explanations |
| `tests/` | Automated application and preprocessing tests |
| `.streamlit/` | Streamlit theme and configuration |
| `requirements.txt` | Python dependencies |
| `LICENSE` | MIT license |

## Notebook Guide

| Notebook | Purpose |
|---|---|
| `01_data_understanding.ipynb` | Dataset structure and initial inspection |
| `02_eda.ipynb` | Exploratory data analysis |
| `03_preprocessing.ipynb` | Feature preparation and preprocessing |
| `04_baseline_models.ipynb` | Baseline training and comparison |
| `05_model_tuning.ipynb` | Tuning, BMI experiment, final selection, and model export |
| `06_explainability.ipynb` | Feature importance and SHAP explanations |

The trained model is included, so retraining is not required to run the application.

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/Mathu-code/Obesity-Risk-Intelligence-System.git
cd Obesity-Risk-Intelligence-System
```

### 2. Create a Virtual Environment

```bash
python -m venv .venv
```

Activate it on Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

On macOS or Linux:

```bash
source .venv/bin/activate
```

### 3. Install Dependencies

```bash
python -m pip install -r requirements.txt
```

## Running This Repository Locally

Run all commands from the project root.

### Start the Flask Backend

```bash
python -m backend.run_production
```

The default backend address is:

```text
http://127.0.0.1:5000
```

### Start the Streamlit Frontend

Open a second terminal, activate the virtual environment, and run:

```bash
python -m streamlit run frontend/app.py
```

Open the local URL printed by Streamlit, usually:

```text
http://localhost:8501
```

## Live Demo and Deployment

**Live application:** https://sm-obesity-risk-intelligence.streamlit.app/

The live demo uses the Streamlit deployment adaptation maintained in the companion repository:

[SMCodeX7/Obesity-Risk-Intelligence-System](https://github.com/SMCodeX7/Obesity-Risk-Intelligence-System)

That version uses an in-process client to reuse Flask routes inside Streamlit without starting a separate backend server.

The current Mathu-code source uses the HTTP API client and requires the separate backend described above. For the standalone deployment implementation, refer to the companion repository.

## API Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/health` | Check API availability |
| GET | `/model-info` | Retrieve model metadata and metrics |
| POST | `/predict` | Generate a prediction |
| GET | `/predictions` | Retrieve saved prediction history |
| GET | `/predictions/<id>` | Retrieve a saved assessment |
| GET | `/predictions/<id>/report` | Download its PDF report |
| DELETE | `/predictions` | Clear history when enabled |

History endpoints depend on the configured access settings.

## Configuration

| Environment variable | Purpose | Default |
|---|---|---|
| `OBESITY_API_BASE_URL` | Backend address used by the HTTP frontend client | `http://127.0.0.1:5000` |
| `OBESITY_DATABASE_PATH` | SQLite database location | `database/obesity_risk.db` |
| `OBESITY_LOG_LEVEL` | Backend logging level | `INFO` |
| `PORT` | Backend server port | `5000` |
| `OBESITY_SAVE_PREDICTIONS` | Enable assessment storage | `true` |
| `OBESITY_ENABLE_HISTORY_ACCESS` | Enable history retrieval and saved reports | `true` |
| `OBESITY_SHOW_HISTORY` | Display the History interface | `true` |
| `OBESITY_ENABLE_HISTORY_RESET` | Allow history clearing | `false` |

For example, enable history clearing locally in PowerShell with:

```powershell
$env:OBESITY_ENABLE_HISTORY_RESET = "true"
```

## Testing

Run the automated test suite from the project root:

```bash
python -m pytest tests/ -q
```

The tests cover:

- Preprocessing
- Model loading and predictions
- API input validation and error responses
- Database operations
- Prediction history and reset controls
- PDF report generation
- Frontend API communication and helper functions
- Production configuration
- Integrated prediction workflows

## Limitations

- Predictions reflect patterns learned from the development dataset.
- Reported metrics describe performance on the project's held-out test set.
- Model confidence is not a clinical certainty score.
- The application does not include user authentication; enabled history is shared.
- Local SQLite files on cloud hosting should not be relied on as permanent storage.
- SHAP explanations describe model contributions, not medical causes.

## Future Improvements

- Keep the main and deployment repositories aligned
- Pin additional runtime dependencies for reproducible builds
- Add continuous integration for automated testing
- Expand evaluation across external datasets and population groups
- Introduce persistent cloud storage if long-term history is required
- Extend the interface with additional explainability views

## License

This project is distributed under the **MIT License**. See [LICENSE](LICENSE) for details.
