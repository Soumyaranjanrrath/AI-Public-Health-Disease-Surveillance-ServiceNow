# Functional Requirements

## 1. Purpose

This document describes the functional requirements for the AI-Enabled Public Health Disease Surveillance and Outbreak Response Platform implemented on ServiceNow, together with the external US-10 prediction API.

The requirements are grouped by workflow area and mapped to the project user stories.

## 2. User and access management

| ID | Functional requirement | Related story |
|---|---|---|
| FR-01 | The application shall provide role-specific access for Hospital Staff, Laboratory Officer, Public Health Officer, Field Investigation Officer, and System Administrator. | US-06 |
| FR-02 | Access to application records and operations shall be controlled using ServiceNow roles and ACLs. | US-06 |
| FR-03 | The System Administrator shall be able to administer the configured application access and records according to assigned permissions. | US-06 |

## 3. Disease case reporting

| ID | Functional requirement | Related story |
|---|---|---|
| FR-04 | Authorized Hospital Staff shall be able to create disease case records. | US-01 |
| FR-05 | A disease case shall capture the configured patient, disease, severity, status, reporting date, symptom onset, location, reporting facility, and clinical-description information. | US-01 |
| FR-06 | Disease cases shall be stored in the application Disease Case table. | US-01 |

## 4. Laboratory verification

| ID | Functional requirement | Related story |
|---|---|---|
| FR-07 | Authorized Laboratory Officers shall be able to create laboratory report records. | US-02 |
| FR-08 | A laboratory report shall be associated with a disease case. | US-02 |
| FR-09 | A laboratory report shall capture configured test, result, date, verification status, and attachment information. | US-02 |

## 5. Public Health Officer case review

| ID | Functional requirement | Related story |
|---|---|---|
| FR-10 | Public Health Officers shall be able to review disease case information needed for surveillance. | US-03 |
| FR-11 | Public Health Officer access to case records shall follow the configured read-only access policy. | US-03 |

## 6. Field investigation management

| ID | Functional requirement | Related story |
|---|---|---|
| FR-12 | Authorized Field Investigation Officers shall be able to create and maintain investigation records according to their permissions. | US-04 |
| FR-13 | Investigation records shall be associated with the relevant case or surveillance work as configured in the application. | US-04 |
| FR-14 | Field Investigation Officer permissions shall prevent deletion where configured. | US-04 |

## 7. Outbreak monitoring and detection

| ID | Functional requirement | Related story |
|---|---|---|
| FR-15 | The application shall evaluate disease cases against configured disease and location matching conditions. | US-05 |
| FR-16 | The outbreak monitoring workflow shall evaluate the configured case-count threshold. | US-05 |
| FR-17 | The time-based outbreak workflow shall restrict matching cases using the configured reporting-time window. | US-07 |
| FR-18 | Before creating a new alert, the workflow shall look for an existing alert matching the configured disease and location conditions. | US-07 |
| FR-19 | The workflow shall create a new alert only when the threshold condition is met and the duplicate-prevention check finds no matching alert. | US-05, US-07 |

## 8. Outbreak alert notifications

| ID | Functional requirement | Related story |
|---|---|---|
| FR-20 | The application shall generate configured notifications when an outbreak alert is created. | US-08 |
| FR-21 | The notification shall present relevant alert information, such as disease, location, case count, threshold, and alert status, according to its configuration. | US-08 |

## 9. Dashboard and analytics

| ID | Functional requirement | Related story |
|---|---|---|
| FR-22 | The application shall provide a public health dashboard for surveillance monitoring. | US-09 |
| FR-23 | Dashboard components shall present configured case, verification, investigation, and outbreak-alert information. | US-09 |
| FR-24 | Dashboard analytics shall use the available application records and configured reports/charts. | US-09 |

## 10. AI-based outbreak risk prediction

| ID | Functional requirement | Related story |
|---|---|---|
| FR-25 | The US-10 integration shall accept current case information and historical case records through a REST/JSON API request. | US-10 |
| FR-26 | The API shall derive historical-count, seven-day-count, severity, demographic, location, and reporting-date features supported by its implementation. | US-10 |
| FR-27 | The API shall load the trained model artifact and produce a risk-level prediction. | US-10 |
| FR-28 | The prediction response shall include the risk level, confidence, class probabilities, and feature summary. | US-10 |
| FR-29 | The API shall expose a health-check endpoint. | US-10 |

## 11. Planned AI enhancements

The following are future requirements, not implemented functionality:

| ID | Planned requirement | Related story |
|---|---|---|
| FR-30 | The system may recommend a priority category for a disease case using configured case information and risk indicators. | US-11 |
| FR-31 | The system may generate AI-assisted summaries or insights from investigation information. | US-12 |

## 12. External interface requirements

### 12.1 US-10 API endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/health` | Return API and model health information. |
| POST | `/predict` | Generate an outbreak risk prediction from a current case and historical cases. |

### 12.2 Prediction request

The POST request contains:

- `case`: the current case.
- `historical_cases`: a list of relevant historical case records supplied by the caller.

The request schema and feature construction are documented in the [US-10 API README](../03-Development/US-10_ML_API/README.md).

## 13. Data requirements

The ServiceNow application uses the following custom tables:

1. Disease Case
2. Hospital
3. Laboratory Report
4. Investigation
5. Outbreak Alert

The US-10 API schema uses disease name, disease status, case status, severity, report date, patient gender, optional patient age, and location. Do not assume that every API field is identical to a ServiceNow field or that an unlisted database table exists.

## 14. Non-functional considerations

The following are design and operational considerations rather than claims of formal performance certification:

- **Security:** Use role-based access controls and protect credentials and sensitive records.
- **Reliability:** Validate API inputs and handle invalid dates and prediction errors.
- **Maintainability:** Keep implementation, testing, and deployment documentation separated.
- **Data privacy:** Use synthetic patient data in public screenshots and sample requests.
- **Integration:** Deploy the API to an appropriately secured, reachable HTTPS endpoint for remote use.
- **Model responsibility:** Treat predictions as prototype estimates, not validated public-health decisions.

## 15. Requirement status

FR-01 through FR-29 correspond to US-01 through US-10, which the project owner reports as completed and verified. FR-30 and FR-31 are planned and map to US-11 and US-12.

Detailed acceptance evidence will be added to the individual user-story and testing documentation.
