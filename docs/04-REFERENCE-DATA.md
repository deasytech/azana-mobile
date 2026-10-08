# Part 04 - Reference Data

## API

`GET /api/v1/reference`

The API provides versioned offline reference lists including documented categories such as:
- pens
- locations
- stores
- feed types
- medicines
- vaccination schedules
- stock items
- mortality causes
- movement reasons
- animal categories
- quick action types

## Claude Prompt

Implement the reference-data subsystem.

### Requirements

- Fetch `/api/v1/reference`.
- Store the response locally.
- Track version/update information according to the actual response contract.
- Make reference data available offline.
- Refresh after sign-in/when online according to the API documentation.
- Avoid unnecessary network requests.
- Expose typed selectors/hooks for screens.

### Rules

Do not invent fields.

Read the actual API response contract.

Reference data is cacheable data, not mutable business state.

### Acceptance Criteria

- Reference data loads from API.
- It is available offline after a successful fetch.
- Screens can access it through a central mechanism.
- Refresh failures do not destroy the last valid cache.
- TypeScript passes.
