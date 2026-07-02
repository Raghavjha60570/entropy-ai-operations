# `src/features/`

## Purpose

**Self-contained vertical slices of application functionality.** Each subdirectory in `features/`
represents a distinct domain or product feature of Entropy AI Operations (e.g., agents, pipelines,
evaluations, billing). Features are the primary unit of development and ownership.

## What Belongs Here

Each feature folder (`src/features/<feature-name>/`) can contain:

```
features/
  agents/
    components/       ← UI components specific to this feature
    hooks/            ← Custom hooks scoped to this feature
    types/            ← TypeScript types/interfaces for this feature
    utils/            ← Utility functions specific to this feature
    services.ts       ← API calls / data fetching for this feature
    store.ts          ← Local state management (Zustand slice, context, etc.)
    index.ts          ← Public exports (barrel file)
```

## What Does NOT Belong Here

- ❌ Shared/reusable UI primitives (belongs in `src/components/ui/`)
- ❌ Cross-cutting utilities like date formatters, validators (belongs in `src/utils/`)
- ❌ Global API client configuration (belongs in `src/lib/`)
- ❌ Shared TypeScript types used across multiple features (belongs in `src/types/`)
- ❌ Route/page files — those live in `src/app/`; features export components that pages use

## Design Principle

A feature module should be **as self-contained as possible**. If you can delete the entire
feature folder and the rest of the app still compiles, you've done it right.

Features may import from `src/components/ui/`, `src/lib/`, `src/utils/`, `src/hooks/`, and `src/types/`,
but should **never import from other feature modules** directly. Use the public `index.ts` export
or a shared service if cross-feature communication is needed.
