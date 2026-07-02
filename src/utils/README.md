# `src/utils/`

## Purpose

**Pure, stateless utility functions** used across the entire codebase. Every function
in `utils/` should be completely free of side effects, React context, and application state.
If you can write a unit test for it with zero mocking, it belongs here.

## What Belongs Here

- **Formatters**: `formatDate`, `formatCurrency`, `formatBytes`, `formatDuration`
- **Validators**: `isValidEmail`, `isValidUrl`, `isNonEmpty`
- **Transformers**: `slugify`, `truncateText`, `capitalize`, `toTitleCase`
- **Array/object helpers**: `groupBy`, `uniqueBy`, `deepMerge`, `pick`, `omit`
- **Type guards**: `isString`, `isDefined`, `isError`
- **Math/calculation helpers**: `clamp`, `round`, `percentOf`

### Example structure:
```
utils/
  date.ts          ← Date formatting and manipulation
  string.ts        ← String transformation utilities
  number.ts        ← Number formatting and math helpers
  array.ts         ← Array manipulation utilities
  validation.ts    ← Validation functions
```

## What Does NOT Belong Here

- ❌ React hooks (belongs in `src/hooks/`)
- ❌ Functions with side effects (API calls, DOM manipulation, logging)
- ❌ Feature-specific helpers (belongs in `src/features/<feature>/utils/`)
- ❌ Constants or configuration values (belongs in `src/constants/`)
- ❌ Infrastructure utilities like database clients (belongs in `src/lib/`)

## Testing Expectation

**Every function in `src/utils/` should have 100% unit test coverage.**
These are the easiest functions to test — there are no excuses for untested utility code.
