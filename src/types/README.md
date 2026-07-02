# `src/types/`

## Purpose

**Shared TypeScript type definitions, interfaces, and enums** that are used across
multiple features, services, or layers of the application. This directory ensures
a single source of truth for the domain model of Entropy AI Operations.

## What Belongs Here

- **Domain model interfaces**: `User`, `Organization`, `Agent`, `Pipeline`, `Run`, `Evaluation`
- **API contract types**: request/response shapes for the internal API
- **Shared enums**: `AgentStatus`, `RunStatus`, `UserRole`, `PlanTier`
- **Global utility types**: `Nullable<T>`, `Optional<T>`, `AsyncResult<T>`, `PaginatedResponse<T>`
- **Zod schemas** used for runtime validation that are shared across layers

### Example structure:
```
types/
  index.ts         ← Re-exports all shared types
  user.ts          ← User, UserRole, UserProfile
  agent.ts         ← Agent, AgentStatus, AgentConfig
  pipeline.ts      ← Pipeline, PipelineRun, RunStatus
  api.ts           ← Generic API response wrappers
  common.ts        ← Utility types used everywhere
```

## What Does NOT Belong Here

- ❌ Types that are **only used within a single feature** (colocate them in `src/features/<feature>/types/`)
- ❌ Component prop types (define those inline or next to the component)
- ❌ Runtime validation logic (use Zod schemas, but keep the validation functions in `src/utils/` or `src/lib/`)
- ❌ Any JavaScript logic — this directory is **types only**

## Convention

Prefer `interface` over `type` for object shapes. Use `type` for unions, intersections, and mapped types.
Always export types as named exports, never as default exports.
