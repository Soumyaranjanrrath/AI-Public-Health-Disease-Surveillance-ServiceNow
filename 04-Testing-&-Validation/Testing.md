# Testing and Validation

## 1. Purpose

This document describes the testing approach for the AI-Enabled Public Health Disease Surveillance and Outbreak Response Platform. It separates application workflow testing, access-control testing, and external API testing.

The project owner reports US-01 through US-10 as completed and verified through project work and Jira tracking. The detailed execution evidence is to be linked from the corresponding user-story documents as screenshots are added.

## 2. Testing scope

Testing is organized around:

- Disease case creation and field validation.
- Laboratory report creation and case association.
- PHO case review and read-only policy.
- Field investigation record operations.
- Outbreak threshold detection.
- Seven-day reporting-time filter.
- Duplicate-alert prevention.
- Outbreak notification behavior.
- Dashboard and analytics display.
- US-10 API health check and prediction request/response.
- Role and ACL enforcement.

## 3. Test environment

| Area | Environment / component |
|---|---|
| Enterprise application | ServiceNow scoped application |
| Workflow automation | ServiceNow Flow Designer |
| Access control | ServiceNow roles and ACLs |
| External API | Local Python FastAPI service for supplied API test |
| API test interface | FastAPI Swagger UI at `/docs` |
| Tracking | Jira |
| Evidence | ServiceNow and Jira screenshots |

Instance name, browser version, API host, and deployment configuration should be recorded from the actual test session rather than inferred.

## 4. Functional test scenarios

| Test ID | Area | Scenario | Expected result |
|---|---|---|---|
| TC-01 | US-01 | Create a Disease Case using valid synthetic data. | Case record is created with entered details. |
| TC-02 | US-02 | Create a Laboratory Report linked to a Disease Case. | Report is saved and linked to the selected case. |
| TC-03 | US-03 | Impersonate PHO and open a Disease Case. | PHO can review the case under the read-only policy. |
| TC-04 | US-04 | FIO creates, reads, and updates an investigation. | Allowed operations succeed. |
| TC-05 | US-04 | FIO attempts to delete an investigation. | Delete operation is denied. |
| TC-06 | US-05 | Create at least three matching disease/location cases for the initial threshold logic. | Outbreak alert is generated when configured conditions are met. |
| TC-07 | US-07 | Evaluate records inside the configured seven-day reporting window. | Only records satisfying the date condition contribute to the lookup count. |
| TC-08 | US-07 | Evaluate an existing disease/location alert before create. | A second matching alert is not created when the existing-alert lookup returns a record. |
| TC-09 | US-08 | Create an outbreak alert satisfying notification configuration. | Configured notification behavior occurs. |
| TC-10 | US-09 | Open the Public Health dashboard with surveillance records. | Configured metrics and visualizations are displayed. |
| TC-11 | US-10 | Call `GET /health`. | API returns a healthy service response when model loading succeeds. |
| TC-12 | US-10 | Submit the supplied synthetic request to `POST /predict`. | API returns risk level, confidence, score distribution, and feature summary. |

The table describes the relevant test scenarios. Detailed actual results, execution dates, tester names, and evidence links should be copied from Jira or test screenshots as they become available.

## 5. US-10 API test evidence

The supplied `local_test_result.json` contains:

- Status: PASS.
- Risk level: High.
- Confidence: 0.7193.
- High score: 0.7193.
- Medium score: 0.2169.
- Low score: 0.0638.
- Historical disease-location cases: 3.
- Disease-location cases in the last seven days: 3.

This verifies the supplied local sample request produced a prediction response. It does not verify model accuracy or clinical validity.

## 6. Role-based access testing

Role-based access testing is documented separately in [Role-Based Access Testing](Role_Based_Access_Testing.md). The project notes record role impersonation and ACL checks, including PHO read-only case access, FIO investigation create/read/update without delete, and System Administrator full CRUD access to custom tables.

## 7. Outbreak detection test considerations

The initial US-05 flow uses disease/location matching and a threshold of three. US-07 adds the seven-day date condition and matching-alert lookup.

When recording test results, distinguish:
- Cases within the configured time window.
- Cases outside the configured time window.
- A threshold count below three.
- A threshold count equal to or above three.
- No existing matching alert.
- An existing matching disease/location alert.

Historical alerts created before duplicate prevention was added should not be treated as test evidence of the updated flow.

## 8. Evidence management

Place screenshots in the appropriate phase folders:

- `ScreenShots/Phase-03/`: implementation configuration and forms.
- `ScreenShots/Phase-04/`: test records, workflow execution, ACL checks, dashboard and API output.

Use synthetic data and mask real patient information. Each evidence image should have a clear filename and be linked from its user-story document.

## 9. Test execution status

The project owner reports US-01 through US-10 as completed and verified in Jira. This repository will add story-specific screenshots and detailed test records when supplied. US-11 and US-12 are In Progress in Jira and have no completed verification status. Their implementation and test evidence must be added after the stories are finished.

## 10. Related documents

- [Test Summary Report](Test_Summary_Report.md)
- [Role-Based Access Testing](Role_Based_Access_Testing.md)
- [Known Limitations](Known_Limitations.md)
