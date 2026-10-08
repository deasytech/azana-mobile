# Part 11 - Breeding Workflows

## Scope

Implement documented breeding field workflows:
- breeding service
- farrowing
- weaning

## Claude Prompt

Build the breeding mobile workflows using the exact API contract.

Use:
- `record_service`
- `record_farrowing`
- `record_weaning`

Respect documented identifiers and payload fields.

Do not invent genealogy/history endpoints.

Use reference data where documented.

Each operation must work through the offline mutation engine.

The app should clearly distinguish:
- queued
- syncing
- accepted
- rejected
- conflict
- failed

Acceptance:
- all three documented workflows work
- payloads match contract
- offline queue works
- validation is clear
- no invented backend behavior
