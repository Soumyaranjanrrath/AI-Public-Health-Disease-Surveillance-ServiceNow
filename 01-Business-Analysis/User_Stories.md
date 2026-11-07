# Project User Stories

## 1. Purpose

This document lists the twelve user stories used to organize development of the AI-Enabled Public Health Disease Surveillance and Outbreak Response Platform.

Jira was used to manage and track the stories. The project owner reports that US-01 through US-10 are completed and verified. US-11 and US-12 are pending.

## 2. User story status

| ID | Story | Actor | Status |
|---|---|---|---|
| US-01 | Disease Case Reporting | Hospital Staff | Completed and verified |
| US-02 | Laboratory Verification | Laboratory Officer | Completed and verified |
| US-03 | Public Health Officer Case Review | Public Health Officer | Completed and verified |
| US-04 | Field Investigation Management | Field Investigation Officer | Completed and verified |
| US-05 | Outbreak Monitoring | Public Health Officer | Completed and verified |
| US-06 | System Administration | System Administrator | Completed and verified |
| US-07 | Time-Based Outbreak Detection | Public Health Officer | Completed and verified |
| US-08 | Outbreak Alert Notifications | Public Health Officer | Completed and verified |
| US-09 | Public Health Dashboard and Analytics | Public Health Officer | Completed and verified |
| US-10 | AI-Based Outbreak Risk Prediction | Public Health Officer | Completed and verified |
| US-11 | AI-Assisted Case Prioritization | Public Health Officer | Planned |
| US-12 | AI-Assisted Investigation Insights | Field Investigation Officer | Planned |

## 3. User story details

### US-01 – Disease Case Reporting

**As a** Hospital Staff member,  
**I want** to register disease cases in the application,  
**So that** reported cases are stored centrally and can be reviewed by authorized public health personnel.

**Scope:** Disease Case record creation and capture of configured patient, disease, clinical, status, reporting-date, location, and reporting-facility information.

**Status:** Completed and verified, according to project Jira tracking.

### US-02 – Laboratory Verification

**As a** Laboratory Officer,  
**I want** to record laboratory reports linked to disease cases,  
**So that** test results and verification status are available in the surveillance workflow.

**Scope:** Laboratory Report records linked to a Disease Case, including configured test name, date, result, verification status, and attachment information.

**Status:** Completed and verified.

### US-03 – Public Health Officer Case Review

**As a** Public Health Officer,  
**I want** to review disease case information,  
**So that** I can assess reported cases using the available surveillance details.

**Scope:** PHO review access to relevant disease case information under the configured read-only policy.

**Status:** Completed and verified.

### US-04 – Field Investigation Management

**As a** Field Investigation Officer,  
**I want** to create and maintain investigation records,  
**So that** field investigation activities can be tracked in the application.

**Scope:** Investigation record management with permissions configured for the Field Investigation Officer role.

**Status:** Completed and verified.

### US-05 – Outbreak Monitoring

**As a** Public Health Officer,  
**I want** the application to monitor disease cases for configured disease-location clusters,  
**So that** a potential outbreak can be identified when the defined case threshold is reached.

**Scope:** Automated matching of disease and location values, evaluation of the configured case-count threshold, and creation of an Outbreak Alert when the configured conditions are satisfied.

**Status:** Completed and verified.

### US-06 – System Administration

**As a** System Administrator,  
**I want** to manage application configuration and access,  
**So that** the application can be maintained and users can perform authorized operations.

**Scope:** Application roles, access controls, and administrative permissions for configured custom tables.

**Status:** Completed and verified.

### US-07 – Time-Based Outbreak Detection

**As a** Public Health Officer,  
**I want** outbreak monitoring to consider cases reported within a defined time window and check for an existing matching alert,  
**So that** recent disease clusters can be identified without repeatedly creating the same disease-location alert.

**Scope:** Time-window condition, threshold evaluation, lookup of existing alerts, and conditional alert creation.

**Status:** Completed and verified.

### US-08 – Outbreak Alert Notifications

**As a** Public Health Officer,  
**I want** to receive notifications when an outbreak alert is generated,  
**So that** relevant alert information is communicated to the appropriate public health personnel.

**Scope:** Configured notifications associated with outbreak alert creation, including relevant disease, location, count, threshold, and status information.

**Status:** Completed and verified.

### US-09 – Public Health Dashboard and Analytics

**As a** Public Health Officer,  
**I want** a dashboard containing surveillance metrics and analytics,  
**So that** I can monitor disease cases, laboratory verification, investigations, and outbreak alerts.

**Scope:** Configured dashboard components and analytics based on application data.

**Status:** Completed and verified.

### US-10 – AI-Based Outbreak Risk Prediction

**As a** Public Health Officer,  
**I want** the application to obtain an ML-based outbreak risk estimate using current and historical case information,  
**So that** I can view a prototype risk assessment alongside surveillance information.

**Scope:** External FastAPI prediction service using a trained Logistic Regression model. The API calculates historical and seven-day features and returns Low, Medium, or High risk, confidence, class probabilities, and a feature summary.

**Status:** Completed and verified, according to the project owner. Supplied local API evidence includes a sample request and a passing prediction result.

**Limitation:** The model uses synthetic prototype data and analyst-assigned labels and is not clinically or epidemiologically validated.

### US-11 – AI-Assisted Case Prioritization

**As a** Public Health Officer,  
**I want** the system to provide an AI-assisted priority recommendation for disease cases,  
**So that** cases that may require earlier review can be identified for attention.

**Scope:** Planned enhancement. The prioritization categories, input factors, model or rules, UI behavior, and validation approach must be defined before implementation.

**Status:** Planned / not implemented.

### US-12 – AI-Assisted Investigation Insights

**As a** Field Investigation Officer,  
**I want** the system to provide AI-assisted insights from investigation information,  
**So that** investigation findings can be reviewed and summarized more efficiently.

**Scope:** Planned enhancement. The source fields, analysis method, output format, user review process, and validation approach must be defined before implementation.

**Status:** Planned / not implemented.

## 4. Story dependencies and workflow sequence

The stories follow the overall surveillance process:

`US-01 → US-02 → US-03 → US-04 → US-05 → US-07 → US-08 → US-09 → US-10`

US-06 provides the application role and administrative foundation used across the workflows. US-11 and US-12 are planned enhancements building on case and investigation data.

This sequence describes the logical process and documentation grouping; it does not imply that every story was implemented in strict chronological order.

## 5. Jira and evidence

Jira was used to track the user stories and record completion. Screenshots captured after story implementation are intended to be stored in the repository's `ScreenShots/` folders and referenced from each story's implementation document.

No Jira issue identifiers or screenshot filenames are listed here because those exact values have not yet been supplied for this document.
