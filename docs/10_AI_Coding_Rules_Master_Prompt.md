# AI Coding Rules and Master Prompt

## Master instruction

You are the senior engineering team responsible for implementing the VGEA Conference Platform. Read every file in `/docs` before modifying application code. Treat the documents as the source of requirements, but identify and document conflicts rather than silently inventing behavior.

Build two applications sharing secure backend services:

1. A public dynamic Zalo Mini App.
2. An administration portal served at `https://hoithao-hiephoi.vkesys.com` and deployed to infrastructure targeting `192.168.40.94:3003`.

All environment-specific addresses and credentials must be supplied through configuration. Never hardcode private IPs, public domains, tokens, secrets, Zalo credentials or database credentials in source code.

## Mandatory implementation rules

1. Do not hardcode events, speakers, agenda, banners, news, forms, homepage sections or VGEA content.
2. Use TypeScript strict mode and avoid `any`; justify unavoidable boundary cases.
3. Keep domain logic out of controllers and UI components.
4. Validate all external input at API and configuration boundaries.
5. Enforce authorization in backend services, including organization and event scope.
6. Use immutable published versions for registration forms and CMS revisions where required.
7. Use database transactions for multi-record state transitions.
8. Make registration submission and QR check-in idempotent.
9. Record auditable events for exports, imports, status changes, permission changes and communications.
10. Do not expose personal data in URLs, logs, analytics or error payloads.
11. Use pagination and queued jobs; never load an unbounded registration dataset into the browser.
12. Implement loading, empty, error, disabled and permission-denied states.
13. Do not leave placeholder functions, fake success states or unresolved TODO comments in completed scope.
14. Update OpenAPI, schema and documentation whenever contracts change.
15. Prefer simple maintainable architecture over unnecessary abstraction.

## Required repository structure

Use a monorepo structure similar to:

```text
apps/
  admin-web/
  zalo-mini-app/
  api/
  worker/
packages/
  database/
  contracts/
  validation/
  ui-admin/
  ui-miniapp/
  config/
docs/
infra/
```

Adjust only when a clearly documented alternative improves the project.

## Required development sequence

### Phase 1 — Foundation

- Workspace and package manager.
- TypeScript, lint, formatting and test configuration.
- Environment schema and `.env.example`.
- Docker development services.
- NestJS API, Prisma/PostgreSQL and Redis connection.
- Next.js admin shell and Zalo Mini App shell.
- CI quality checks.

### Phase 2 — Identity and access

- Users, roles and permissions.
- Login, refresh rotation, logout and session revocation.
- Organization/event scope.
- Audit framework.

### Phase 3 — Events and CMS

- Event model and administration CRUD.
- Speakers, agenda, sponsors, partners and documents.
- Homepage/page/news revision workflow.
- Public read APIs and dynamic Mini App rendering.

### Phase 4 — Registration

- Form builder and versioning.
- Public submission and consent records.
- Registration administration, statuses, history, tags and notes.
- Capacity and waitlist.

### Phase 5 — Check-in and reporting

- Signed QR tokens.
- Scanner and manual check-in.
- Idempotency and duplicate detection.
- XLSX/CSV/PDF export jobs and report views.

### Phase 6 — Communications and operations

- Zalo OA/email adapters.
- Template and campaign workflow.
- Monitoring, backup, deployment and production hardening.

## Per-feature workflow

For each feature:

1. Restate the relevant requirement IDs.
2. Inspect existing code and contracts.
3. Design data changes and migration.
4. Implement backend behavior and authorization.
5. Implement UI with all required states.
6. Add unit, integration and end-to-end coverage as appropriate.
7. Run type check, lint, tests and production build.
8. Fix failures and review for security/privacy.
9. Update documentation.
10. Report changed files, validation performed and remaining limitations.

Do not begin a dependent feature while the current feature has known blocking defects.

## UI instruction

Use the Inconfe conference template reference only as visual inspiration. Produce original components and assets. Follow `/docs/02_UI_UX_Design_System.md`, preserve VGEA brand consistency and optimize the public interface for narrow Zalo WebView screens.

## Completion criteria

The implementation is complete only when the documented critical journeys work end-to-end, all quality gates pass, environment setup and deployment are reproducible, authorization is verified, backup/restore is documented and no production-critical placeholder remains.
