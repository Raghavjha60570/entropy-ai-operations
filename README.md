# Entropy AI Operations

> Internal AI Operations platform for managing, monitoring, and orchestrating AI agents, pipelines, and evaluations at scale.

---

## Overview

**Entropy AI Operations** is an internal SaaS platform that provides engineering and operations teams with a unified control plane for AI workflows. It enables teams to:

- **Deploy and manage** AI agents across environments
- **Build and run** multi-step AI pipelines with real-time observability
- **Evaluate** model outputs using structured scoring frameworks
- **Monitor** costs, latency, error rates, and reliability metrics
- **Collaborate** across teams with shared workspaces, RBAC, and audit logs

---

## Vision

To become the central nervous system of AI operations within the organisation — replacing
fragmented scripts, ad-hoc notebooks, and manual processes with a scalable, auditable, and
developer-friendly operations platform.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Framework | [Next.js 16](https://nextjs.org/) (App Router) |
| Language | [TypeScript](https://www.typescriptlang.org/) (strict mode) |
| Styling | [Tailwind CSS v4](https://tailwindcss.com/) |
| Database | PostgreSQL via [Prisma ORM](https://www.prisma.io/) |
| Auth | (to be implemented — Auth.js / NextAuth v5) |
| AI | [OpenAI SDK](https://platform.openai.com/docs/api-reference) |
| Linting | [ESLint](https://eslint.org/) + `eslint-config-next` |
| Package Manager | npm |
| Runtime | Node.js ≥ 20 |

---

## Folder Structure

```
entropy-ai-operations/
├── src/
│   ├── app/                  # Next.js App Router — routes, layouts, pages
│   │   ├── (auth)/           # Auth route group
│   │   ├── (dashboard)/      # Protected dashboard route group
│   │   ├── api/              # API route handlers
│   │   ├── layout.tsx        # Root layout
│   │   └── globals.css       # Global styles (Tailwind entry point)
│   │
│   ├── components/
│   │   ├── ui/               # Reusable primitive UI components (Button, Card, Input…)
│   │   └── layout/           # Application shell components (Sidebar, Navbar, Header…)
│   │
│   ├── features/             # Vertical feature slices (agents, pipelines, evaluations…)
│   ├── services/             # External API clients and third-party integrations
│   ├── lib/                  # Infrastructure: DB client, config, logger, auth options
│   ├── hooks/                # Shared custom React hooks
│   ├── utils/                # Pure utility functions (formatters, validators, helpers)
│   ├── types/                # Shared TypeScript interfaces, types, and enums
│   └── constants/            # App-wide constant values (routes, limits, enums)
│
├── prisma/                   # Prisma schema, migrations, and seed data
├── docs/                     # Architecture docs, ADRs, runbooks, API specs
├── public/                   # Static assets (fonts, images, icons)
├── .env.example              # Template for required environment variables
├── next.config.ts            # Next.js configuration
├── tsconfig.json             # TypeScript configuration
├── postcss.config.mjs        # PostCSS / Tailwind configuration
└── eslint.config.mjs         # ESLint configuration
```

> Each directory contains a `README.md` explaining its purpose and conventions.

---

## Local Setup

### Prerequisites

- **Node.js** ≥ 20 (use [nvm](https://github.com/nvm-sh/nvm) or [fnm](https://github.com/Schniz/fnm))
- **npm** ≥ 10
- **PostgreSQL** (local or via Docker)
- **Git** ≥ 2.40

### 1. Clone the repository

```bash
git clone https://github.com/Raghavjha60570/entropy-ai-operations.git
cd entropy-ai-operations
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

```bash
cp .env.example .env.local
```

Open `.env.local` and fill in all required values. See [`.env.example`](.env.example) for descriptions.

### 4. Set up the database

```bash
# Apply migrations (once database is connected)
npx prisma migrate dev

# Optional: seed with development data
npx prisma db seed
```

### 5. Start the development server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## Development Workflow

### Code Quality

```bash
npm run lint          # Run ESLint
npm run build         # Production build (also type-checks)
```

### Database

```bash
npx prisma studio     # Open visual database browser
npx prisma generate   # Regenerate Prisma client after schema changes
npx prisma migrate dev --name <description>  # Create a new migration
```

### Path Aliases

Absolute imports are configured via `@/*` mapping to `src/*`:

```ts
// ✅ Use this
import { Button } from "@/components/ui/Button";

// ❌ Avoid this
import { Button } from "../../components/ui/Button";
```

---

## Git Branching Strategy

This project follows **trunk-based development** with short-lived feature branches.

### Branch Naming

| Type | Pattern | Example |
|---|---|---|
| Feature | `feature/<ticket-or-description>` | `feature/agent-run-view` |
| Bug Fix | `fix/<description>` | `fix/pipeline-timeout-error` |
| Configuration | `feature/project-<topic>` | `feature/project-configuration` |
| Release | `release/<version>` | `release/1.2.0` |
| Hotfix | `hotfix/<description>` | `hotfix/auth-token-expiry` |

### Workflow

```
main
  └── feature/project-foundation       ← Initial scaffold (Step 1)
  └── feature/project-configuration    ← Config & structure (Step 2)
  └── feature/<next-feature>           ← Each new ticket = new branch
```

1. **Branch from `main`** — never commit directly to `main`
2. **Open a Pull Request** — all changes require code review before merging
3. **Squash and merge** — keep `main` history clean and linear
4. **Delete the branch** after merging

### Commit Message Convention

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
feat(agents): add agent run status polling
fix(auth): resolve token refresh race condition
chore(deps): update next to 16.3.0
docs(readme): add branching strategy section
refactor(pipeline): extract run execution into service layer
```

---

## Contributing

1. Pick a ticket from the project board
2. Create a branch following the naming convention above
3. Write code — follow the conventions in each folder's `README.md`
4. Open a PR with a clear description
5. Address review feedback
6. Merge after approval ✅

---

## License

Internal project — not for public distribution.
