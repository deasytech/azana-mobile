# Part 13 - Inventory

## Scope

Implement mobile inventory workflows explicitly supported by the API.

Primary documented workflow:
- stock count

## Claude Prompt

Implement stock counting for field workers/supervisors.

Use the exact `stock_count` payload contract.

The API documents:
- location_id
- lines
- item_id
- batch_id
- counted_quantity
- seen_quantity
- reason
- notes

The backend documents all-or-nothing behavior and stale-count rejection.

### UX

- choose/scan location where supported
- enter count lines
- review before submission
- show clear submission state
- support offline queueing

Do not calculate authoritative inventory balances on the phone.

The server remains authoritative.

Acceptance:
- exact payload
- offline persistence
- all-or-nothing server outcomes clearly shown
- stale count rejection explained using server message
