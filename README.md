# AI-Enabled Public Health Disease Surveillance and Outbreak Response Platform

A ServiceNow-based public health surveillance platform for disease case reporting, laboratory verification, field investigations, outbreak monitoring, alert notifications, surveillance analytics, and machine-learning-assisted outbreak risk prediction.

> **Implementation status:** US-01 through US-10 are reported as completed and verified. US-11 and US-12 are currently **In Progress** in Jira and are not yet completed.

## Overview

Public health surveillance depends on timely case reporting, reliable laboratory information, coordinated field investigations, and the ability to identify possible disease clusters. This project brings these activities into a centralized ServiceNow application and adds an external Python machine-learning service for outbreak risk estimation.

The application is organized around role-based workflows for Hospital Staff, Laboratory Officers, Public Health Officers, Field Investigation Officers, and System Administrators.

## Objectives

- Centralize disease case reporting and tracking.
- Record and verify laboratory reports linked to disease cases.
- Support public health case review and field investigation workflows.
- Detect potential disease clusters using disease, location, and reporting-time conditions.
- Prevent repeated alert insertion by maintaining the case count of an existing matching alert.
- Notify relevant public health personnel and provide surveillance dashboards.
- Integrate an external ML prediction API to estimate outbreak risk from current and historical case information.
- Extend the system with AI-assisted case prioritization and investigation insights.

## Implemented capabilities

- Disease case registration and management.
- Laboratory report capture and verification.
- Public Health Officer case review with read-only case access.
- Field investigation management with create/read/update permissions and restricted deletion.
- Threshold-based outbreak monitoring.
- Time-window-based outbreak detection and existing-alert case-count synchronization.
- Outbreak alert notifications to the configured Public Health Officer group.
- Public Health dashboard and analytics.
- External FastAPI service for ML-based outbreak risk prediction.
- Application roles and ACL-based access control.

## In-progress capabilities

- **US-11 – AI-Assisted Case Prioritization:** Jira status In Progress; not yet completed.
- **US-12 – AI-Assisted Investigation Insights:** Jira status In Progress; not yet completed.

## Technology stack

| Area | Technology |
|---|---|
| Enterprise application platform | ServiceNow |
| Application development | ServiceNow App Engine Studio |
| Workflow automation | Flow Designer |
| Application logic | ServiceNow Business Rules |
| Access control | ServiceNow roles and ACLs |
| Notifications and analytics | ServiceNow Notifications and Platform Analytics |
| External API | Python, FastAPI |
| ML and data processing | Scikit-learn, Pandas, NumPy |
| Model persistence | Joblib |
| API communication | REST / JSON |
| Outbound email in US-08 | Gmail SMTP configuration |
| Version control | Git and GitHub |
| Project tracking | Jira |

## User roles

| Role | Main responsibility |
|---|---|
| Hospital Staff | Submit disease case reports. |
| Laboratory Officer | Record laboratory reports and verification results. |
| Public Health Officer (PHO) | Review cases, monitor alerts, receive notifications, and use surveillance analytics. |
| Field Investigation Officer (FIO) | Manage field investigation records and findings. |
| System Administrator | Manage application configuration, roles, and access. |

## Application workflow

1. Hospital Staff submits a disease case.
2. A Laboratory Officer records and verifies the associated laboratory information.
3. A Public Health Officer reviews case information.
4. A Field Investigation Officer manages investigation activities.
5. Outbreak monitoring evaluates matching disease and location records.
6. The time-based workflow applies its configured reporting window and case threshold.
7. If a matching alert already exists, the workflow synchronizes its case count; otherwise it creates a new alert when the conditions are met.
8. Alert notifications are sent to the configured Public Health Officer group.
9. Dashboards provide surveillance information and analytics.
10. The external prediction service evaluates a current case together with historical records and returns an estimated risk level.

## US-10: machine-learning integration

US-10 uses an external Python API. The documented architecture is:

`ServiceNow Disease Case → REST/JSON → FastAPI → Logistic Regression Model → Prediction → ServiceNow`

