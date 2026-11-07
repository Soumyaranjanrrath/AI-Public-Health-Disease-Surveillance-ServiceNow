# Installation Guide

## 1. Purpose

This guide describes the setup considerations for reviewing and recreating the AI-Enabled Public Health Disease Surveillance and Outbreak Response Platform.

The solution consists of a ServiceNow scoped application and a separate FastAPI service used by US-10. The exact installation steps depend on the exported ServiceNow application package and target instance configuration.

## 2. Prerequisites

### ServiceNow

- Access to a ServiceNow instance with permissions to install/import application artifacts.
- Access to App Engine Studio or the relevant application development tools.
- Required roles and permissions for creating or importing tables, forms, flows, ACLs, notifications, and dashboards.
- A reviewed ServiceNow application package or Update Set, when available.

### US-10 API

- Python 3.11 or later, as specified in the supplied API README.
- pip.
- The source files in `03-Development/US-10_ML_API/`.
- The persisted model artifact at `model/best_outbreak_risk_model.joblib`.

**Model artifact note:** The model file was not among the files supplied for this documentation task. The API cannot start without it. Obtain the correct artifact from the project owner or model-training workspace before attempting to run the API.

## 3. ServiceNow application setup

The repository documents the application design and implementation. It does not currently provide a verified, complete ServiceNow Update Set export. Therefore, these are preparation and installation checks, not a claim that a portable package is already available.

Before installation:

1. Identify the source and target ServiceNow instances.
2. Confirm that the target instance supports the required application features.
3. Confirm the required application scope and dependencies.
4. Obtain the reviewed application package or Update Set from the project owner.
5. Inspect its contents for credentials, tokens, personal data, and private instance configuration.
6. Confirm that all referenced tables, roles, flows, notifications, and dashboard components are included or have documented dependencies.

If an Update Set is used, follow the ServiceNow-supported import and preview process for the applicable release:

1. Import the XML into the target instance.
2. Preview the Update Set.
3. Resolve missing dependencies and conflicts.
4. Commit only after reviewing the preview results.
5. Validate the imported application components.
6. Reconfigure environment-specific endpoints, credentials, and properties securely.

Do not assume that an Update Set includes every application artifact until its contents have been inspected.

## 4. US-10 API setup (Windows)

1. Open a terminal in `03-Development/US-10_ML_API/`.
2. Create a virtual environment:

   `python -m venv .venv`

3. Activate it:

   `.venv\Scripts\activate`

4. Install packages:

   `pip install -r requirements.txt`

5. Ensure the model file exists at:

   `model/best_outbreak_risk_model.joblib`

6. Start the service:

   `python -m uvicorn app:app --reload --host 0.0.0.0 --port 8000`

7. Open the local API documentation:

   `http://127.0.0.1:8000/docs`

8. Call `GET /health` to check that the service and model loaded successfully.
9. Submit the synthetic sample request to `POST /predict`.

The supplied `start_api.bat` may be used as an alternative launcher after its contents are reviewed and the file is included in the repository.

## 5. ServiceNow-to-API connectivity

The local loopback address `127.0.0.1` is not reachable by a remote ServiceNow instance. For remote integration:

1. Deploy the API to an approved, reachable host with HTTPS, or use an appropriately secured development tunnel.
2. Configure the ServiceNow REST integration to call the approved endpoint.
3. Store credentials and tokens in an appropriate secure configuration mechanism.
4. Test the health endpoint from the integration environment.
5. Test the prediction request with synthetic records.
6. Confirm how the response fields are mapped into the ServiceNow application.

Do not commit API keys, tunnel tokens, passwords, or private instance URLs to GitHub.

## 6. Post-installation validation

- Confirm all five custom tables are available.
- Confirm the application roles and ACLs are present.
- Confirm application forms and navigator modules are accessible.
- Confirm Flow Designer workflows are active and correctly configured.
- Confirm notification behavior.
- Confirm dashboard components load and query the expected data.
- Confirm the US-10 API can load its model and answer sample requests.
- Run the role-based and functional test scenarios.

## 7. Test data and privacy

Use synthetic records for demonstrations and public screenshots. Do not import or publish real patient information in this repository.

## 8. Related documents

- [Solution Design](../02-Solution-Design/Solution_Design.md)
- [Testing](../04-Testing-&-Validation/Testing.md)
- [Deployment Verification](Deployment_Verification.md)
- [Known Limitations](../04-Testing-&-Validation/Known_Limitations.md)
