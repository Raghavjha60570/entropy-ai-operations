# `src/hooks/`

## Purpose

**Shared custom React hooks** that encapsulate reusable stateful logic, side effects,
or browser API interactions. These hooks are used across multiple features or components.

## What Belongs Here

- Hooks that abstract **browser APIs**: `useLocalStorage`, `useMediaQuery`, `useOnClickOutside`, `useDebounce`
- Hooks that abstract **global state access**: `useCurrentUser`, `useTheme`, `useToast`
- Hooks that abstract **shared data fetching patterns**: `usePaginatedQuery`, `useInfiniteScroll`
- Hooks used in **two or more different features** — if a hook is only used by one feature, colocate it in that feature's `hooks/` folder

### Example structure:
```
hooks/
  useDebounce.ts
  useLocalStorage.ts
  useMediaQuery.ts
  useOnClickOutside.ts
  useToast.ts
```

## What Does NOT Belong Here

- ❌ Feature-specific hooks (e.g., `useAgentRuns` — belongs in `src/features/agents/hooks/`)
- ❌ Hooks that are only used in one place — keep them colocated until they're shared
- ❌ Non-hook utility functions (belongs in `src/utils/`)
- ❌ State management stores (use Zustand/Jotai directly — or place in `src/features/`)
- ❌ Server-side code — hooks are **client-side only** (use `"use client"` as needed)

## Naming Convention

All custom hooks must start with `use` and be named in **camelCase**:
- ✅ `useDebounce`, `useLocalStorage`, `useCurrentUser`
- ❌ `debounceHook`, `LocalStorageHook`
