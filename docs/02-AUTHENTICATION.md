# Part 02 - Authentication

## Objective

Implement secure mobile authentication using the documented API.

## API Contract

- `POST /api/v1/auth/login`
- `POST /api/v1/auth/logout`
- `GET /api/v1/me`

Login contract includes:
- email
- password
- device_id
- device_name

The API may require two-factor handling for accountant/owner roles according to the documented contract.

## Claude Prompt

Implement authentication for the Azana Farms Expo app.

Read the backend API documentation before writing code.

Build:
- splash/session restoration
- login screen
- login validation
- authentication error handling
- authenticated route protection
- current user loading
- logout
- session persistence

Store credentials/tokens using an appropriate secure mechanism for Expo.

Never log passwords or tokens.

The authenticated user model must reflect the API's `/me` response rather than an invented shape.

The UI must be permission-aware, but server authorization remains authoritative.

### Acceptance Criteria

- User can sign in through the real API.
- Existing session can be restored securely.
- Invalid credentials show a useful message.
- Forbidden/mobile/2FA-required responses are handled according to the API contract.
- User can log out.
- Unauthenticated users cannot access protected app routes.
- Authenticated users can reach the protected shell.
- TypeScript and lint pass.

Stop after authentication.
