# Part 06 - Scanner

## API

`GET /api/v1/scan/{code}`

The documented scan response may match:
- animal
- pen
- production_batch
- item
- litter
- task

## Claude Prompt

Implement a reusable barcode/QR scanning workflow for the Expo app.

### Requirements

- Request camera permission correctly.
- Provide a clear scanning UI.
- Detect a code.
- Prevent duplicate rapid scans.
- Call `/api/v1/scan/{code}`.
- Display the documented result.
- Route to the appropriate supported workflow.
- Handle not-found and API errors.
- Work correctly with intermittent connectivity.

Do not invent offline scan lookup behavior if the scanned code cannot be resolved from local cached data.

The scanner must be reusable by later quick-action screens.

### Acceptance

- Camera permission flow works.
- Code can be scanned.
- Real API lookup is performed.
- Result is displayed correctly.
- Errors are understandable.
- Scanner can be reused.
