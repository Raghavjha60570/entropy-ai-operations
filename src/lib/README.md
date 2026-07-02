# `src/lib/`

## Purpose

**Low-level infrastructure and configuration utilities** — foundational code that is used
by services, features, and utilities. Think of `lib/` as the "engine room" of the application.

## What Belongs Here

- **Singleton clients**: database client, HTTP client, logger instance
- **Environment variable access**: a typed config module that validates and exports env vars
- **Authentication helpers**: session utilities, JWT parsing (not auth logic — that's a feature)
- **Third-party library configuration**: initialisation of analytics, monitoring (e.g., Sentry)
- **Server-side utilities**: rate limiting helpers, caching adapters

### Example structure:
```
lib/
  db.ts            ← Prisma client singleton
  config.ts        ← Typed & validated environment variables (using zod)
  logger.ts        ← Pino/Winston logger instance
  auth.ts          ← next-auth configuration options
  rate-limit.ts    ← Edge rate limiting helper
```

## What Does NOT Belong Here

- ❌ React components or hooks of any kind
- ❌ Business logic or domain rules (belongs in `src/features/`)
- ❌ Feature-specific utilities (belongs in the feature's own `utils/` folder)
- ❌ General-purpose utility functions like `formatDate` (belongs in `src/utils/`)
- ❌ UI constants like color tokens (belongs in `src/constants/`)

## Key Principle

`src/lib/` should be **framework-agnostic where possible**. Code here should work in
Node.js server context and should not import from React or Next.js client-side APIs.
