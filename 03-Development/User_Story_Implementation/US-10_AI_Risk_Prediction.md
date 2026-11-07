# US-10 – AI-Based Outbreak Risk Prediction

## User story

**As a** Public Health Officer, **I want** the application to obtain an ML-based outbreak risk estimate using current and historical case information, **so that** I can view a prototype risk assessment alongside surveillance information.

## Objective

Integrate an external Python prediction service with the ServiceNow disease surveillance workflow. The service uses a trained Logistic Regression model to classify the supplied case context into Low, Medium, or High risk.

## Architecture

`ServiceNow Disease Case → REST/JSON → FastAPI → Logistic Regression model → Prediction response → ServiceNow`

The API is a separate service. It does not independently query ServiceNow; the caller supplies the current case and relevant historical records in the request.

## Technology

- Python, FastAPI, Uvicorn.
- Pandas and NumPy.
- Scikit-learn.
- Joblib for persisted model loading.
- REST/JSON communication.

## API endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/health` | Return API status, model filename, and API version. |
| POST | `/predict` | Generate a risk prediction from a current case and historical cases. |

Interactive API documentation is available at `/docs` while the local service is running.

## Request structure

The prediction request contains:
- `case`: current disease case.
- `historical_cases`: list of relevant historical disease case records.

Each case supports disease name, disease status, case status, severity, report date, patient gender, optional patient age, and location. See `sample_request.json` in the API folder for the supplied synthetic example.

## Feature engineering

The API derives:
- Historical Disease Cases.
- Historical Location Cases.
- Historical Disease-Location Cases.
- Cases Last 7 Days (Disease).
- Cases Last 7 Days (Disease-Location).
- Severity Score.
- Report Year, Month, Day, Day of Week, and Day of Year.
- Categorical case attributes, including disease, status, severity, gender, and location.

The seven-day features are calculated against the current case's report date using the historical cases supplied in the request.

## Model loading and prediction

The API loads the persisted model from:

`model/best_outbreak_risk_model.joblib`

If the artifact is missing, the API raises a startup error. The model file was not among the files supplied for this documentation task, so it must be added separately if a runnable public repository copy is intended.

The prediction endpoint:
1. Builds a feature row.
2. Calls the model's `predict()` method for the predicted class.
3. Calls `decision_function()` and applies softmax to produce the returned class score distribution.
4. Returns the risk level, confidence, probabilities, and feature summary.

The returned score distribution is derived from model decision scores using softmax. It should not automatically be interpreted as calibrated real-world probability.

## Sample local test result

The supplied `local_test_result.json` reports:

| Output | Value |
|---|---:|
| Test status | PASS |
| Risk level | High |
| Confidence | 0.7193 |
| High score | 0.7193 |
| Medium score | 0.2169 |
| Low score | 0.0638 |
| Historical disease-location cases | 3 |
| Disease-location cases in last seven days | 3 |

This confirms that the supplied sample request produced a local response. It does not establish model accuracy, clinical validity, or production readiness.

## Local setup (Windows)

The supplied API README specifies Python 3.11 or later.

1. Open Command Prompt in the API folder.
2. Create a virtual environment: `python -m venv .venv`
3. Activate it: `.venv\Scripts\activate`
4. Install dependencies: `pip install -r requirements.txt`
5. Ensure the model artifact exists at `model/best_outbreak_risk_model.joblib`.
6. Start the API: `python -m uvicorn app:app --reload --host 0.0.0.0 --port 8000`
7. Open `http://127.0.0.1:8000/docs`.

## ServiceNow connectivity

A local address such as `127.0.0.1` cannot be reached directly by a remote ServiceNow instance. Remote integration requires an Internet-accessible HTTPS host or an appropriately secured development tunnel.

Do not publish tunnel credentials, API keys, passwords, ServiceNow credentials, or private instance details.

## Important model limitation

The supplied API documentation states that the model was trained using synthetic prototype surveillance data and synthetic analyst-assigned risk labels. It has not been clinically or epidemiologically validated. It is an academic integration prototype and must not be used for real diagnosis or public-health intervention decisions.

## Evidence to attach

- API source and project structure.
- Successful `/health` response.
- Swagger `/docs` interface.
- Sample `POST /predict` request.
- Prediction response and local test result.
- ServiceNow REST integration configuration and returned prediction, if captured.

Store actual screenshots under `ScreenShots/Phase-03/` and `ScreenShots/Phase-04/`, then add their exact file links here.

## Related stories

- US-05 – Outbreak Monitoring
- US-07 – Time-Based Outbreak Detection
- US-09 – Public Health Dashboard and Analytics
- US-11 – AI-Assisted Case Prioritization (planned)
