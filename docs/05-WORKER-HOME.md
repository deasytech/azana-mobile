# Part 05 - Worker Home

## Objective

Create the primary field-worker home screen.

## API

- `GET /api/v1/me`
- `GET /api/v1/tasks`
- cached `/reference`
- sync engine status

## Claude Prompt

Build the Azana Farms worker home screen.

This is a field app, not a miniature Filament dashboard.

Prioritize:
- today's work
- quick actions
- scanner
- tasks
- offline/sync state
- user identity
- permission-aware options

Use the actual `/me` permissions and roles.

Do not display options the current user cannot access where permissions are available.

Do not invent statistics or dashboard metrics not supplied by the API.

### UX

The most common field actions should be reachable quickly.

Show:
- connection state
- pending sync count/status
- task shortcut
- scanner shortcut
- documented quick-action shortcuts allowed to the worker

### Acceptance

- Worker sees an actionable home screen.
- No invented data.
- Permissions are respected.
- Offline state is visible.
- Sync state is visible.
