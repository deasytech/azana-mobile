# Quick Action - Add Birth

## Endpoint

`POST /api/v1/quick/add_birth`

## Permission

Documented permission: `animals.create`

## Payload

Documented fields:
`litter, pen_id, piglets, sex, birth_weight`

## Claude Prompt

Implement the **Add Birth** quick-action workflow for the Azana Farms Expo mobile application.

### Before Coding

Read:
- `CLAUDE.md`
- master mobile plan
- backend API documentation
- offline sync documentation
- existing authentication/reference/scanner infrastructure

Use the backend API contract exactly.

### Requirements

Create a fast field workflow that:
1. identifies/selects the required entity
2. presents only fields documented by the API
3. validates obvious required input
4. creates the documented mutation
5. queues it when offline
6. submits it through the sync infrastructure
7. displays the resulting state
8. handles accepted/rejected/conflict/failed outcomes

If the API supports immediate quick-action submission as documented, integrate it without creating a second business-logic path.

### Offline

The mutation must include:
- generated client_id
- occurred_at
- documented type
- documented payload

Do not invent payload properties.

### Errors

Use documented validation/business errors where available.

Never replace a server error with an invented explanation.

### UX

Optimize for field use:
- large controls
- minimal typing
- scan-first where useful
- clear confirmation
- clear offline state

### Acceptance

- Real documented endpoint is used.
- Payload exactly matches contract.
- Offline mutation survives restart.
- Sync engine processes it.
- Server outcomes are displayed correctly.
- No invented fields/endpoints.
- TypeScript/lint/tests pass.

Stop after this quick action.
