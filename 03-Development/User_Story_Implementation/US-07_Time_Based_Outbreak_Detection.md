# US-07 – Time-Based Outbreak Detection

## Jira reference

**Issue:** PHDS-9  
**Status shown:** Done

## User story

**As a** Public Health Officer, **I want** the system to detect disease case clusters within a defined time window and location, **so that** possible outbreaks can be identified more accurately.

## Objective

Extend the initial threshold-based outbreak monitoring flow with a reporting-date condition and logic to maintain the case count of an existing alert when new matching cases are reported.

## ServiceNow components

- Flow Designer flow: `Outbreak Alert Monitoring`.
- Disease Case Lookup Records action.
- Outbreak Alert Lookup Records action.
- Threshold and duplicate-alert conditions.
- Create Record and existing-alert update logic.

## Implemented logic described by the project evidence

1. Trigger when a Disease Case is created.
2. Look up Disease Case records matching the trigger's Disease Name and Location.
3. Apply the configured seven-day relative Date Reported condition.
4. Check whether the matching case count reaches the configured threshold of 3.
5. Look up existing Outbreak Alert records matching the disease and location.
6. If no matching alert exists, create a new Outbreak Alert.
7. If a matching alert already exists, synchronize/update the Case Count on that existing alert when new matching cases are submitted.

The Jira completion note explicitly records both alert creation when the threshold is reached and synchronization of the case count on existing alerts.

## Outbreak Alert information

The original Create Record mapping included disease name, location, case count, threshold, alert status, time-window value, description, and detection-date information.

The implementation history includes a screenshot where the Time Window value in the Create Record mapping appeared as 6, while the lookup condition was set to seven days. Verify the stored Time Window field mapping separately. The seven-day lookup condition and the stored alert Time Window field are separate configuration items.

## Verification

Jira issue PHDS-9 is shown as Done. Its completion note states that the seven-day detection flow was tested successfully, including threshold and time-window conditions.

The project history also records earlier alert records generated before duplicate-alert prevention was added. Historical duplicates should not be treated as evidence that the updated branch failed.

## Evidence

- Jira completion evidence: `../../../../ScreenShots/Phase-01/Jira_User_Stories/Jira_US-07_PHDS-9.png`
- Flow configuration and seven-day filter: `../../../../ScreenShots/Phase-03/`
- Threshold, alert creation, and case-count synchronization tests: `../../../../ScreenShots/Phase-04/`

Replace folder references with exact filenames when the ServiceNow screenshots are uploaded.

## Configuration caution

A relative condition such as "Date Reported relative after seven days ago" is evaluated according to the platform's relative-date behavior. Do not claim it is anchored to the trigger record's Date Reported value unless that has been independently demonstrated.

## Related stories

- US-05 – Outbreak Monitoring
- US-08 – Outbreak Alert Notifications
