# Known Limitations

## 1. Purpose

This document records known limitations and constraints of the academic prototype. It distinguishes confirmed limitations from items that should be rechecked against the current ServiceNow configuration.

## 2. Machine-learning model

### Synthetic training data

The supplied US-10 API README states that the model was trained using synthetic prototype surveillance data and synthetic analyst-assigned risk labels.

### No clinical or epidemiological validation

The model has not been clinically or epidemiologically validated. Its output must not be used for real diagnosis, treatment, or public-health intervention decisions.

### Returned confidence and class scores

The API uses the model's `decision_function()` output and applies softmax to create a class score distribution. These values are not necessarily calibrated probabilities and should not be described as real-world predictive certainty.

### Missing model artifact in the supplied file set

The supplied `app.py` loads `model/best_outbreak_risk_model.joblib` at startup and raises an error if the file is missing. That model file was not among the files supplied for this documentation task. A runnable public repository copy requires the artifact or a documented secure method to obtain it.

## 3. API connectivity

The local API uses a loopback address for development. A remote ServiceNow instance cannot directly call `127.0.0.1` on a developer's computer. Remote integration requires a reachable HTTPS deployment or an appropriately secured development tunnel.

Do not commit tunnel tokens, API keys, or passwords.

## 4. Outbreak monitoring configuration

### Relative date behavior

The US-07 flow condition was recorded as Date Reported relative after seven days ago. Relative-date conditions should be understood in relation to the flow execution time unless another reference point is explicitly implemented and demonstrated. Do not claim that the filter is anchored to the trigger record's report date without evidence.

### Separate Time Window field mapping

The project history includes a screenshot where the Time Window value in the Create Outbreak Alert action appeared as 6, while the lookup condition was set to seven days. The Time Window field mapping should be checked and corrected to the intended value if required. The date filter and stored alert field are separate configuration items.

### Historical duplicate alerts

Earlier versions of the flow created multiple alerts for some disease-location combinations before duplicate prevention was added. The later lookup-and-condition logic prevents new duplicates under its configured matching conditions, but it does not automatically clean up historical alert records.

## 5. Scope limitations

- US-11 – AI-Assisted Case Prioritization is In Progress in Jira and is not yet completed or verified.
- US-12 – AI-Assisted Investigation Insights is In Progress in Jira and is not yet completed or verified.
- The project does not claim production deployment in a real hospital or public-health organization.
- Exact ServiceNow notification configuration and dashboard widget details should be supported by screenshots before being described at a lower implementation level.

## 6. Data and privacy

- Public examples and screenshots should use synthetic patient information.
- Patient names, identifiers, contact details, and sensitive case information must not be published.
- Review ServiceNow Update Set XML and application exports for credentials, tokens, private instance details, and sensitive records.

## 7. Further validation recommended

- Verify the current US-07 Time Window field mapping.
- Test records just inside and outside the seven-day boundary.
- Verify duplicate prevention with an existing alert.
- Re-test roles and ACLs after configuration changes.
- Perform end-to-end ServiceNow-to-API testing using a secured reachable endpoint.
- Evaluate the ML model with appropriately governed, representative, validated data before any real-world use.

## 8. Related documents

- [US-07 – Time-Based Outbreak Detection](../03-Development/User_Story_Implementation/US-07_Time_Based_Outbreak_Detection.md)
- [US-10 – AI-Based Outbreak Risk Prediction](../03-Development/User_Story_Implementation/US-10_AI_Risk_Prediction.md)
- [Testing](Testing.md)
