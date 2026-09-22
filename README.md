# Obesity Risk Intelligence System

## IT3051 Fundamentals of Data Mining - Group Project Plan

This repository contains the planned structure and coordination guide for a four-member data-mining project. The project will develop an educational system that classifies obesity-risk categories from demographic, physical, eating-habit, and lifestyle information.

> This project is for educational and research purposes. Predictions are dataset classifications, not medical diagnoses or treatment recommendations.

## Project Status

The repository is currently at the setup and planning stage. The dataset must be validated by the instructor before the team performs EDA, preprocessing, model training, or system development.

Completed in this setup:

- Main repository structure.
- Four equal member branches.
- Dataset proposal details.
- Full-project responsibility plan.
- Evaluation 1 workflow and checklist.

Not started yet:

- Dataset download and verification.
- EDA notebooks.
- Preprocessing and feature engineering.
- Model training or tuning.
- Backend and frontend implementation.
- Final report and presentation materials.

## Dataset

The proposed dataset is the Kaggle Playground Series Season 4 Episode 2 obesity-risk dataset.

- **Dataset URL:** <https://www.kaggle.com/competitions/playground-series-s4e2/data>
- **Task:** Seven-class multi-class classification.
- **Target:** `NObeyesdad`.
- **Expected training records:** 20,758.
- **Expected columns:** 18, including `id`, 16 predictive features, and `NObeyesdad`.

Expected numerical features:

`Age`, `Height`, `Weight`, `FCVC`, `NCP`, `CH2O`, `FAF`, `TUE`

Expected categorical features:

`Gender`, `family_history_with_overweight`, `FAVC`, `CAEC`, `SMOKE`, `SCC`, `CALC`, `MTRANS`

The team must verify the actual row count, columns, data types, missing values, duplicates, invalid values, and target distribution after instructor approval. The identifier `id` will normally be excluded from predictive modelling because it identifies records rather than describing the subject.

The team must record the dataset version, download date, source, citation, license, and instructor validation evidence. Raw data and Kaggle credentials must not be committed to Git.

## Main Branch Structure

```text
Obesity-Risk-Intelligence-System/
├── backend/                 # Later: prediction API/service
├── data/
│   ├── raw/                 # Local source dataset; not committed
│   ├── interim/             # Temporary transformed data
│   └── processed/           # Approved processed data
├── docs/                    # Setup plan, decisions, evidence, and report material
├── frontend/                # Later: user-facing prediction interface
├── models/                  # Later: trained model and metadata
├── notebooks/               # Ordered analysis notebooks
├── reports/                 # Figures, results, and report assets
├── src/                     # Reusable data and machine-learning code
├── tests/                   # Unit and integration tests
├── .gitignore
├── LICENSE
└── README.md
```

The detailed coordination document is [docs/PROJECT_SETUP.md](docs/PROJECT_SETUP.md).

## Equal Member Branches

All four branches represent equal full-project contributors. The lead descriptions below identify who prepares the first draft or coordinates a stage; they do not limit the other members' responsibilities.

| Branch | Member | Coordination lead |
|---|---|---|
| `member-1` | Member 1 | Problem definition, dataset proposal, and later model comparison |
| `member-2` | Member 2 | Data understanding, EDA, and later model tuning |
| `member-3` | Member 3 | Preprocessing, feature engineering, and later backend work |
| `member-4` | Member 4 | Integration, evidence, frontend, and testing |

Every member must contribute to every project stage, review other members' work, participate in testing, contribute to the report and presentation, and understand the complete project for individual evaluation.

## Full Project Workflow

### Stage 1: Problem understanding

- Define the real-world obesity-risk classification scenario.
- Define the prediction objective and `NObeyesdad` target.
- Identify users, stakeholders, decisions, inputs, and outputs.
- Document the educational and non-clinical scope of the system.

### Stage 2: Dataset identification and validation

- Prepare the dataset proposal with source, URL, citation, context, dimensions, features, target, task type, suitability, quality observations, limitations, ethics, privacy, licensing, and accessibility considerations.
- Obtain instructor validation before continuing.
- Keep rejected or unverified dataset decisions documented.

### Stage 3: Data understanding and EDA

- Inspect structure, variable meanings, types, distributions, and relationships.
- Check missing values, duplicates, identifiers, invalid values, outliers, and unusual observations.
- Examine class balance and create relevant visualisations.
- Identify leakage risks and record observations that affect preprocessing.

### Stage 4: Preprocessing and feature engineering

- Handle missing, duplicate, invalid, and justified outlier cases.
- Encode categorical variables and scale numerical variables when required.
- Decide how `id` is handled.
- Engineer or select features only when supported by evidence.
- Separate training and test data correctly and fit transformations only on training data.

### Stage 5: Progress Evaluation 1

