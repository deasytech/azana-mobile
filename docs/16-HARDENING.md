# Part 16 - Production Hardening

## Objective

Prepare the Expo mobile app for production use.

## Claude Prompt

Perform a production-readiness review of the completed Azana Farms mobile application.

### Test

- authentication
- session restoration
- logout
- permissions
- scanner
- every quick action
- task completion
- offline mutation creation
- app restart with queued mutations
- reconnect and synchronization
- duplicate resend/idempotency behavior
- rejected mutations
- conflicts
- failed requests
- reference-data refresh
- API timeout behavior
- malformed responses
- navigation
- Android
- iOS where available

### Security Review

Check:
- secrets
- token handling
- logs
- debug output
- production API configuration
- insecure storage
- permission bypasses

### Performance

Check:
- unnecessary renders
- large local lists
- scanner performance
- queue processing
- startup time
- memory use

### UX

Check:
- offline visibility
- errors
- loading states
- empty states
- touch targets
- accessibility
- form usability in field conditions

### API Contract Audit

Search the codebase for:
- undocumented endpoints
- invented fields
- fake data
- hardcoded business rules
- duplicate backend logic

Remove or report any violations.

### Acceptance

Produce a production-readiness report:
- passed
- failed
- needs backend change
- recommended future work

Do not silently fix unrelated ERP/backend functionality.
