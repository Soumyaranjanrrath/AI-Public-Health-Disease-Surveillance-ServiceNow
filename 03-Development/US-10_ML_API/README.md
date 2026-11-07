# US-10 Outbreak Risk Prediction API

This directory contains the external Python FastAPI service used by User Story US-10.

## Architecture

`ServiceNow Disease Case → REST/JSON → FastAPI → Logistic Regression model → prediction → ServiceNow`

The caller supplies the current case and a list of relevant historical cases. The API calculates model features and passes them to the persisted model.

## Files

| File | Description |
|---|---|
| `app.py` | FastAPI application, request models, feature engineering, and prediction endpoint. |
| `requirements.txt` | Python dependencies. |
| `sample_request.json` | Synthetic example request with current and historical cases. |
| `local_test_result.json` | Captured sample local API result. |
| `start_api.bat` | Optional Windows launcher, if included. |
| `model/best_outbreak_risk_model.joblib` | Required model artifact; it must be supplied separately. |

## Local setup (Windows)

1. Install Python 3.11 or later.
2. Open Command Prompt in this directory.
3. Create a virtual environment: `python -m venv .venv`
4. Activate it: `.venv\Scripts\activate`
5. Install dependencies: `pip install -r requirements.txt`
6. Ensure `model/best_outbreak_risk_model.joblib` exists.
7. Start the API: `python -m uvicorn app:app --reload --host 0.0.0.0 --port 8000`
8. Open `http://127.0.0.1:8000/docs`.

The app loads the model at startup and raises an error if the artifact is missing.

## Endpoints

### GET `/health`

Returns service status, model filename, and API version.

### POST `/predict`

The request body contains:
- `case`: the current Disease Case.
- `historical_cases`: historical Disease Case records supplied by the caller.

The request schema supports disease name, disease status, case status, severity, report date, patient gender, optional patient age, and location.

The API derives historical disease/location counts, disease-location counts, seven-day counts, severity score, and reporting-date features.

The response contains:
- Risk level: Low, Medium, or High.
- Confidence.
- Class score distribution.
- Feature summary.

The score distribution is calculated by applying softmax to model decision scores. It should not be treated as a clinically calibrated probability.

## Sample test evidence

The supplied local test result reports `status: PASS`, a `High` risk level, and confidence `0.7193` for the supplied synthetic request. This demonstrates execution for that sample only; it does not establish model accuracy or real-world validity.

## ServiceNow connectivity

A local address such as `127.0.0.1` cannot be reached directly by a remote ServiceNow instance. Remote integration requires an Internet-accessible HTTPS deployment or an appropriately secured development tunnel.

Do not commit tunnel credentials, API keys, passwords, ServiceNow credentials, or private instance details.

## Model limitation

The model was trained using synthetic prototype surveillance data and synthetic analyst-assigned risk labels. It has not been clinically or epidemiologically validated and must not be used for real diagnosis or public-health intervention decisions.
