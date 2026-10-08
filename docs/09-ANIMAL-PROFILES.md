# Part 09 - Animal Profiles

## API

`GET /api/v1/animals/{code}`

Documented fields include:
- animal_number
- public_id
- sex
- category
- breed
- status
- position
- latest_weight_kg
- URL

## Claude Prompt

Implement the animal profile experience using only the documented animal lookup contract.

### Entry Points

- scanner result
- animal code lookup where supported

### Display

Show documented animal information clearly.

Provide navigation to supported actions only when their required API contracts exist.

Do not invent:
- medical history endpoints
- breeding history endpoints
- movement history endpoints
- timeline endpoints

If those capabilities are required but not documented, report the missing API contract instead.

### Acceptance

- Animal lookup works.
- Profile uses real API data.
- Loading/error/not-found states work.
- Actions do not depend on invented endpoints.
