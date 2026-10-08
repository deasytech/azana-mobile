# Part 10 - Production Workflows

## Scope

Implement production-related mobile workflows supported by the current API contract.

Known documented quick action:
- record weight
- record feed

## Claude Prompt

Review the API documentation and implement only production workflows that are explicitly supported.

Prioritize:
- weight recording
- feed recording
- production/batch-related selection

Do not invent production endpoints.

Reuse:
- scanner
- reference data
- offline mutation queue
- reusable forms

The server remains authoritative for production business rules such as stock availability and plausibility checks.

Acceptance:
- real endpoints only
- offline support
- server outcomes shown
- no duplicated ERP business logic
