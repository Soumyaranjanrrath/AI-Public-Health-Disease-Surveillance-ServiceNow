# AI-Enabled Public Health Disease Surveillance and Outbreak Response Platform

A ServiceNow-based public health surveillance platform for disease case reporting, laboratory verification, field investigations, outbreak monitoring, alert notifications, surveillance analytics, and machine-learning-assisted outbreak risk prediction.

> **Implementation status:** US-01 through US-10 are reported as completed and verified. US-11 and US-12 remain planned and have not been implemented.

## Overview

Public health surveillance depends on timely case reporting, reliable laboratory information, coordinated field investigations, and the ability to identify possible disease clusters. This project brings these activities into a centralized ServiceNow application and adds an external Python machine-learning service for outbreak risk estimation.

The application is organized around role-based workflows for hospital staff, laboratory officers, public health officers, field investigation officers, and system administrators.

## Objectives

- Centralize disease case reporting and tracking.
- Record and verify laboratory reports linked to disease cases.
- Support public health review and field investigation workflows.
- Detect potential disease clusters using disease, location, and reporting-time conditions.
- Avoid creating duplicate outbreak alerts for an existing disease-location alert.
- Notify relevant public health personnel and provide surveillance dashboards.
- Integrate an external ML prediction API to estimate outbreak risk from current and historical case information.
- Document implementation, testing, and deployment evidence.

## Implemented capabilities

- Disease case registration and management.
- Laboratory report capture and verification.
- Public Health Officer case review.
- Field investigation management.
- Threshold-based outbreak monitoring.
- Time-window-based outbreak detection.
- Duplicate outbreak-alert prevention.
- Application roles and access controls.
- Outbreak alert notifications.
- Public health dashboard and analytics.
- External FastAPI service for ML-based outbreak risk prediction.

## Planned capabilities

- **US-11 – AI-Assisted Case Prioritization:** planned; not implemented.
- **US-12 – AI-Assisted Investigation Insights:** planned; not implemented.

## Technology stack

| Area | Technology |
|---|---|
| Enterprise application platform | ServiceNow |
| Application development | ServiceNow App Engine Studio |
| Workflow automation | Flow Designer |
| Application logic | ServiceNow Business Rules |
| Access control | ServiceNow roles and ACLs |
| Notifications and analytics | ServiceNow Notifications, dashboards and reports |
| External API | Python, FastAPI |
| ML and data processing | Scikit-learn, Pandas, NumPy |
| Model persistence | Joblib |
| API communication | REST / JSON |
| Version control | Git and GitHub |
| Project tracking | Jira |

## Roles and responsibilities

| Role | Main responsibility |
|---|---|
| Hospital Staff | Submit disease case reports. |
| Laboratory Officer | Record laboratory reports and verification results. |
| Public Health Officer (PHO) | Review cases, monitor alerts, and use surveillance analytics. |
| Field Investigation Officer (FIO) | Manage field investigation records and findings. |
| System Administrator | Manage application configuration, roles, and access. |

See [Actors and Roles](01-Business-Analysis/Actors_and_Roles.md) for the role documentation.

## Application workflow

1. Hospital Staff submits a disease case.
2. A Laboratory Officer records and verifies the associated laboratory information.
3. A Public Health Officer reviews case information.
4. A Field Investigation Officer manages investigation activities.
5. Outbreak monitoring evaluates matching disease and location records.
6. The time-based workflow applies its configured reporting window and case threshold.
7. The workflow checks for an existing matching outbreak alert before creating another.
8. Alert notifications and dashboards support public health monitoring.
9. The external prediction service can evaluate a current case together with historical records and return an estimated risk level.

## US-10: machine-learning integration

US-10 uses an external Python API. The documented architecture is:

`ServiceNow Disease Case → REST/JSON → FastAPI → Logistic Regression Model → Prediction → ServiceNow`

