# `docs/`

## Purpose

**Project-level documentation** for the Entropy AI Operations platform. This directory
is the central knowledge base for engineers, product managers, and contributors working on this codebase.

## What Belongs Here

- **Architecture documents**: system design decisions, data flow diagrams, infrastructure overview
- **ADRs (Architecture Decision Records)**: records of important technical decisions and their rationale
- **Feature specifications**: detailed specs for complex features before implementation
- **API documentation**: endpoint contracts, authentication flows, error codes
- **Runbooks**: operational procedures for deployment, incident response, database migrations
- **Onboarding guides**: getting-started documentation for new team members

### Recommended structure:
```
docs/
  architecture/
    system-overview.md
    data-model.md
    auth-flow.md
  adr/
    0001-use-nextjs-app-router.md
    0002-use-prisma-as-orm.md
  features/
    agents.md
    pipelines.md
  runbooks/
    deployment.md
    database-migrations.md
  api/
    overview.md
```

## What Does NOT Belong Here

- ❌ Code — documentation only; no `.ts`, `.tsx`, `.js` files
- ❌ Environment-specific credentials or secrets (use `.env.local` and a secrets manager)
- ❌ Auto-generated files — don't commit build output or auto-generated API docs unless intentional
- ❌ Personal notes or scratch content — use your own local files

## Convention

All documents use **Markdown** (`.md`). Use clear headings, tables of contents for long documents,
and diagrams using Mermaid syntax where helpful.
