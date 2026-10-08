# Azana Farms Expo React Native Mobile App
## Claude Implementation Master Plan

## 1. Purpose

Build the field-worker mobile application for the Integrated Princess Azana Farms ERP using Expo React Native.

The application consumes the documented Laravel API and is designed for workers and supervisors who may operate in areas with unreliable connectivity.

The mobile application must allow field users to:
- sign in
- view their work
- scan animal and operational codes
- perform documented quick actions
- work offline
- synchronize recorded activity later
- see rejected/conflicting records
- complete assigned tasks

## 2. Backend Contract

The API documentation is authoritative.

API base path:
`/api/v1`

Authentication:
- `POST /auth/login`
- `POST /auth/logout`
- `GET /me`

Reference:
- `GET /reference`

Lookup:
- `GET /scan/{code}`
- `GET /animals/{code}`
- `GET /tasks`

Synchronization:
- `POST /sync/push`
- `GET /sync/status`
- `GET /sync/mutations/{client_id}`

Quick actions:
- `POST /quick/add_birth`
- `POST /quick/record_weight`
- `POST /quick/record_feed`
- `POST /quick/record_treatment`
- `POST /quick/record_vaccination`
- `POST /quick/record_mortality`
- `POST /quick/move_pigs`
- `POST /quick/record_service`
- `POST /quick/record_farrowing`
- `POST /quick/record_weaning`
- `POST /quick/stock_count`
- `POST /quick/complete_task`

The actual request and response contracts must be read from the backend API documentation before implementation.

## 3. Implementation Order

### Phase 00 - Initial Expo Setup
Developer initializes the Expo project.

### Phase 01 - Application Foundation
Set up:
- router
- root providers
- theme
- reusable UI
- configuration
- API foundation
- error/loading/empty states

### Phase 02 - Authentication
Build:
- splash/session restoration
- login
- authentication errors
- logout
- current-user state
- permission state

### Phase 03 - Offline Storage and Sync Engine
Build:
- local persistence
- mutation model
- mutation queue
- UUID generation
- occurred_at
- network monitoring
- sync manager
- retries
- outcomes
- conflict handling

### Phase 04 - Reference Data
Implement:
- `/reference`
- local reference cache
- refresh strategy
- offline availability

### Phase 05 - Worker Home
Implement:
- worker summary
- quick actions
- task shortcut
- sync state
- permission-aware navigation

### Phase 06 - Scanner
Implement:
- camera scanning
- code lookup
- result routing
- manual code fallback if supported by contract

### Phase 07 - Quick Actions
Implement separately:
1. Add Birth
2. Record Weight
3. Record Feed
4. Treatment
5. Vaccination
6. Mortality
7. Move Pigs
8. Breeding Service
9. Farrowing
10. Weaning
11. Stock Count
12. Complete Task

### Phase 08 - Tasks
Implement:
- task list
- task detail
- due/overdue states
- task completion

### Phase 09 - Animal Profiles
Implement only documented lookup/profile data and supported navigation.

### Phase 10 - Production
Implement production-related field workflows supported by the API.

### Phase 11 - Breeding
Implement breeding workflows supported by the API.

### Phase 12 - Health
Implement health workflows supported by the API.

### Phase 13 - Inventory
Implement inventory/stock workflows supported by the API.

### Phase 14 - Sync Center
Give workers visibility into:
- queued mutations
- syncing
- accepted
- rejected
- conflict
- failed/retry states

### Phase 15 - Profile and Device
Implement:
- current user
- roles
- permissions
- device/session information
- logout

### Phase 16 - Hardening
Perform:
- testing
- performance review
- offline testing
- failure testing
- navigation review
- accessibility review
- production configuration review

## 4. Global Rules

Every implementation phase must:
- read the relevant docs first
- inspect existing code first
- reuse existing components
- avoid speculative packages
- use TypeScript
- avoid API invention
- preserve offline requirements
- preserve permission requirements
- avoid duplicated backend business logic
- stay inside phase scope

## 5. Mobile UX Principle

The field worker should be able to complete common jobs with as few taps as reasonably possible.

The app should favor:
- scan
- select
- enter
- confirm
- queue/sync

rather than complex navigation.

## 6. Offline Mutation Lifecycle

A mutation follows:

`Draft -> Queued -> Sending -> Accepted`

or:

`Draft -> Queued -> Sending -> Rejected`

or:

`Draft -> Queued -> Sending -> Conflict`

or:

`Draft -> Queued -> Sending -> Failed -> Queued`

Accepted:
- remove/archive from active queue

Rejected:
- show server message
- worker corrects data
- create a new mutation

Conflict:
- do not blindly resend
- show clear conflict state
- server/supervisor resolves where required

Failed:
- retain mutation
- retry according to retry policy

## 7. Acceptance Standard

A phase is complete only when:
- its documented scope works
- API calls match the contract
- TypeScript is clean
- errors are handled
- offline behavior is correct where relevant
- no future scope was silently introduced
