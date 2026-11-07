# Project User Stories

## 1. Purpose

This document lists the twelve user stories used to organize development of the AI-Enabled Public Health Disease Surveillance and Outbreak Response Platform.

Jira was used to manage the stories and track implementation progress. The supplied Jira screenshots show US-01 to US-09 marked Done, and US-11 and US-12 marked In Progress. The project owner reports US-10 as completed and verified, but its Jira issue screenshot was not included in the supplied batch.

## 2. User story and Jira status

| ID | User story | Actor | Jira issue | Jira status shown | Project status |
|---|---|---|---|---|---|
| US-01 | Disease Case Reporting | Hospital Staff | PHDS-1 | Done | Completed and verified |
| US-02 | Laboratory Verification | Laboratory Officer | PHDS-2 | Done | Completed and verified |
| US-03 | Public Health Officer Case Review | Public Health Officer | PHDS-5 | Done | Completed and verified |
| US-04 | Field Investigation Management | Field Investigation Officer | PHDS-6 | Done | Completed and verified |
| US-05 | Outbreak Monitoring | Public Health Officer | PHDS-7 | Done | Completed and verified |
| US-06 | System Administration | System Administrator | PHDS-8 | Done | Completed and verified |
| US-07 | Time-Based Outbreak Detection | Public Health Officer | PHDS-9 | Done | Completed and verified |
| US-08 | Outbreak Alert Notifications | Public Health Officer | PHDS-10 | Done | Completed and verified |
| US-09 | Public Health Dashboard and Analytics | Public Health Officer | PHDS-11 | Done | Completed and verified |
| US-10 | AI-Based Outbreak Risk Prediction | Public Health Officer | Not supplied | Not shown | Completed and verified, per project owner |
| US-11 | AI-Assisted Case Prioritization | Public Health Officer | PHDS-13 | In Progress | In progress; not completed |
| US-12 | AI-Assisted Investigation Insights | Field Investigation Officer | PHDS-14 | In Progress | In progress; not completed |

## 3. User story details

### US-01 – Disease Case Reporting (PHDS-1)

**As a** Hospital Staff member, **I want** to report a suspected or confirmed disease case, **so that** the case can be recorded for public health surveillance.

**Completion evidence in Jira:** The Disease Case table was created and required fields were configured, including case status, severity, patient information, reporting facility, and reference fields. The completion note identifies test record `DSC0001014`.

**Jira status shown:** Done.

### US-02 – Laboratory Verification (PHDS-2)

**As a** Laboratory Officer, **I want** to review and update laboratory results for a disease case, **so that** the reported case can be verified.

**Completion evidence in Jira:** The Laboratory Report table was created with a Disease Case reference, Test Name, Test Date, Result, Verification Status, and Report Attachment fields. A report was linked to `DSC0001014` with a Positive result and Pending verification status in the recorded test.

**Jira status shown:** Done.

### US-03 – Public Health Officer Case Review (PHDS-5)

**As a** Public Health Officer, **I want** to review reported and verified disease cases, **so that** I can decide what action is required for each case.

**Completion evidence in Jira:** PHO can view disease, case status, laboratory verification status, severity, reporting date, symptom onset date, patient information, and location details. The completion note states that PHO access is read-only and the officer cannot modify case records.

**Jira status shown:** Done.

### US-04 – Investigation Management (PHDS-6)

**As a** Field Investigation Officer, **I want** to update investigation details for an assigned disease case, **so that** investigation findings can be recorded in the system.

**Completion evidence in Jira:** FIO can create and view Investigation records and update Investigation Status, Findings, Contact Tracing Information, and other relevant details. The officer can modify existing records but cannot delete them.

**Jira status shown:** Done.

### US-05 – Outbreak Monitoring (PHDS-7)

**As a** Public Health Officer, **I want** to monitor disease cases by location and time, **so that** I can identify possible outbreak situations.

**Completion evidence in Jira:** Threshold-based outbreak monitoring was configured to evaluate Disease Case records by disease name and location. When the matching case count reached the threshold of 3, the system created an Outbreak Alert containing disease name, location, case count, detection date, threshold, alert status, time window, and description. Three Dengue cases from Bhubaneswar generated alert `OUA0001001` with Case Count = 3 and Threshold = 3.

**Jira status shown:** Done.

### US-06 – User and System Management (PHDS-8)

**As an** Administrator, **I want** to manage users, roles, hospitals, and disease information, **so that** the surveillance platform remains properly configured and controlled.

**Completion evidence in Jira:** The System Administrator role was configured with full Create, Read, Write, and Delete permissions for the application's core tables: Disease Case, Hospital, Laboratory Report, Investigation, and Outbreak Alert. The completion note states that the administrator can access and manage application data and configuration.

