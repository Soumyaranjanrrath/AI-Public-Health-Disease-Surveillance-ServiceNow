# Business Requirements Document (BRD)

## 1. Document purpose

This document describes the business context, objectives, stakeholders, scope, and high-level requirements for the AI-Enabled Public Health Disease Surveillance and Outbreak Response Platform.

The system is an academic/portfolio project implemented using ServiceNow. Its purpose is to demonstrate a centralized workflow for disease reporting, laboratory verification, case review, field investigation, outbreak monitoring, notifications, analytics, and an external machine-learning risk prediction prototype.

## 2. Business background

Disease surveillance requires information from multiple participants. A case may be reported by hospital staff, supplemented by laboratory findings, reviewed by public health personnel, and investigated by field officers. Public health teams also need to monitor whether similar cases are being reported in the same location within a defined period.

When these activities are handled through disconnected or manual processes, it can be difficult to maintain a consistent case history, coordinate work, and identify possible clusters promptly.

The proposed platform provides a shared application and workflow structure for these activities.

## 3. Business problem

The project addresses the following process needs:

- A centralized place to register and track disease cases.
- A structured way to associate laboratory reports with cases.
- A review process for Public Health Officers.
- A record of field investigation activities.
- Automated monitoring of disease and location combinations.
- Time-based outbreak detection and duplicate-alert checks.
- Notifications and dashboards that make surveillance information easier to monitor.
- An experimental ML integration that estimates outbreak risk from current and historical case features.

These statements describe the intended problem and project scope; they are not claims that the platform has been deployed in a real public-health organization.

## 4. Project objectives

1. Implement a ServiceNow application for disease case management.
2. Support laboratory verification linked to reported cases.
3. Provide role-specific case review and investigation workflows.
4. Automate outbreak monitoring using configured conditions.
5. Apply a defined time window to outbreak detection.
6. Prevent repeated creation of an alert for an already-alerted disease-location combination.
7. Provide notifications and dashboards for public health monitoring.
8. Integrate an external FastAPI service that returns a prototype outbreak risk prediction.
9. Maintain documentation and evidence for implementation and testing.

## 5. Stakeholders and actors

| Stakeholder / actor | Interest in the system |
|---|---|
| Hospital Staff | Enter disease case information. |
| Laboratory Officer | Record and verify laboratory reports. |
| Public Health Officer | Review reported cases, monitor outbreak alerts, and view analytics. |
| Field Investigation Officer | Record and update investigation information. |
| System Administrator | Configure and maintain application access and setup. |
| Project team / developer | Design, implement, test, and document the application. |

## 6. Project scope

### 6.1 In scope

- Disease Case, Hospital, Laboratory Report, Investigation, and Outbreak Alert application data structures.
- Role-oriented application workflows.
- Disease case reporting and laboratory verification.
- Public health case review and field investigation management.
- Outbreak detection based on disease, location, reporting date, and configured threshold.
- Duplicate-alert prevention.
- Outbreak notifications.
- Public health dashboard and analytics.
- External ML API integration for prototype outbreak risk prediction.
- Testing, evidence collection, and deployment documentation.

### 6.2 Planned extensions

- US-11: AI-Assisted Case Prioritization.
- US-12: AI-Assisted Investigation Insights.

These two stories are not part of the completed implementation at the time of this document.

### 6.3 Out of scope / limitations

- Clinical diagnosis or treatment recommendations.
- Replacement of professional public-health judgment.
- A production-certified epidemiological prediction system.
- Claims of integration with real hospitals or live government surveillance systems unless separately demonstrated.
- Claims of clinical validation for the synthetic-data ML model.

## 7. High-level business requirements

| ID | Requirement |
|---|---|
| BR-01 | The system shall allow authorized hospital personnel to register disease cases. |
| BR-02 | The system shall support laboratory reports linked to disease cases. |
| BR-03 | The system shall allow authorized public health personnel to review case information. |
| BR-04 | The system shall support field investigation record management. |
| BR-05 | The system shall monitor disease cases for configured disease-location clusters. |
| BR-06 | The system shall apply a reporting-time window during outbreak monitoring. |
| BR-07 | The system shall check for an existing matching outbreak alert before creating another. |
| BR-08 | The system shall notify relevant public health personnel when configured alert conditions are met. |
| BR-09 | The system shall present surveillance information through dashboards and analytics. |
| BR-10 | The system shall integrate with an external API to obtain a prototype ML-based outbreak risk estimate. |
| BR-11 | The system shall restrict application operations according to assigned roles and access controls. |
| BR-12 | Future enhancements may support case prioritization and investigation insights. |

## 8. Business workflow

1. Hospital Staff submits a disease case.
2. A Laboratory Officer records the corresponding laboratory report and verification information.
3. A Public Health Officer reviews the case.
4. A Field Investigation Officer records investigation activities where required.
5. The outbreak monitoring workflow checks matching cases using configured disease, location, and time conditions.
6. When the configured threshold is met, the workflow checks for an existing matching alert.
7. A new outbreak alert is created only when the duplicate-prevention condition allows it.
8. Notifications and dashboards support public health monitoring.
9. For US-10, case and historical information are sent to the external prediction service, which returns a risk estimate.

## 9. Expected business benefits

- More structured disease case information.
- Better linkage between case records and laboratory reports.
- Clearer assignment of responsibilities through role-based workflows.
- Automated identification of configured disease-location clusters.
- Reduced duplicate alert creation through an explicit existence check.
- Centralized access to surveillance records and analytics.
- Demonstration of REST-based integration between ServiceNow and an external Python ML service.

These are expected benefits of the prototype workflow, not measured outcomes from a live public-health deployment.

## 10. Assumptions and dependencies

- ServiceNow platform access and permissions are available for application development.
- Application users are assigned the appropriate roles.
- Disease case and historical records contain the fields required by the workflows and API.
- Outbreak detection depends on correctly configured date, disease, location, and threshold conditions.
- US-10 depends on an accessible FastAPI endpoint and a compatible trained model file.
- The ML model and its training labels are synthetic prototype artifacts.

## 11. Risks and constraints

| Risk / constraint | Consideration |
|---|---|
| Synthetic training data | Predictions may not generalize to real-world surveillance data. |
| API availability | ServiceNow cannot reach a developer's loopback address directly; remote integration needs a reachable endpoint. |
| Data quality | Missing or inconsistent dates, disease names, or locations can affect counts and features. |
| Access configuration | Incorrect role or ACL configuration may expose or block records. |
| Alert logic | Incorrect thresholds or time filters can produce missed or excessive alerts. |
| Sensitive information | Public repository evidence must use synthetic data and exclude secrets and personal information. |

## 12. Completion status

The project owner reports US-01 through US-10 as completed and verified through the project Jira tracking and implementation work. US-11 and US-12 remain pending. Detailed test evidence and screenshots will be linked in the relevant user-story and testing documents as they are added to the repository.

## 13. Related documents

- [Functional Requirements](Functional_Requirements.md)
- [User Stories](User_Stories.md)
- [Actors and Roles](Actors_and_Roles.md)
- [Solution Design](../02-Solution-Design/Solution_Design.md)
