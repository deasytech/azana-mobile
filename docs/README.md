# Azana Farms Expo Claude Instructions

This package contains the implementation instructions for the **Expo React Native mobile application** of the Integrated Princess Azana Farms ERP.

## Start Here

1. Read `CLAUDE.md`.
2. Read `docs/react/REACT_NATIVE_CLAUDE_MASTER_PLAN.md`.
3. Developer completes `docs/react/00-INITIAL-SETUP.md`.
4. Claude implements one phase at a time.
5. Update `docs/react/IMPLEMENTATION_STATUS.md` after each phase.

## Important

The Expo project is initialized by the developer before Claude starts.

The backend API documentation is authoritative.

Claude must never invent API endpoints, fields, permissions, response shapes, or business rules.

## Quick Action Documentation

The twelve quick-action prompts are under:

`docs/react/07-QUICK-ACTIONS/`

They correspond to the backend's documented quick actions.

## Recommended Workflow

Give Claude one phase document at a time.

Example:

> Read `CLAUDE.md` and `docs/react/01-FOUNDATION.md`, inspect the existing Expo project, and implement Part 01 only. Do not proceed to Part 02.

After completion, review the result before starting the next phase.