The API accepts a current case and a list of historical cases. It derives features including historical disease counts, location counts, disease-location combinations, seven-day counts, severity, and reporting-date attributes. The response contains a risk level (Low, Medium, or High), confidence, class scores, and a feature summary.

The supplied local test result returned a **High** risk level with **0.7193** confidence for its sample request. This is an API test result, not a claim of real-world predictive performance.

**Important limitation:** The supplied API README states that the model was trained using synthetic prototype surveillance data and synthetic analyst-assigned risk labels. It is not clinically or epidemiologically validated. The local API also requires a reachable HTTPS endpoint or appropriate development tunnel before a remote ServiceNow instance can call it; `127.0.0.1` is not directly reachable from the Internet.

See [US-10 API documentation](03-Development/US-10_ML_API/README.md) and [US-10 implementation](03-Development/User_Story_Implementation/US-10_AI_Risk_Prediction.md).

## User story and Jira status

| User Story | Jira issue | Jira status shown | Project status |
|---|---|---|---|
| US-01 – Disease Case Reporting | PHDS-1 | Done | Completed and verified |
| US-02 – Laboratory Verification | PHDS-2 | Done | Completed and verified |
| US-03 – PHO Case Review | PHDS-5 | Done | Completed and verified |
| US-04 – Field Investigation Management | PHDS-6 | Done | Completed and verified |
| US-05 – Outbreak Monitoring | PHDS-7 | Done | Completed and verified |
| US-06 – System Administration | PHDS-8 | Done | Completed and verified |
| US-07 – Time-Based Outbreak Detection | PHDS-9 | Done | Completed and verified |
| US-08 – Outbreak Alert Notifications | PHDS-10 | Done | Completed and verified |
| US-09 – Public Health Dashboard and Analytics | PHDS-11 | Done | Completed and verified |
| US-10 – AI-Based Outbreak Risk Prediction | Not visible in supplied Jira screenshots | To be confirmed | Completed and verified, per project owner |
| US-11 – AI-Assisted Case Prioritization | PHDS-13 | In Progress | In progress; not completed |
| US-12 – AI-Assisted Investigation Insights | PHDS-14 | In Progress | In progress; not completed |

See [Jira Tracking and Evidence](01-Business-Analysis/Jira_Tracking.md) for screenshot mapping and the observed issue details.

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

Jira is used to manage and track the project user stories. The supplied screenshots show the Jira issue keys and workflow status for US-01 to US-09, US-11, and US-12. Two supplied images show the US-06 issue. A Jira screenshot for US-10 was not present in the supplied batch.

The Jira screenshots are evidence of issue descriptions, workflow statuses, and completion notes. They do not replace ServiceNow implementation screenshots or independent test logs.

## Testing and validation

Testing documentation is maintained in [04-Testing-&-Validation](04-Testing-&-Validation/). It covers workflow behavior, role-based access, outbreak detection and case-count synchronization, notifications, dashboard behavior, and the external prediction API. Detailed results are reported from available project evidence rather than assumed.

## Deployment

Deployment and installation notes are maintained in [05-Deployment](05-Deployment/). A ServiceNow Update Set must be reviewed for secrets, personal data, and private instance details before any public release.

## Known limitations and responsible use

- The ML model uses synthetic prototype data and analyst-assigned labels.
- Its outputs are not validated for clinical or epidemiological decision-making.
- Model confidence is not equivalent to clinical or epidemiological certainty.
- Remote ServiceNow-to-API communication requires a reachable, appropriately secured HTTPS endpoint.
- US-11 and US-12 are in progress and are not completed.
- Jira screenshots document project tracking; corresponding ServiceNow implementation and test evidence should also be included.

## Skills demonstrated

ServiceNow application development, workflow automation, Business Rules, role-based access control, ACL configuration, REST integration, Python backend development, FastAPI, machine-learning model integration, feature engineering, testing, Jira project tracking, and Git/GitHub documentation.

## Repository

[AI-Public-Health-Disease-Surveillance-ServiceNow](https://github.com/Soumyaranjanrrath/AI-Public-Health-Disease-Surveillance-ServiceNow)
