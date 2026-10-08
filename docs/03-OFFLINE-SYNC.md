# Part 03 - Offline Storage and Sync Engine

## Objective

Build the core offline-first infrastructure before implementing the majority of field workflows.

## API Contract

`POST /api/v1/sync/push`

Request:
- device_id
- mutations
- each mutation contains:
  - client_id
  - type
  - occurred_at
  - payload

The API processes mutations in sent order and provides an outcome for each mutation.

Outcomes:
- accepted
- rejected
- conflict
- failed

Also documented:
- `GET /sync/status`
- `GET /sync/mutations/{client_id}`

## Claude Prompt

Implement the Azana Farms offline-first synchronization engine.

First inspect the existing project and authentication foundation.

### Build

1. Local persistence layer.
2. Mutation model.
3. Mutation queue.
4. Client UUID generation.
5. Event timestamp handling.
6. Queue status model.
7. Network connectivity monitoring.
8. Sync manager.
9. Ordered sending.
10. Batch size support up to the documented API limit.
11. Retry handling.
12. Accepted handling.
13. Rejected handling.
14. Conflict handling.
15. Failed handling.
16. Sync status observable by UI.

### Important

Do not assume AsyncStorage is sufficient for the complete queue without evaluating requirements.

Use the simplest robust local persistence solution compatible with the initialized Expo project.

Do not create fake synchronization.

### Required behavior

Accepted:
- mark mutation synchronized/remove from active queue.

Rejected:
- retain history
- expose server message
- do not automatically resend unchanged data.

Conflict:
- retain conflict state
- do not blindly resend.

Failed:
- keep queued
- retry.

Resends must be safe because the backend uses `client_id` for exactly-once idempotency.

### Acceptance Criteria

- A mutation can be created offline.
- It survives app restart.
- It receives a client UUID.
- It records occurred_at.
- It enters the queue.
- Queue can be inspected.
- When online, queue sends in order.
- Results are persisted.
- Failed requests retry.
- Rejected/conflict mutations are not blindly retried.
- Sync status is available to the UI.
- Tests cover the critical state transitions.

Stop after the sync engine.
