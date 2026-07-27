# Backend API Specification

## Base conventions

- Base path: `/api/v1`
- JSON request and response bodies.
- OpenAPI documentation generated from source annotations and validated in CI.
- Cursor pagination for large feeds; page pagination may be used for bounded admin tables.
- Standard error envelope with `code`, `message`, `details`, `requestId`.
- Idempotency keys for registration submission and selected write operations.

## Public endpoints

- `GET /public/config`
- `GET /public/home`
- `GET /public/events`
- `GET /public/events/:slug`
- `GET /public/events/:eventId/speakers`
- `GET /public/events/:eventId/schedule`
- `GET /public/events/:eventId/documents`
- `GET /public/news`
- `GET /public/news/:slug`
- `GET /public/pages/:slug`
- `POST /public/events/:eventId/registrations`
- `GET /me/registrations`
- `GET /me/registrations/:id`
- `GET /me/registrations/:id/qr`
- `POST /me/registrations/:id/cancel`

## Administration endpoints

### Events

- `GET /admin/events`
- `POST /admin/events`
- `GET /admin/events/:id`
- `PATCH /admin/events/:id`
- `POST /admin/events/:id/publish`
- `POST /admin/events/:id/unpublish`
- `POST /admin/events/:id/duplicate`
- `DELETE /admin/events/:id`

### Registration forms

- `GET /admin/events/:eventId/form`
- `PUT /admin/events/:eventId/form/draft`
- `POST /admin/events/:eventId/form/publish`
- `GET /admin/events/:eventId/form/versions`

### Registrations

- `GET /admin/registrations`
- `GET /admin/registrations/:id`
- `PATCH /admin/registrations/:id/status`
- `POST /admin/registrations/bulk-status`
- `POST /admin/registrations/:id/notes`
- `POST /admin/registrations/export`
- `POST /admin/registrations/import`

### Check-in

- `POST /admin/check-in/validate`
- `POST /admin/check-in/manual`
- `POST /admin/check-in/:attendanceId/undo`
- `GET /admin/events/:eventId/check-in/summary`

### CMS

- CRUD endpoints for pages, homepage layouts, news, media, documents, menus, speakers, sponsors, partners and FAQs.
- Draft and published revisions must use explicit publish endpoints.

### Security and operations

- `POST /auth/login`
- `POST /auth/refresh`
- `POST /auth/logout`
- `POST /auth/logout-all`
- `GET /admin/users`
- `GET /admin/roles`
- `GET /admin/audit-logs`
- `GET /health/live`
- `GET /health/ready`

## Authorization

Each administration endpoint declares a permission and scope. Service-layer authorization must verify organization and event ownership; hiding buttons in the UI is not sufficient.

## Validation

- Reject unknown fields on sensitive commands.
- Normalize phone and email values without destroying original user input.
- Validate file metadata before accepting upload URLs.
- Validate all builder schemas against versioned JSON schemas.

## Rate limits

Apply stricter limits to login, token refresh, registration submission, file upload initialization and public search. Limits should combine IP, authenticated identity and organization context where appropriate.