**Jira status shown:** Done.

**Scope clarification:** This evidence supports the role and table-access configuration. It does not, by itself, establish that a separate custom user-management interface was developed.

### US-07 – Time-Based Outbreak Detection (PHDS-9)

**As a** Public Health Officer, **I want** the system to detect disease case clusters within a defined time window and location, **so that** possible outbreaks can be identified more accurately.

**Completion evidence in Jira:** The completion note records seven-day time-based outbreak detection using Disease Name, Location, and case-count threshold. It also states that the workflow creates alerts when the threshold is reached and synchronizes the Case Count of existing alerts when new cases are submitted. The workflow was tested for threshold and time-window conditions.

**Jira status shown:** Done.

### US-08 – Outbreak Alert Notification (PHDS-10)

**As a** Public Health Officer, **I want** to receive a notification when a possible outbreak is detected, **so that** I can take timely action.

**Completion evidence in Jira:** An automated Outbreak Alert Notification was configured to notify the Public Health Officers group whenever an Outbreak Alert record is inserted or updated. The notification includes alert number, disease name, affected location, case count, threshold, alert status, detection date, and description. Gmail SMTP was configured for outbound email; the notification was tested by updating a sample Outbreak Alert and verifying generation and delivery to the configured recipient.

**Jira status shown:** Done.

### US-09 – Public Health Dashboard and Analytics (PHDS-11)

**As a** Public Health Officer, **I want** to view disease surveillance information through a dashboard, **so that** I can monitor disease trends, locations, investigations, and possible outbreaks.

**Completion evidence in Jira:** A Public Health Disease Surveillance Dashboard was configured in ServiceNow Platform Analytics. The completion note lists summary visualizations for total disease cases, verified cases, active investigations, and possible outbreak alerts, plus analytical visualizations by disease, location, severity, case status, investigation status, and outbreak alert status.

**Jira status shown:** Done.

### US-10 – AI-Based Outbreak Risk Prediction

**As a** Public Health Officer, **I want** the application to obtain an ML-based outbreak risk estimate using current and historical case information, **so that** I can view a prototype risk assessment alongside surveillance information.

**Implementation evidence available:** The supplied FastAPI source implements `/health` and `/predict`, loads a persisted Logistic Regression model, derives historical and seven-day features, and returns risk level, confidence, class scores, and feature summary. The supplied local test result reports PASS with High risk and confidence 0.7193 for its synthetic sample.

**Jira status:** No US-10 Jira screenshot was included in the supplied batch. The project owner reports US-10 as completed and verified.

**Model limitation:** The model was trained using synthetic prototype surveillance data and synthetic analyst-assigned risk labels. It is not clinically or epidemiologically validated.

### US-11 – AI-Assisted Case Prioritization (PHDS-13)

**As a** Public Health Officer, **I want** disease cases to be prioritized based on severity and outbreak risk, **so that** high-priority cases can be reviewed first.

**Completion criteria recorded in Jira:** Implement an AI-assisted case prioritization mechanism using disease case severity and outbreak risk information. Configure priority levels such as Critical, High, Medium, or Normal. Display the priority with the relevant Disease Case, verify PHO visibility, and test cases with different severity and risk conditions.

**Jira status shown:** In Progress. This story is not completed.

### US-12 – AI-Assisted Investigation Insights (PHDS-14)

**As a** Field Investigation Officer, **I want** the system to analyze investigation findings and provide useful insights, **so that** important patterns can be identified more efficiently.

**Completion criteria recorded in Jira:** Develop an AI-assisted capability to analyze field findings, exposure history, and contact tracing details. Generate a useful summary or identify potential patterns such as common exposures, locations, or contact clusters. Associate the insight with the relevant investigation or disease case and verify the result using sample investigation records.

**Jira status shown:** In Progress. This story is not completed.

## 4. Jira tracking and evidence

The supplied screenshot batch includes:
- One Jira issue screenshot each for US-01 through US-05 and US-07 through US-09.
- Two screenshots of US-06 (PHDS-8).
- One screenshot each for US-11 (PHDS-13) and US-12 (PHDS-14).
- No US-10 Jira issue screenshot.

See [Jira Tracking and Evidence](Jira_Tracking.md) for the screenshot inventory and issue mapping.

## 5. Logical workflow

The stories cover disease intake, laboratory verification, PHO review, investigation, outbreak monitoring, notification, dashboard analytics, and risk prediction. US-06 provides role and administration capabilities across the application. US-11 and US-12 extend the application with AI-assisted capabilities that are currently In Progress in Jira.

This grouping describes the end-to-end solution workflow; it does not imply that stories were implemented in strict numerical order.
