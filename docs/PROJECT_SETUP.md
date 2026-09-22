# Obesity Risk Intelligence System

## IT3051 Fundamentals of Data Mining

**Project type:** Group mini project  
**Repository:** `Obesity-Risk-Intelligence-System`  
**Primary integration branch:** `main`  
**Current scope:** Setup and Progress Evaluation 1 preparation only

## 1. Project Purpose

The project will develop an educational machine learning system that classifies a person's obesity-risk category from demographic, physical, eating-habit, and lifestyle information.

The prediction target is `NObeyesdad`. This is a **multi-class classification** problem. The system is not a medical diagnosis tool and must not provide treatment advice.

The intended users are students, researchers, and demonstration users who need to explore how lifestyle and demographic variables can be used in a data-mining classification workflow.

## 2. Dataset Proposal

### Dataset

- **Name:** Obesity Risk Dataset, Kaggle Playground Series Season 4 Episode 2
- **Source:** Kaggle
- **URL:** <https://www.kaggle.com/competitions/playground-series-s4e2/data>
- **Original research context:** The data is based on the obesity estimation dataset associated with the UCI Machine Learning Repository. The Kaggle competition version should be cited as the project download source.
- **Expected records:** 20,758 training records in the commonly distributed competition training file.
- **Expected columns:** 18 columns, including the identifier `id`, 16 predictive features, and the target `NObeyesdad`.
- **Target:** `NObeyesdad`, the obesity-risk category label.
- **Task:** Seven-class classification.

### Expected feature groups

**Numerical features:** `Age`, `Height`, `Weight`, `FCVC`, `NCP`, `CH2O`, `FAF`, `TUE`  
**Categorical features:** `Gender`, `family_history_with_overweight`, `FAVC`, `CAEC`, `SMOKE`, `SCC`, `CALC`, `MTRANS`  
**Identifier:** `id`  
**Target:** `NObeyesdad`

The exact columns, row count, data types, missing values, duplicate count, and class distribution must be verified from the downloaded file. Do not treat the expected values in this document as a replacement for inspection of the source data.

### Dataset suitability

The dataset supports the assigned scenario because it contains a clearly defined categorical target and a meaningful combination of physical, nutritional, demographic, and lifestyle predictors. It is sufficiently large for exploratory analysis, preprocessing, comparison of at least four classification algorithms, and later system integration.

### Known limitations and responsibilities

- The dataset is a public competition dataset and may contain synthetic or simulated records; findings must not be presented as population-level medical conclusions.
- The target labels should be treated as dataset categories, not as clinical diagnoses.
- `id` is an identifier and must not be used as a predictive feature unless a documented experiment justifies it; the default plan is to exclude it.
- The dataset must be shown to and approved by the instructor before EDA, preprocessing, training, or application development.
- Record the dataset version, download date, source URL, citation, and instructor validation evidence.
- Do not commit private health information, credentials, Kaggle API tokens, or unnecessary raw copies of the dataset.

## 3. Main Branch Structure

The `main` branch is the stable integration branch. Member branches should be merged into `main` through pull requests after review.

```text
Obesity-Risk-Intelligence-System/
├── backend/                 # Later: prediction service/API
├── data/
│   ├── raw/                 # Local source files; do not commit dataset contents
│   ├── interim/             # Later: temporary transformed data
│   └── processed/           # Later: approved processed datasets
├── docs/                    # Project proposal, decisions, evidence, and report material
├── frontend/                # Later: user-facing prediction interface
├── models/                  # Later: exported trained model and metadata
├── notebooks/               # Analysis notebooks, in workflow order
├── reports/                 # Later: figures, evaluation results, and report assets
├── src/                     # Reusable data, preprocessing, and modelling code
├── tests/                   # Tests for reusable code and integrated system
├── .gitignore
├── LICENSE
└── README.md
```

Only the folder structure and project documentation are being added at this setup stage. No dataset, notebook implementation, preprocessing code, model, backend, or frontend is included yet.

