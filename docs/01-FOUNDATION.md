# Part 01 - Expo Application Foundation

## Objective

Establish a production-quality foundation without implementing business modules.

## Read First

- `CLAUDE.md`
- `docs/react/REACT_NATIVE_CLAUDE_MASTER_PLAN.md`
- `docs/react/00-INITIAL-SETUP.md`
- backend API documentation
- existing Expo project

## Claude Prompt

You are implementing Part 01 of the Azana Farms Expo React Native mobile application.

The Expo project has already been initialized by the developer.

DO NOT recreate or reinitialize the project.

First inspect:
- package.json
- app configuration
- tsconfig
- Expo Router structure
- existing source files
- installed dependencies

### Objective

Create the application foundation:

- Expo Router structure
- root layout
- providers
- theme
- typography
- safe-area handling
- reusable UI primitives
- loading state
- empty state
- error state
- reusable buttons/inputs/cards
- toast/feedback mechanism if appropriate
- global error boundary
- environment configuration
- API client foundation
- request/error normalization

Do not implement business modules yet.

### API Rules

Do not invent endpoints or response types.

The API client should be generic enough to support the documented `/api/v1` contract.

### Quality

Use TypeScript throughout.

Do not introduce a large dependency set unless necessary.

### Acceptance Criteria

- App launches.
- Navigation foundation works.
- Shared UI components are reusable.
- API base configuration is centralized.
- Error/loading/empty states exist.
- TypeScript passes.
- Lint passes if configured.
- No business feature has been implemented.

### Finish

Report:
- files changed
- dependencies added
- checks run
- remaining limitations

Stop after Part 01.
