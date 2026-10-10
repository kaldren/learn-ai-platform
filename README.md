# AI Learning Platform

A platform that helps people learn AI through structured roadmaps relevant to their professional roles. See [PRODUCT.md](PRODUCT.md) and [TECH_STACK.md](TECH_STACK.md).

## Getting started

```bash
npm install
cp .env.example .env.local   # fill in Supabase staging credentials
npm run dev
```

## Scripts

| Script              | Purpose                                                   |
| ------------------- | --------------------------------------------------------- |
| `npm run dev`       | Start the Next.js dev server                              |
| `npm run build`     | Production build                                          |
| `npm run lint`      | ESLint                                                    |
| `npm run typecheck` | TypeScript checks                                         |
| `npm run db:start`  | Start local Supabase (requires Docker)                    |
| `npm run db:reset`  | Recreate the local database from `supabase/migrations`    |
| `npm run db:types`  | Regenerate `src/lib/supabase/database.types.ts` from local DB |

New migrations: `npx supabase migration new <name>`.

## Structure

```
src/
  app/              # App Router: routes, layouts, Server Actions, Route Handlers
  lib/supabase/     # Supabase clients (browser, server, proxy) and DB types
  proxy.ts          # Refreshes the Supabase auth session on each request
supabase/           # Supabase CLI config and SQL migrations
```
