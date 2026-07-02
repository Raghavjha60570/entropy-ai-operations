# `src/components/layout/`

## Purpose

**Application-level structural components** that define the visual skeleton and navigation
of the Entropy AI Operations platform. These components wrap pages and establish the
overall UI frame (shell) of the application.

## What Belongs Here

- **Navigation**: `Navbar`, `Sidebar`, `TopBar`, `BottomNav`
- **Shell wrappers**: `DashboardLayout`, `AuthLayout`, `PublicLayout`
- **Page chrome**: `Header`, `Footer`, `PageContainer`, `SectionWrapper`
- **Breadcrumbs** and **page-level tab bars**
- Components that are used to **frame pages or sections** but do not contain business logic

## What Does NOT Belong Here

- ❌ UI primitives like buttons, inputs, or cards (belongs in `src/components/ui/`)
- ❌ Feature-specific panels or cards (belongs in the appropriate `src/features/*/components/` folder)
- ❌ Route definitions or page files (belongs in `src/app/`)
- ❌ Business logic, data fetching, or API calls

## Usage Pattern

Layout components are typically used in `src/app/layout.tsx` or nested layouts:

```tsx
// src/app/(dashboard)/layout.tsx
import { DashboardLayout } from "@/components/layout/DashboardLayout";

export default function Layout({ children }: { children: React.ReactNode }) {
  return <DashboardLayout>{children}</DashboardLayout>;
}
```
