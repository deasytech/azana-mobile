# Part 08 - Worker Tasks

## API

`GET /api/v1/tasks`

Task completion:
`POST /api/v1/quick/complete_task`

## Claude Prompt

Build the worker task experience.

### Screens

- My Tasks
- Task Detail
- Completion flow

Use the actual documented task response:
- number
- title
- description
- category
- priority
- status
- due_on
- overdue
- requires_evidence

Do not invent additional task fields.

### Requirements

- Filter/present tasks appropriately using documented data.
- Make overdue tasks obvious.
- Show task details.
- Allow completion using the documented quick action.
- Support notes according to the contract.
- Respect offline queue behavior.
- Reflect conflict/rejection/failed states.

Do not invent evidence upload functionality unless the API contract explicitly supports it.

### Acceptance

- Task list works.
- Task details work.
- Completion uses the real API contract.
- Offline completion works.
- Errors are handled.
