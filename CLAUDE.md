# Azana Farms Expo Mobile App - Claude Instructions

## Project Context

This repository contains the **Expo React Native mobile worker application** for the Integrated Princess Azana Farms ERP.

The Laravel application is the central ERP/backend. The mobile app is a field application for workers and supervisors.

The mobile application must support:
- Secure worker sign-in
- Permission-aware access
- Fast field data capture
- Animal/tag scanning
- Twelve documented quick actions
- Worker task management
- Offline-first data capture
- Reliable synchronization when connectivity returns
- Reference-data caching
- Conflict/rejection handling
- Device/session management

## Critical Rule: The Expo Project Is Already Initialized

The developer will initialize the Expo project before Claude begins implementation.

DO NOT:
- run `create-expo-app`
- recreate or reinitialize the Expo project
- replace the project unnecessarily
- delete the existing project structure
- replace package.json without a clear technical reason
- install large groups of packages speculatively

First inspect the existing project and work with what is already installed.

## Authoritative Documentation

Before implementation, read:

1. `docs/react/REACT_NATIVE_CLAUDE_MASTER_PLAN.md`
2. `docs/react/00-INITIAL-SETUP.md`
3. The current phase document being implemented
4. The backend API documentation supplied with the ERP project
5. Existing source code and configuration

The API documentation is the contract.

## API Contract Rule

NEVER invent:
- endpoints
- HTTP methods
- request fields
- response fields
- permissions
- status values
- error codes
- business rules

If the mobile screen requires information that is not documented by the API contract:

1. Stop implementation of that dependency.
2. Identify exactly what is missing.
3. Report the missing API contract.
4. Do not create a fake endpoint or guessed field.
5. Do not hide the gap with hardcoded mock data.

## Architecture Principles

Use:
- Expo
- React Native
- TypeScript
- Expo Router where compatible with the initialized project
- Reusable components
- Feature-oriented modules
- Central API client
- Central authentication/session management
- Offline persistence
- Mutation queue
- Synchronization manager
- Network awareness
- Permission-driven UI

Prefer a structure similar to:

app/
  _layout.tsx
  index.tsx
  (auth)/
  (app)/
    _layout.tsx
    home.tsx
    tasks.tsx
    scanner.tsx
    sync.tsx
    profile.tsx
    animals/
    breeding/
    health/
    production/
    inventory/

src/
  api/
  auth/
  components/
  features/
  hooks/
  storage/
  sync/
  types/
  utils/
  constants/

Do not force this exact structure if the initialized project has a better equivalent. Preserve a clean architecture.

## Offline-First Requirement

Offline operation is a first-class requirement.

Mutations must support:
- client-generated UUID
- occurred_at event timestamp
- local persistence
- queued status
- retry
- idempotent resend
- ordered processing
- accepted outcome
- rejected outcome
- conflict outcome
- failed outcome

The backend contract defines `client_id` idempotency.

Do not use temporary fake API responses where real documented API endpoints exist.

## Backend API Contract

The documented API is under `/api/v1`.

Important documented endpoints include:

### Authentication
- `POST /auth/login`
- `POST /auth/logout`
- `GET /me`

### Reference Data
- `GET /reference`

### Scanning and Lookup
- `GET /scan/{code}`
- `GET /animals/{code}`
- `GET /tasks`

### Offline Synchronization
- `POST /sync/push`
- `GET /sync/status`
- `GET /sync/mutations/{client_id}`

### Quick Actions
- `POST /quick/{type}`

The twelve documented quick actions are:
1. `add_birth`
2. `record_weight`
3. `record_feed`
4. `record_treatment`
5. `record_vaccination`
6. `record_mortality`
7. `move_pigs`
8. `record_service`
9. `record_farrowing`
10. `record_weaning`
11. `stock_count`
12. `complete_task`

Read the API documentation before implementing any of them.

## Business Logic

The mobile application should not become a second ERP backend.

The server remains authoritative for business rules.

The mobile app is responsible for:
- collecting valid user input
- validating obvious client-side requirements
- storing mutations offline
- sending mutations
- presenting server outcomes
- showing conflicts and rejections clearly

Do not duplicate complex backend business rules in the mobile app.

## User Experience

This is a field application, not a mobile copy of the Filament ERP.

Prioritize:
- large touch targets
- minimal typing
- scan-first workflows
- clear status
- fast actions
- obvious offline state
- clear synchronization state
- simple forms
- confirmation for destructive/high-impact actions
- useful validation messages
- accessibility
- usable operation in poor connectivity


## Azana Farms Brand Assets

The Expo application uses the official **Integrated Princess Azana Farms** logo and brand identity.

A prepared asset package has been supplied for this project. It contains:

```text
branding/
├── azana-farms-logo-transparent.png
├── azana-farms-logo.jpg
├── azana-farms-mark.png
└── brand-colors.json

icons/
├── icon.png
├── adaptive-icon-foreground.png
├── adaptive-icon-background.png
└── notification-icon.png

splash/
├── splash-logo.png
├── splash-dark.png
├── splash-cream.png
└── splash-white.png
```

### Asset Installation Rule

Before implementing or changing the application's branding:

1. Inspect the existing `assets/` directory.
2. Inspect `app.json` or `app.config.js`, `app.config.ts`, or equivalent Expo configuration.
3. Inspect the current splash/icon configuration.
4. Back up existing assets if necessary.
5. Use the supplied Azana Farms assets instead of the original Expo placeholder branding.
6. Do not recreate the logo in code.
7. Do not redesign, recolor, distort, stretch, crop or otherwise alter the official logo.
8. Do not replace unrelated assets that are still required by the application.
9. Keep branding assets centralized and reusable.

