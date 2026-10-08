# Part 12 - Health Workflows

## Scope

Implement documented:
- treatment
- vaccination
- mortality

## Claude Prompt

Implement health field workflows using the documented quick-action contracts.

Use cached reference data for:
- medicines
- vaccination schedules
- mortality causes

Only use disease selection if the API/reference contract supplies it.

Do not invent:
- diagnosis workflows
- withdrawal-period calculations
- medical history APIs
- vet dashboards

unless explicitly documented by the backend.

All mutations must use offline-first synchronization.

Acceptance:
- real API contract
- reference data works offline
- server validation is surfaced
- critical duplicate/conflict behavior is handled
