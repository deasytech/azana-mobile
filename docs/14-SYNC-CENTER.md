# Part 14 - Sync Center

## Objective

Provide a worker-facing view of offline synchronization.

## Claude Prompt

Build a Sync Center using the existing sync engine.

Display:
- queued mutations
- currently syncing
- accepted history where retained
- rejected records
- conflicts
- failed records
- retry availability

Do not allow users to blindly duplicate mutations.

For conflicts:
- clearly explain that the record requires resolution
- do not automatically resend unchanged data

For rejected:
- show server feedback
- provide a path to correct data and create a new mutation

For failed:
- provide retry when appropriate

Use `/sync/status` and `/sync/mutations/{client_id}` only according to their documented contracts.

Acceptance:
- worker understands whether data has synchronized
- failed records can be retried
- conflicts are not silently lost
- no duplicate submission is introduced
