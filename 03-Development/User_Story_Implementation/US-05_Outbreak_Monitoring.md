# US-05 – Outbreak Monitoring

## User story

**As a** Public Health Officer, **I want** the application to monitor disease cases for configured disease-location clusters, **so that** a potential outbreak can be identified when the defined case threshold is reached.

## Objective

Automate the initial threshold-based detection of possible outbreak clusters and create an Outbreak Alert record when the configured matching case count reaches the threshold.

## ServiceNow components

- Disease Case table.
- Outbreak Alert table.
- Flow Designer flow: `Outbreak Alert Monitoring`.
- Lookup Records action.
- Conditional logic and Create Record action.

## Initial detection logic

The initial flow was recorded as:

1. Trigger when a Disease Case is created.
2. Look up Disease Case records matching the trigger's Disease Name and Location.
3. Check whether the lookup count is greater than or equal to 3.
4. Create an Outbreak Alert when the threshold condition is met.

**Important distinction:** The original US-05 implementation was threshold-based and did not yet apply the seven-day reporting-date filter. The time-window enhancement belongs to US-07.

## Outbreak Alert information

The original alert mapping included:

- Disease Name from the trigger case.
- Location from the trigger case.
- Case Count from the matching-record lookup count.
- Threshold: 3.
- Alert Status: Possible Outbreak.
- Time Window field.
- Description indicating that a possible outbreak was detected based on the case threshold.
- Detection Date mapped from the trigger record's date information.

## Verification evidence from project notes

The implementation history records three matching Dengue / Bhubaneswar test cases:

- `DSC0001014`
- `DSC0001016`
- `DSC0001017`

The flow generated Outbreak Alert `OUA0001001` with a case count of 3.

The project owner reports US-05 as completed and verified.

## Evidence

- Outbreak Alert Monitoring flow: `../../../../ScreenShots/Phase-03/`
- Matching test cases and generated alert: `../../../../ScreenShots/Phase-04/`

## Known behavior before US-07

The initial threshold-only flow could generate repeated alerts when later case creation events again satisfied the threshold. The subsequent time-based story adds a matching-alert lookup before creating a new alert.

## Related stories

- US-01 – Disease Case Reporting
- US-07 – Time-Based Outbreak Detection
- US-08 – Outbreak Alert Notifications
