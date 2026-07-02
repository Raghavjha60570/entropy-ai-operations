# `src/components/ui/`

## Purpose

Reusable, **design-system-level UI primitives** shared across the entire application.
These are the atomic and molecular building blocks of every interface in Entropy AI Operations.

## What Belongs Here

- **Primitive components**: `Button`, `Input`, `Select`, `Checkbox`, `Badge`, `Spinner`, `Avatar`, `Tooltip`
- **Display components**: `Card`, `Modal`, `Dialog`, `Drawer`, `Toast`, `Alert`, `Accordion`
- **Layout primitives**: `Divider`, `Skeleton`, `EmptyState`
- Components that are **fully reusable**, accept props, and are **not tied to any feature or business domain**
- Each component should live in its own subfolder: `ui/Button/Button.tsx`, `ui/Button/Button.test.tsx`

## What Does NOT Belong Here

- ❌ Feature-specific components (e.g., `AgentRunCard` — belongs in `src/features/agents/components/`)
- ❌ Page-level layouts or route wrappers (belongs in `src/components/layout/`)
- ❌ Components that import from `src/services/` or `src/features/`
- ❌ Business logic, API calls, or state management
- ❌ Anything that is not meant to be reused outside a single feature

## Naming Convention

Use **PascalCase** for component files and folders:
```
src/components/ui/
  Button/
    Button.tsx
    Button.test.tsx
    index.ts
  Card/
    Card.tsx
    index.ts
```
