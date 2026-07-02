# `src/services/`

## Purpose

**Application-level API service layer** — the single source of truth for all external
HTTP communication, third-party SDK integrations, and backend API calls.
Every interaction with a remote API or service is defined and exported from here.

## What Belongs Here

- **HTTP client modules**: functions that call internal or external REST/GraphQL APIs
- **Third-party SDK wrappers**: wrapped integrations for OpenAI, Stripe, Resend, S3, etc.
- **Server actions** that communicate with external systems (if not colocated in a feature)
- **API response transformation** — mapping raw API responses to typed domain models

### Example structure:
```
services/
  openai.ts        ← OpenAI client wrapper
  database.ts      ← Prisma client singleton
  storage.ts       ← S3/Blob storage utilities
  analytics.ts     ← Analytics event tracking
  email.ts         ← Email sending via Resend/SendGrid
```

## What Does NOT Belong Here

- ❌ Business logic or domain rules (belongs in `src/features/`)
- ❌ React hooks that wrap service calls (belongs in `src/hooks/` or the feature's `hooks/`)
- ❌ Database schema definitions (belongs in `prisma/schema.prisma`)
- ❌ UI components of any kind
- ❌ Configuration values or secrets — use `src/lib/config.ts` for environment variable access

## Conventions

- Each file exports **named functions**, not class instances where possible
- All functions should be typed with explicit return types
- Errors should be surfaced as typed exceptions or Result types — never silently swallowed
