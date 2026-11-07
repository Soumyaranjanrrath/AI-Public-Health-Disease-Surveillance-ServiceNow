# US-11 – AI-Assisted Case Prioritization

## User story

**As a** Public Health Officer, **I want** the system to provide an AI-assisted priority recommendation for disease cases, **so that** cases that may require earlier review can be identified for attention.

## Status

<badge>Planned – Not implemented</badge>

The project owner has confirmed that US-11 is one of the two remaining user stories. This page documents the intended scope only; it does not claim that a model, flow, ServiceNow field, or user interface has been built.

## Proposed objective

Extend the surveillance workflow with a case-priority recommendation that can help a Public Health Officer review incoming cases in a consistent order.

## Proposed scope for design

The project story concept identifies case severity and outbreak risk as possible inputs to prioritization. Before implementation, the project team should define:

- The priority categories and their exact meaning.
- The input attributes and data quality requirements.
- Whether prioritization will use rules, a trained model, or a hybrid approach.
- How the US-10 risk output will be consumed, if applicable.
- Where the recommendation will appear on the Disease Case form or dashboard.
- Who can view, override, or update the recommendation.
- How recommendations will be logged and tested.

No specific priority labels, formula, thresholds, model, or field names are asserted here because those details have not yet been implemented or confirmed.

## Potential ServiceNow components

These are design candidates, not implemented components:

- Additional case-priority field or related recommendation record.
- Business Rule or Flow Designer orchestration.
- REST integration with an external prioritization service, if a model-based approach is selected.
- PHO-facing list or dashboard indicator.
- Audit information recording recommendation and human override.

## Acceptance criteria to define

1. A recommendation is generated only when the required input fields are available.
2. The recommendation and its rationale are visible to authorized PHO users.
3. The PHO can distinguish a system-generated recommendation from a human decision.
4. Invalid or incomplete inputs are handled without corrupting the case record.
5. The behavior is tested across representative severity and risk combinations.
6. The feature does not present an unvalidated recommendation as a medical or public-health directive.

## Testing plan (future)

- Test all defined priority categories.
- Test missing and invalid input values.
- Test interaction with US-10 risk output, if selected.
- Test role-based visibility and modification permissions.
- Test whether a human override is recorded.
- Document false-high and false-low prioritization cases.

## Evidence

No US-11 implementation screenshots or test results are available because this story has not been implemented. Add Jira planning evidence and later implementation/test screenshots when work is completed.

## Responsible-use note

Any prioritization logic must be evaluated for bias, data quality, explainability, and operational safety. A recommendation should support human review rather than replace professional judgment.

## Dependencies

- Disease Case data from US-01.
- Severity and surveillance context.
- US-10 risk prediction may be a potential input after its use is explicitly designed and verified.

## Related stories

- US-01 – Disease Case Reporting
- US-09 – Public Health Dashboard and Analytics
- US-10 – AI-Based Outbreak Risk Prediction
- US-12 – AI-Assisted Investigation Insights
