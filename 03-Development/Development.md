# Development Overview

## 1. Introduction

This document summarizes the development structure of the AI-Enabled Public Health Disease Surveillance and Outbreak Response Platform. The primary application is implemented on ServiceNow, with a separate Python FastAPI service for the US-10 machine-learning prediction capability.

The project owner reports US-01 through US-10 as completed and verified. US-11 and US-12 remain pending.

## 2. ServiceNow application

**Application name:** AI Enabled Public Health Disease Surveillance and Outbreak Response Platform

The application uses ServiceNow App Engine Studio and includes the following custom tables:

| Table | Development purpose |
|---|---|
| Disease Case | Disease case intake and tracking. |
| Hospital | Hospital and reporting-facility information. |
| Laboratory Report | Laboratory results and verification linked to disease cases. |
| Investigation | Field investigation record management. |
| Outbreak Alert | Stores potential outbreak alert records. |

The application also uses forms, roles, ACLs, application navigator modules, workflow automation, notifications, and dashboard components.

## 3. Application roles

Five application roles are configured:

- Hospital Staff
- Laboratory Officer
- Public Health Officer
- Field Investigation Officer
- System Administrator

Access is governed by ServiceNow roles and ACLs. The documented policies include PHO read-only case review, FIO create/read/update access without delete, and System Administrator full CRUD access to the custom application tables.

## 4. Application navigator

The project context records these application navigator modules:

- Disease Cases
- Laboratory Reports
- Outbreak Alert
- Investigations

Additional navigation or dashboard entry points should be added here only after confirming them from the instance.

## 5. Workflow and automation

### 5.1 Outbreak Alert Monitoring

The outbreak monitoring flow evaluates disease case records for matching disease and location values and checks whether the configured threshold is reached.

US-07 adds:
- A relative reporting-date condition for the seven-day window.
- A lookup for an existing Outbreak Alert matching disease and location.
- A conditional create step that runs only when the matching alert lookup count is zero.

### 5.2 Notifications and analytics

The implemented project includes outbreak alert notifications and a Public Health dashboard. Detailed recipient configuration, notification channel, dashboard widgets, and chart names will be documented from the corresponding implementation evidence.

## 6. US-10 external ML service

US-10 is implemented as a separate FastAPI service using Python and a persisted Logistic Regression model.

### Main files

| File | Purpose |
|---|---|
| `app.py` | FastAPI application, request validation, feature engineering, and prediction endpoint. |
| `requirements.txt` | Python package dependencies. |
| `sample_request.json` | Example current-case and historical-case request. |
| `local_test_result.json` | Captured local prediction test result. |
| `start_api.bat` | Windows helper for starting the API, if included in the repository. |
| `model/best_outbreak_risk_model.joblib` | Persisted model file required by the API; not included in the supplied file set. |

The API README documents the setup commands and endpoints. The application expects the model artifact at `model/best_outbreak_risk_model.joblib`; without that file, the application raises a startup error.

### API endpoints

| Method | Endpoint | Function |
|---|---|---|
| GET | `/health` | Health check. |
| POST | `/predict` | Predict risk from a current case and historical case list. |

### Feature engineering

The API derives:
- Historical disease case count.
- Historical location case count.
- Historical disease-location case count.
- Disease cases in the last seven days.
- Disease-location cases in the last seven days.
- Severity score and reporting-date components.

### Model and output limitation

The model was trained on synthetic prototype data and synthetic analyst-assigned risk labels. It is not clinically or epidemiologically validated. The sample local response is evidence of API execution for the supplied sample, not evidence of predictive accuracy on real surveillance data.

## 7. Development status by user story

| Story | Development area | Status |
|---|---|---|
| US-01 | Disease case reporting | Completed and verified |
| US-02 | Laboratory verification | Completed and verified |
| US-03 | PHO case review | Completed and verified |
| US-04 | Field investigation | Completed and verified |
| US-05 | Outbreak monitoring | Completed and verified |
| US-06 | System administration | Completed and verified |
| US-07 | Time-based outbreak detection | Completed and verified |
| US-08 | Alert notifications | Completed and verified |
| US-09 | Dashboard and analytics | Completed and verified |
| US-10 | ML outbreak risk prediction | Completed and verified |
| US-11 | AI-assisted case prioritization | Planned |
| US-12 | AI-assisted investigation insights | Planned |

## 8. Development evidence

Screenshots and Jira evidence will be organized under the repository's `ScreenShots/` directory. Each user-story document contains an evidence section that will be completed with actual screenshot paths after the corresponding files are uploaded.

## 9. Related documentation

- [User Story Implementation](User_Story_Implementation/)
- [US-10 API README](US-10_ML_API/README.md)
- [Testing and Validation](../04-Testing-&-Validation/Testing.md)
