# Part 15 - Profile and Device

## API

`GET /api/v1/me`
`POST /api/v1/auth/logout`

## Claude Prompt

Implement the mobile profile/device area.

Show only data actually returned by `/me`.

Possible areas:
- user identity
- roles
- permissions
- session/device information where supported
- logout

Do not expose sensitive authentication values.

Provide:
- clear logout confirmation
- session cleanup
- local queue handling according to safe product behavior

Do not delete unsynchronized business mutations merely because the user logs out.

Acceptance:
- profile loads from real `/me`
- logout works
- auth state is cleared securely
- unsynchronized data is protected from accidental loss