### Recommended Expo Asset Structure

Adapt this to the project's existing structure rather than blindly creating a new one:

```text
assets/
├── icon.png
├── adaptive-icon-foreground.png
├── adaptive-icon-background.png
├── splash.png
└── branding/
    ├── azana-farms-logo-transparent.png
    └── azana-farms-mark.png
```

If the project already has a different but clean asset structure, preserve it and place the files in the appropriate equivalent locations.

### Expo App Icon

Use the supplied:

```text
icon.png
```

as the main application icon where the current Expo configuration expects the app icon.

For example, if the project uses the standard Expo configuration:

```json
{
  "expo": {
    "icon": "./assets/icon.png"
  }
}
```

Do not blindly overwrite the existing configuration. Inspect it first.

### Android Adaptive Icon

Use:

```text
adaptive-icon-foreground.png
adaptive-icon-background.png
```

for Android adaptive icon configuration where supported by the current Expo setup.

The foreground asset has been prepared with safe spacing because Android launchers may crop adaptive icons.

### Splash Screen

Use the supplied Azana Farms splash assets.

Preferred branded option:

```text
splash/splash-dark.png
```

Alternatives:

```text
splash/splash-cream.png
splash/splash-white.png
```

If the existing Expo configuration uses a separate image and background color, use:

```text
splash/splash-logo.png
```

with the appropriate Azana Farms background color.

Preferred dark background:

```text
#261B14
```

Do not create a splash screen that looks unrelated to the application branding.

### Reusable Branding

Use:

```text
branding/azana-farms-logo-transparent.png
```

for:

- login screen
- authenticated app header where appropriate
- profile/about areas
- empty states where branding is useful
- onboarding if introduced in an approved phase

Use:

```text
branding/azana-farms-mark.png
```

for compact areas where the complete logo would be too large.

Do not place the full logo everywhere. Branding should be visible but restrained.

### Notification Icon

Where the Expo/native notification implementation requires a monochrome notification icon, use:

```text
icons/notification-icon.png
```

Do not use the full-color logo as an Android notification icon if the platform requires a monochrome asset.

Verify the resulting notification appearance on the supported Android target.

### Brand Colors

The supplied `branding/brand-colors.json` is the source for the prepared Azana Farms palette.

Core colors:

```text
Primary Orange:       #F08732
Bright Golden Orange: #F7A62E
Royal Gold:           #F3C63C
Light Gold:           #F7E376

Deep Brown:           #261B14
Pig Brown:            #D5A14C
Dark Pig Brown:       #B47E3D

Warm Cream:           #FBFBEA
White:                #FFFFFF
```

Do not hardcode these colors inconsistently throughout the application.

Create or use centralized theme/design tokens so that:

- buttons
- headers
- cards
- badges
- backgrounds
- typography
- active states
- icons

can consistently use the Azana Farms visual system.

### Branding Design Direction

The mobile app should feel:

- professional
- modern
- clean
- agricultural
- premium
- trustworthy
- practical for field workers

Do NOT make the app overwhelmingly orange.

Use the brand palette with restraint:

- white/cream for most surfaces
- deep brown for strong text and selected dark surfaces
- orange for primary actions and active states
- gold for highlights
- semantic colors for success/warning/error states

The mobile application is a field application, not a marketing website. Brand the app without sacrificing speed, readability or usability.

### Asset Verification

When implementing the asset update:

1. Verify the logo renders correctly on light and dark backgrounds.
2. Verify the app icon has no unexpected white border.
3. Verify the Android adaptive icon does not crop the important parts of the logo.
4. Verify the splash screen is centered and visually balanced.
5. Verify the logo is not stretched or distorted.
6. Verify images are loaded from local bundled assets.
7. Verify production builds can resolve the assets.
8. Verify the app launches successfully after the configuration changes.

Do not move on to unrelated implementation until the branding assets are correctly integrated.

## Security

Never:
- log passwords
- expose authentication tokens in UI
- put secrets in source code
- commit production API credentials
- bypass server authorization
- assume a permission based only on navigation visibility

The server rechecks authorization on requests.

## Scope Control

Implement one phase at a time.

Do not:
- jump to future phases
- redesign unrelated screens
- refactor unrelated code
- add unrequested features
- build speculative dashboards
- create fake backend functionality

If a dependency belongs to a later phase, document it rather than silently implementing it.

## Testing

After every implementation phase:
- run TypeScript checks
- run linting if configured
- run tests if configured
- verify the app starts
- verify the implemented flow
- verify offline behavior where applicable
- verify error states
- verify navigation
- inspect changed files

Fix errors caused by the current phase before declaring completion.


### Asset Integration Completion Check

If the current phase touches application branding, also verify:

- official Azana Farms logo is being used
- Expo icon configuration is correct
- splash configuration is correct
- Android adaptive icon configuration is correct where applicable
- no original Expo placeholder branding remains where it should have been replaced
- branding assets are stored in the project's agreed asset structure

## Completion Protocol

At the end of each phase:

1. Summarize files created/changed.
2. Summarize functionality implemented.
3. List tests/checks performed.
4. List any known limitations.
5. Identify missing backend/API contracts, if any.
6. Update the project's implementation status documentation.
7. Stop.

Do not automatically start the next phase.