The API accepts a current case and a list of historical cases. Its feature engineering includes historical disease counts, location counts, disease-location counts, seven-day counts, severity, and reporting-date attributes. The response contains a risk level (Low, Medium, or High), confidence, class probabilities, and a feature summary.

The supplied local test result returned a **High** risk level with **0.7193** confidence for its sample request. This is an API test result, not a claim of real-world predictive performance.

**Important limitation:** The supplied API README states that the model was trained using synthetic prototype surveillance data and synthetic analyst-assigned risk labels. It is not clinically or epidemiologically validated. The local API also requires a reachable HTTPS endpoint or appropriate development tunnel before a remote ServiceNow instance can call it; `127.0.0.1` is not directly reachable from the Internet.

See [US-10 API documentation](03-Development/US-10_ML_API/README.md) and [US-10 implementation](03-Development/User_Story_Implementation/US-10_AI_Risk_Prediction.md).

## User story status

| ID | User story | Status |
|---|---|---|
| US-01 | Disease Case Reporting | Completed and verified |
| US-02 | Laboratory Verification | Completed and verified |
| US-03 | Public Health Officer Case Review | Completed and verified |
| US-04 | Field Investigation Management | Completed and verified |
| US-05 | Outbreak Monitoring | Completed and verified |
| US-06 | System Administration | Completed and verified |
| US-07 | Time-Based Outbreak Detection | Completed and verified |
| US-08 | Outbreak Alert Notifications | Completed and verified |
| US-09 | Public Health Dashboard and Analytics | Completed and verified |
| US-10 | AI-Based Outbreak Risk Prediction | Completed and verified |
| US-11 | AI-Assisted Case Prioritization | Planned |
| US-12 | AI-Assisted Investigation Insights | Planned |

The completion status above reflects the project's Jira tracking and the status supplied by the project owner. Story-specific implementation details and evidence will be added to the corresponding documentation files.

## Repository structure

```text
AI-Public-Health-Disease-Surveillance-ServiceNow/
├── README.md
├── LICENSE
├── 01-Business-Analysis/
├── 02-Solution-Design/
├── 03-Development/
│   ├── User_Story_Implementation/
│   └── US-10_ML_API/
├── 04-Testing-&-Validation/
├── 05-Deployment/
└── ScreenShots/
    ├── Phase-01/
    ├── Phase-02/
    ├── Phase-03/
    ├── Phase-04/
    └── Phase-05/
```

## Project management and evidence

Jira is used to track the user stories and their completion. Screenshots captured during implementation and verification are intended to be organized under `ScreenShots/` and linked from the relevant documentation pages. Only evidence actually supplied and reviewed should be added to those references.

## Testing and validation

Testing documentation is maintained in [04-Testing-&-Validation](04-Testing-&-Validation/). It will cover workflow behavior, role-based access, outbreak detection and duplicate prevention, notifications, dashboard behavior, and the external prediction API. Individual test outcomes will be reported from available test evidence rather than assumed.

## Deployment

Deployment and installation notes will be maintained in [05-Deployment](05-Deployment/). Any ServiceNow Update Set shared publicly must be reviewed for credentials, tokens, private instance details, and personal or patient data.

## Known limitations and responsible use

- The ML model is a prototype trained on synthetic data and synthetic labels.
- Its outputs are not validated for diagnosis, treatment, public-health intervention, or operational outbreak decisions.
- Model confidence is not equivalent to clinical or epidemiological certainty.
- Remote ServiceNow-to-API communication requires a reachable and appropriately secured endpoint.
- US-11 and US-12 are not implemented.
- Project screenshots and test details will be added as evidence becomes available.

## Skills demonstrated

ServiceNow application development, workflow automation, Business Rules, role-based access control, ACL configuration, REST integration, Python backend development, FastAPI, machine-learning model integration, feature engineering, testing, Jira project tracking, and Git/GitHub documentation.

## Repository

[AI-Public-Health-Disease-Surveillance-ServiceNow](https://github.com/Soumyaranjanrrath/AI-Public-Health-Disease-Surveillance-ServiceNow)