## 4. Four Member Branches

Create these branches from the latest `main` branch. Replace the member placeholders in the team register when the team is finalized.

| Branch | Lead owner | Initial lead area | Expected contribution |
|---|---|---|---|
| `member-1` | Member 1 | Problem and dataset lead | Leads the first draft for the assigned stage and contributes to every other stage |
| `member-2` | Member 2 | EDA and data understanding lead | Leads the first draft for the assigned stage and contributes to every other stage |
| `member-3` | Member 3 | Preprocessing and feature engineering lead | Leads the first draft for the assigned stage and contributes to every other stage |
| `member-4` | Member 4 | Integration and evidence lead | Leads the first draft for the assigned stage and contributes to every other stage |

These are lead areas, not isolated work silos. **All four members have equal responsibility for the full project.** Every member must contribute to problem understanding, dataset validation, EDA, preprocessing, model development, optimization, system testing, documentation, and presentation. The lead member coordinates the work and prepares the first draft; the other three members review it, contribute evidence, and can explain it during the viva. Members 2 and 3 must wait for instructor dataset validation before developing EDA or preprocessing outputs. Member 4 coordinates documentation and integration but does not replace technical contributions from the other members.

For every major stage, the team must record one lead, three reviewers/contributors, the files changed, and each person's contribution. No stage may be claimed as the work of only one member.

## 5. Branch Deliverables Before Evaluation 1

### `member-1`

- Problem statement and real-world scenario.
- Prediction objective and target-variable definition.
- Stakeholder and user requirements.
- Dataset proposal with name, source, URL, citation, expected dimensions, feature groups, task, suitability, limitations, and ethical considerations.
- Instructor validation evidence or a clearly marked pending-validation record.

### `member-2`

- A numbered data-understanding notebook added only after approval.
- Verified shape, columns, data types, missing values, duplicate records, identifier uniqueness, and target classes.
- Distribution and relationship visualisations with short observations.
- Class-balance analysis and data-quality findings.
- Notes identifying possible leakage risks.

### `member-3`

- A written preprocessing plan tied to observed data-quality findings.
- Decision on identifier handling.
- Numerical and categorical feature handling plan.
- Invalid-value, duplicate, missing-value, and outlier policy where justified.
- Stratified train/test split plan performed without fitting transformations on the test set.
- Feature-engineering and feature-selection decisions with reasons.

### `member-4`

- Final folder and naming convention check.
- Requirements-to-deliverables checklist.
- Dataset validation record and decision log.
- Contribution register for all four members.
- Pull-request review checklist and Evaluation 1 rehearsal checklist.
- Main-branch integration of reviewed documentation only.

## 6. Equal Full-Project Responsibilities

Each member must complete the following responsibilities, regardless of branch name:

- Read and explain the complete problem definition, dataset proposal, EDA findings, preprocessing pipeline, models, evaluation results, system architecture, limitations, and ethical considerations.
- Make a documented contribution to every major project stage.
- Review at least one other member's work at every stage and record useful feedback.
- Produce or verify evidence for decisions, including data observations, experiment results, validation records, screenshots, and test results.
- Participate in the implementation and testing of the final end-to-end system.
- Contribute to the technical report, presentation slides, system demonstration, and individual viva preparation.
- Maintain a personal contribution log with dates, branch commits, pull requests, reviews, and decisions.

### Full-project stage rotation

The following rotation gives every member a technical lead opportunity while keeping all members involved:

