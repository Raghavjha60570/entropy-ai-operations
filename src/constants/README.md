# `src/constants/`

## Purpose

**Application-wide constant values** — immutable data that is referenced by name
throughout the codebase to avoid magic numbers, magic strings, and duplicated literals.

## What Belongs Here

- **Route paths**: `ROUTES.dashboard`, `ROUTES.settings`, `ROUTES.agentDetail`
- **API endpoints**: base URL constants, endpoint path strings
- **UI constants**: breakpoint values, z-index scale, animation durations
- **Business rule constants**: max file size, free tier limits, timeout durations
- **Feature flags** (static, compile-time flags — not remote config)
- **Regex patterns** used in multiple places

### Example structure:
```
constants/
  routes.ts        ← All client-side route path strings
  api.ts           ← API base URLs and endpoint paths
  limits.ts        ← Business rule limits (e.g., MAX_AGENTS_FREE_TIER = 3)
  ui.ts            ← UI constants (breakpoints, z-index, durations)
  regex.ts         ← Shared regular expressions
```

## What Does NOT Belong Here

- ❌ Functions or computed values — constants must be **static literals**
- ❌ Environment-specific values — use `src/lib/config.ts` for environment variables
- ❌ Feature-scoped constants that are only used in one feature (keep them colocated)
- ❌ TypeScript types or interfaces (belongs in `src/types/`)
- ❌ Default configuration objects for third-party libraries (belongs in `src/lib/`)

## Convention

Use **SCREAMING_SNAKE_CASE** for primitive constants and **PascalCase** for constant
object namespaces:

```ts
// ✅ Correct
export const MAX_UPLOAD_SIZE_MB = 50;
export const ROUTES = { dashboard: "/dashboard" } as const;

// ❌ Incorrect
export const maxUploadSize = 50;
```