Each member must be able to explain the scenario, dataset, EDA findings, data-quality issues, preprocessing decisions, feature engineering, leakage prevention, and personal contribution.

### Stage 6: Model development

- Implement and compare at least four suitable machine-learning algorithms.
- Use an appropriate validation strategy and classification metrics.
- Record experiments, results, assumptions, and observations.

### Stage 7: Model optimization

- Tune suitable models using a documented search strategy.
- Compare tuned models with baselines.
- Investigate feature and modelling improvements.
- Select and justify the final model.

### Stage 8: Progress Evaluation 2

Each member must explain algorithm selection, validation, metrics, tuning, model comparison, interpretation, final selection, and personal contribution.

### Stage 9: Backend development

- Load the final model and preprocessing pipeline.
- Validate inputs and return meaningful predictions.
- Apply exactly the preprocessing used during training.
- Handle missing and invalid input safely.

### Stage 10: Frontend and user experience

- Provide clear input controls and validation.
- Display the prediction and supporting result information clearly.
- Connect frontend and backend into a complete workflow.
- Keep the interface understandable for non-technical users.

### Stage 11: Technical report

The report must cover the problem, stakeholders, dataset and validation, EDA, cleaning, preprocessing, feature engineering, algorithms, evaluation, tuning, final model, architecture, implementation, testing, limitations, future work, and individual/group contributions.

### Stage 12: Final presentation and demonstration

Present the business problem, solution, findings, predictions, decision support, evidence-based recommendations, and working system in language suitable for non-technical stakeholders. Every member must present and answer questions.

## Full-Project Responsibility Rotation

| Stage | First-draft or coordination lead | Other members |
|---|---|---|
| Problem and dataset validation | Member 1 | Review and contribute scenario, source, suitability, ethics, and approval evidence |
| EDA and data understanding | Member 2 | Reproduce checks, review findings, and challenge leakage/class-balance conclusions |
| Preprocessing and feature engineering | Member 3 | Review transformations, split strategy, leakage controls, and reproducibility |
| Integration and Evaluation 1 evidence | Member 4 | Supply technical evidence, review the checklist, and rehearse the viva |
| Four-model comparison | Member 1 | Each member owns or implements at least one model experiment |
| Hyperparameter tuning and final selection | Member 2 | Review search strategy, metrics, experiment logs, and selection reasoning |
| Backend and input validation | Member 3 | Test API behavior, preprocessing consistency, errors, and predictions |
| Frontend and end-to-end testing | Member 4 | Test the complete workflow and provide usability and accessibility feedback |
| Report and final presentation | Shared | Every member writes, reviews, presents, and explains the complete project |

For each stage, record the lead, reviewers, files changed, evidence produced, and individual contributions. No stage belongs exclusively to one member.

## Git Workflow

1. Create each member branch from the latest `main`.
2. Work only on the branch assigned to that member.
3. Use clear commits such as `docs: add dataset proposal` or `eda: inspect target distribution`.
4. Open a pull request into `main` for every completed contribution.
5. Obtain at least one review before merging.
6. Keep `main` stable and merge only reviewed work.
7. Do not merge work that the author cannot explain in an individual evaluation.

## Evaluation 1 Checklist

- [ ] Problem scenario and prediction objective are clear.
- [ ] Target variable and classification task are explained.
- [ ] Stakeholders, user requirements, inputs, and outputs are documented.
- [ ] Dataset source, URL, citation, context, dimensions, and feature groups are documented.
- [ ] Instructor validation is recorded before EDA or preprocessing work.
- [ ] Data types, missing values, duplicates, invalid values, outliers, and class balance are investigated.
- [ ] Leakage risks and prevention are documented.
- [ ] Preprocessing and feature-engineering decisions are justified by evidence.
- [ ] Test-set information is not used to fit preprocessing.
- [ ] Every member can explain the whole project and their own contribution.

## Team Register

Complete this table when the team is finalized.

| Member | Name / student ID | Branch | Lead area | Backup/review area |
|---|---|---|---|---|
| 1 | To complete | `member-1` | Problem and dataset | Models and documentation |
| 2 | To complete | `member-2` | EDA and data understanding | Dataset and preprocessing |
| 3 | To complete | `member-3` | Preprocessing | EDA and backend |
| 4 | To complete | `member-4` | Integration and evidence | Models and frontend |

## Citation Placeholder

Verify the author, year, and license shown on the live Kaggle page before final submission:

> Kaggle. (2024). *Playground Series Season 4, Episode 2: Obesity Risk Prediction*. Kaggle. <https://www.kaggle.com/competitions/playground-series-s4e2/data>

## Related Documentation

- [Full project setup and branch guide](docs/PROJECT_SETUP.md)
- [IT3051 assignment source document](docs/PROJECT_SETUP.md#7-it3051-workflow-boundary)