| Project stage | Lead for the first draft | Required contribution from the other three |
|---|---|---|
| Problem, dataset proposal, and instructor validation | Member 1 | Review scenario, dataset suitability, citation, ethics, and approval evidence |
| Data understanding and EDA | Member 2 | Reproduce checks, challenge findings, and review leakage/class-balance evidence |
| Preprocessing and feature engineering | Member 3 | Review transformations, split strategy, leakage controls, and reproducibility |
| Repository integration and Evaluation 1 evidence | Member 4 | Supply technical evidence, review checklist, and rehearse the viva |
| Model development and four-algorithm comparison | Member 1 | Each member implements or owns at least one model experiment and explains its results |
| Hyperparameter tuning and final model selection | Member 2 | Review search strategy, metrics, experiment logs, and selection justification |
| Backend service and input validation | Member 3 | Test the API, preprocessing consistency, invalid inputs, and prediction responses |
| Frontend, end-to-end testing, and user experience | Member 4 | Test the complete workflow and contribute UI, accessibility, and usability feedback |
| Technical report and final presentation | Shared rotating ownership | Every member writes, reviews, presents, and answers questions about the complete project |

The rotation is a coordination method only. It does not reduce any member's responsibility for the complete deliverable.

## 7. IT3051 Workflow Boundary

The full assignment workflow is:

1. Understand the problem scenario.
2. Identify a dataset and obtain instructor validation.
3. Perform data understanding and EDA after approval.
4. Perform preprocessing and feature engineering after approval.
5. Complete Progress Evaluation 1.
6. Develop and compare at least four suitable machine-learning algorithms.
7. Tune models and select the final model.
8. Complete Progress Evaluation 2.
9. Develop the backend service.
10. Develop the frontend and complete end-to-end integration.
11. Prepare the technical report.
12. Present and demonstrate the system.

This setup covers only Steps 1-5. Model development, hyperparameter tuning, backend development, frontend development, report production, and final presentation work are intentionally reserved for later milestones.

## 8. Shared Working Rules

- Branch from the latest `main` before starting work.
- Keep raw data local under `data/raw/`; never commit Kaggle credentials or downloaded competition files unless the team and license explicitly permit it.
- Use clear commit messages, for example `docs: add dataset proposal` or `eda: document target distribution`.
- Open a pull request into `main`; at least one other member reviews it.
- Do not silently change column names or target labels. Document every transformation.
- Use reproducible random seeds when analysis or splitting requires randomness.
- Keep notebook outputs manageable and store reusable logic in `src/` later.
- Mark unverified assumptions as `To verify` until checked against the downloaded data.
- Every member records their own contribution for individual assessment.
- Every pull request must identify the lead, reviewers, evidence produced, and any follow-up work.
- A member must not merge work they cannot explain during an individual evaluation.

## 9. Evaluation 1 Checklist

- [ ] Problem scenario and prediction objective are clear.
- [ ] Target variable and task type are explained.
- [ ] Stakeholders, inputs, outputs, and user requirements are documented.
- [ ] Dataset name, source URL, citation, context, dimensions, and features are documented.
- [ ] Dataset has instructor validation before development proceeds.
- [ ] Data types, missing values, duplicates, invalid values, outliers, and class balance are investigated.
- [ ] Potential data leakage and prevention plan are documented.
- [ ] Preprocessing and feature-engineering decisions are justified by evidence.
- [ ] No test-set information is used to fit preprocessing.
- [ ] Each member can explain the complete project and their own contribution.

## 10. Team Register

Complete this table in the first team meeting.

| Member | Name / student ID | Branch | Main responsibility | Backup responsibility |
|---|---|---|---|---|
| 1 | To complete | `member-1` | Problem and dataset lead; full-project contributor | Documentation and model review |
| 2 | To complete | `member-2` | EDA and data-understanding lead; full-project contributor | Dataset and preprocessing review |
| 3 | To complete | `member-3` | Preprocessing lead; full-project contributor | EDA and backend review |
| 4 | To complete | `member-4` | Integration and evidence lead; full-project contributor | Model and frontend review |

## 11. Citation Placeholder

Add the final citation after confirming the competition page's listed data source and license:

> Kaggle. (2024). *Playground Series Season 4, Episode 2: Obesity Risk Prediction*. Kaggle. <https://www.kaggle.com/competitions/playground-series-s4e2/data>

The team should verify the year, author or uploader, and license shown on the live Kaggle page before submitting the proposal.