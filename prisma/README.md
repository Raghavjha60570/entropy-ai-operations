# `prisma/`

## Purpose

**Database schema, migrations, and seed data** for the Entropy AI Operations platform.
This directory is the single source of truth for the relational data model, managed by [Prisma ORM](https://www.prisma.io/).

## What Belongs Here

- `schema.prisma` — The Prisma schema file defining all models, relations, and enums
- `migrations/` — Auto-generated migration files (created by `prisma migrate dev`)
- `seed.ts` — Database seeding script for development/staging environments
- `seed-data/` — Static seed data files (JSON, CSV) referenced by `seed.ts`

### Expected structure once active:
```
prisma/
  schema.prisma
  seed.ts
  migrations/
    20240101000000_initial/
      migration.sql
  seed-data/
    users.json
    roles.json
```

## What Does NOT Belong Here

- ❌ Application business logic (belongs in `src/features/`)
- ❌ The Prisma client singleton (belongs in `src/lib/db.ts`)
- ❌ API route handlers
- ❌ TypeScript interfaces — Prisma auto-generates types; import from `@prisma/client`

## Common Commands

```bash
# Generate Prisma client after schema changes
npx prisma generate

# Create and apply a new migration
npx prisma migrate dev --name <description>

# Open Prisma Studio (database GUI)
npx prisma studio

# Reset database and re-seed
npx prisma migrate reset
```

> **Note:** Database is not yet connected. Add `DATABASE_URL` to `.env.local` before running any Prisma commands.
