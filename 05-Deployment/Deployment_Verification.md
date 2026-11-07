# Deployment Verification

## 1. Purpose

This document provides a checklist for verifying deployment of the ServiceNow disease surveillance application and its external US-10 prediction API.

A complete deployment should be considered verified only after the target environment has been checked and the relevant evidence has been recorded.

## 2. Deployment status

The repository currently contains project documentation and the US-10 API documentation. A verified complete ServiceNow Update Set export and target-instance deployment evidence have not yet been supplied for this repository.

Accordingly, this document defines the verification procedure. It does not claim that a production deployment has been completed.

## 3. ServiceNow package verification

Before importing:

- [ ] Confirm the exported application package or Update Set is from the intended source instance.
- [ ] Confirm the package contains the expected scoped application components.
- [ ] Review the package for credentials, API keys, tokens, personal data, and private instance details.
- [ ] Identify required plugins, application dependencies, and environment-specific configuration.
- [ ] Record the package name, export date, source release, and owner.

During import:

- [ ] Import the package using the supported ServiceNow process.
- [ ] Preview the Update Set or package.
- [ ] Review skipped records, conflicts, and missing dependencies.
- [ ] Resolve issues before committing.
- [ ] Record the import and commit result.

After import:

- [ ] Confirm the scoped application is present.
- [ ] Confirm all five custom tables are available: Disease Case, Hospital, Laboratory Report, Investigation, and Outbreak Alert.
- [ ] Confirm application roles are present.
- [ ] Confirm ACL rules and permissions.
- [ ] Confirm forms and application navigator modules.
- [ ] Confirm Flow Designer workflows are present, active, and configured.
- [ ] Confirm outbreak alert notification behavior.
- [ ] Confirm dashboard components and reports.
- [ ] Execute the relevant test scenarios and save evidence.

## 4. US-10 API deployment verification

### Local verification

- [ ] Python environment is prepared.
- [ ] Dependencies are installed from `requirements.txt`.
- [ ] Required model artifact is present at `model/best_outbreak_risk_model.joblib`.
- [ ] API starts without model-loading errors.
- [ ] `GET /health` returns a healthy response.
- [ ] `POST /predict` accepts the synthetic sample request.
- [ ] Response contains risk level, confidence, score distribution, and feature summary.

### Remote integration verification

- [ ] API is deployed to an approved host or secured development tunnel.
- [ ] HTTPS connectivity is available.
- [ ] ServiceNow can reach the configured endpoint.
- [ ] Authentication and secrets are configured securely.
- [ ] A synthetic case request returns the expected response structure.
- [ ] ServiceNow response mapping is verified.
- [ ] Error handling is tested for unavailable service and invalid input.

A successful local API request alone does not prove remote ServiceNow integration or production deployment.

## 5. Role and workflow verification

- [ ] Hospital Staff reporting workflow is available.
- [ ] Laboratory Officer report workflow is available.
- [ ] PHO case review follows the read-only policy.
- [ ] FIO investigation create/read/update operations work and delete is restricted.
- [ ] System Administrator has the configured administrative access.
- [ ] Outbreak threshold logic works.
- [ ] Seven-day reporting-date condition works at the required boundaries.
- [ ] Existing-alert lookup prevents a duplicate matching alert.
- [ ] Alert notification behavior works.
- [ ] Dashboard metrics and charts display the expected records.

## 6. Deployment evidence

Capture and retain:

- Source and target instance release information.
- Exported package or Update Set name and version.
- Import/preview/commit result screenshots.
- Application and table verification screenshots.
- Role and ACL verification screenshots.
- Flow and notification verification screenshots.
- Dashboard verification screenshot.
- API health and prediction request/response evidence.
- Date and outcome of post-deployment tests.

Store sanitized evidence under `ScreenShots/Phase-05/`.

## 7. Rollback and recovery considerations

Before deployment, preserve the approved package and record the target environment's current state. Follow the organization's ServiceNow change and recovery process if an import introduces conflicts or unexpected behavior. Do not attempt an unreviewed production rollback based solely on this academic project document.

## 8. Deployment record

Complete this table after an actual deployment:

| Item | Recorded value |
|---|---|
| Source instance / release | To be recorded |
| Target instance / release | To be recorded |
| Package or Update Set name | To be recorded |
| Import date | To be recorded |
| Preview result | To be recorded |
| Commit result | To be recorded |
| Post-deployment test result | To be recorded |
| Verifier | To be recorded |

## 9. Related documents

- [Installation Guide](Installation_Guide.md)
- [Testing](../04-Testing-&-Validation/Testing.md)
- [Test Summary Report](../04-Testing-&-Validation/Test_Summary_Report.md)
- [Known Limitations](../04-Testing-&-Validation/Known_Limitations.md)
