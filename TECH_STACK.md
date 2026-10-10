# Platform Tech Stack — Reference for People and Agents

## Principles

- Prefer established managed services over operating infrastructure.
- Keep custom backend code focused on product-specific logic.
- Use stable releases and official SDKs and documentation.

## Application

- **Frontend:** Next.js App Router, React, TypeScript, React Flow.
- **Application backend:** Next.js Server Components for server-rendered
  reads, Server Actions for mutations, and Route Handlers for HTTP APIs
  and webhooks.
- **Hosting:** Vercel, using the Node.js runtime for backend code.

## Managed Backend

- **Backend platform:** Supabase.
- **Database:** Supabase-managed PostgreSQL.
- **Database access:** Supabase JavaScript client with generated
  TypeScript database types. No separate ORM initially.
- **Schema migrations:** Version-controlled SQL migrations managed
  through the Supabase CLI.
- **Authentication:** Supabase Auth with cookie-based Next.js sessions
  through @supabase/ssr.
- **Authorization:** PostgreSQL grants and Row Level Security policies
  for exposed application data; server-side checks for privileged actions.
- **File storage:** Supabase Storage when uploads are introduced.
- **Privileged credentials:** Server-only; ordinary user requests use
  the authenticated user's session.

## Supporting Services

- **Email:** Resend for Supabase Auth SMTP and transactional app email.
- **Error monitoring:** Sentry for browser and server errors.

## Delivery and Environments

- **Source control:** GitHub.
- **Deployments:** Vercel Git integration with pull-request previews.
- **Environments:** Separate Supabase staging and production projects.
  Local development and Vercel previews use staging credentials.
- **CI:** GitHub Actions for application checks and migration validation.
- **Production releases:** Validate migrations in staging, apply
  backward-compatible migrations, then release the application.
- **Initial region:** Frankfurt for Supabase and Vercel server functions.
- **Production plans:** Vercel Pro and Supabase Pro.
- **Recovery:** Supabase daily database backups, with a restore procedure
  tested before launch. Storage object backups require a separate plan
  if uploads become part of the product.

## Add Only When Required

- AI inference providers and model selection.
- Billing and subscriptions.
- Durable background jobs.
- Product analytics, realtime subscriptions, and additional search services.
