# US-07 – Time-Based Outbreak Detection

## User story

**As a** Public Health Officer, **I want** outbreak monitoring to consider cases reported within a defined time window and check for an existing matching alert, **so that** recent disease clusters can be identified without repeatedly creating the same disease-location alert.

## Objective

Extend the initial threshold-based outbreak monitoring flow with a reporting-date condition and duplicate-alert prevention.

## ServiceNow components

- Flow Designer flow: `Outbreak Alert Monitoring`.
- Disease Case Lookup Records action.
- Outbreak Alert Lookup Records action.
- Threshold and duplicate-prevention conditions.
- Outbreak Alert Create Record action.

## Implemented logic

The updated flow is structured as follows:

1. Trigger when a Disease Case is created.
2. Look up Disease Case records matching the trigger's Disease Name.
3. Match the trigger's Location.
4. Apply the relative reporting-date condition: Date Reported is within the configured seven-day lookback (shown in the flow condition as relative after seven days ago).
5. Check whether the first lookup count is greater than or equal to 3.
6. Look up existing Outbreak Alert records matching the trigger Disease Name and Location.
7. Check whether the existing-alert lookup count is zero.
8. Create an Outbreak Alert only when no matching alert is found.

## Alert creation

The Create Record action uses the matching Disease Case lookup count for Case Count and maps disease and location from the trigger. The alert also includes the configured threshold, status, time-window, description, and detection-date fields.

The implementation history includes a screenshot where the Time Window value in the Create Record mapping appeared as 6, despite the seven-day lookup condition. Confirm the stored mapping and correct it to the intended value before treating that field mapping as verified. The flow's seven-day date condition and the Outbreak Alert's Time Window field are separate configuration items.

## Duplicate-alert behavior

The duplicate check searches existing Outbreak Alert records matching disease and location. Alert creation is nested under the condition that the matching-alert lookup count equals zero.

This prevents another alert for a disease-location combination when a matching alert already exists. It does not automatically remove duplicate alerts created by earlier versions of the flow.

## Verification

The project owner reports US-07 as completed and verified. Earlier test data included multiple outbreak alert records created before duplicate prevention was added. Those historical records should not be described as evidence that the updated duplicate-prevention branch failed.

The exact test record IDs for inside-window, outside-window, and existing-alert scenarios should be linked from the Jira screenshots when supplied.

## Evidence checklist

Add actual screenshots for:

1. Complete Outbreak Alert Monitoring flow.
2. Disease Case lookup conditions showing disease and location matching.
3. Seven-day relative Date Reported condition.
4. Threshold condition (lookup count greater than or equal to 3).
5. Existing Outbreak Alert lookup conditions.
6. Duplicate-prevention condition (existing-alert lookup count equals zero).
7. Create Outbreak Alert field mappings.
8. Generated alert and test result.
9. Inside-window and outside-window test evidence.

Place screenshots under `ScreenShots/Phase-03/` and `ScreenShots/Phase-04/` and update this document with their exact filenames.

## Configuration caution

A relative condition such as "after seven days ago" is evaluated relative to the flow execution time according to the platform's relative-date behavior. Do not claim it is anchored to the trigger record's reporting timestamp unless that behavior has been separately demonstrated.

## Related stories

- US-05 – Outbreak Monitoring
- US-08 – Outbreak Alert Notifications
