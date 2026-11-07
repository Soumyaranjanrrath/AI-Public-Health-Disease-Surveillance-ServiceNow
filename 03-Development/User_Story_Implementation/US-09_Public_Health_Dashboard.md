# US-09 – Public Health Dashboard and Analytics

## User story

**As a** Public Health Officer, **I want** a dashboard containing surveillance metrics and analytics, **so that** I can monitor disease cases, laboratory verification, investigations, and outbreak alerts.

## Objective

Provide a consolidated dashboard view of the surveillance information stored in the ServiceNow application.

## ServiceNow components

- ServiceNow dashboard.
- Configured reports and visualizations.
- Disease Case, Laboratory Report, Investigation, and Outbreak Alert data sources.
- Public Health Officer access.

## Dashboard scope

The project story scope identifies these surveillance indicators and analysis dimensions:

- Total disease cases.
- Verified cases.
- Active investigations.
- Possible outbreak alerts.
- Distribution by disease and location.
- Reporting trends over time.
- Severity distribution.
- Investigation status.

The exact widget titles, chart types, report filters, and source-table configurations should be taken from dashboard screenshots rather than inferred from this high-level list.

## Implementation summary

1. Dashboard components were configured using the application's surveillance records and reports.
2. The dashboard supports monitoring of case, verification, investigation, and alert information.
3. Public Health Officer access is used for the surveillance monitoring workflow.

## Verification

The project owner reports US-09 as completed and verified. Actual dashboard screenshots and individual widget details will be attached when project evidence is uploaded.

## Evidence to attach

- Complete dashboard overview.
- Individual chart/report configurations where useful.
- Example dashboard data using synthetic records.
- Jira completion evidence.

Suggested locations: `../../../../ScreenShots/Phase-03/` and `../../../../ScreenShots/Phase-04/`. Replace these folder references with exact relative image links once the screenshot files are added.

## Notes

Dashboard values depend on the records available in the ServiceNow instance at the time of viewing. Use synthetic data in public screenshots and avoid exposing patient-level personal information.

## Related stories

- US-03 – Public Health Officer Case Review
- US-05 – Outbreak Monitoring
- US-07 – Time-Based Outbreak Detection
- US-08 – Outbreak Alert Notifications
- US-10 – AI-Based Outbreak Risk Prediction
