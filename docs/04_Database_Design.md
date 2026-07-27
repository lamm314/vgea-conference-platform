# Database Design

## Conventions

- PostgreSQL with Prisma migrations.
- UUID primary keys unless a measured reason requires another strategy.
- `created_at`, `updated_at` and optional `deleted_at` on business entities.
- Store timestamps in UTC and render using organization/event timezone.
- Use database constraints for uniqueness and referential integrity.
- Use JSON only for validated flexible schemas; do not replace relational modeling with arbitrary JSON.

## Core entity groups

### Identity and tenancy

- `organizations`
- `users`
- `user_identities`
- `roles`
- `permissions`
- `role_permissions`
- `user_role_assignments`
- `refresh_sessions`

### Events

- `events`
- `event_translations`
- `event_categories`
- `event_category_assignments`
- `event_days`
- `event_tracks`
- `sessions`
- `session_speakers`
- `venues`
- `speakers`
- `sponsors`
- `sponsor_levels`
- `event_sponsors`
- `partners`
- `event_partners`
- `faqs`

### Registration

- `registration_forms`
- `registration_form_versions`
- `registration_fields`
- `registrations`
- `registration_answers`
- `registration_status_history`
- `registration_tags`
- `registration_tag_assignments`
- `registration_notes`
- `consent_records`
- `waitlist_entries`
- `attendance_records`
- `qr_tokens`

### Content

- `pages`
- `page_versions`
- `homepage_layouts`
- `homepage_layout_versions`
- `news_articles`
- `news_categories`
- `media_assets`
- `documents`
- `menus`
- `menu_items`
- `organization_settings`
- `theme_settings`

### Operations

- `notification_templates`
- `notification_campaigns`
- `notification_deliveries`
- `export_jobs`
- `import_jobs`
- `certificates`
- `certificate_templates`
- `audit_logs`
- `webhook_deliveries`
- `system_jobs`

## Important relations and constraints

- An organization owns events, content, users and settings.
- Event slug is unique within an organization.
- A registration belongs to exactly one event and one form version.
- Form versions are immutable after receiving a registration.
- One active registration per event and configured identity key, unless duplicates are explicitly allowed.
- One active attendance record per registration and event entrance rule.
- QR tokens store a digest or signed-token identifier, not unnecessary plaintext secrets.
- Audit logs reference actor, organization, action, target type/id, timestamp, IP metadata and a redacted change summary.

## Required indexes

- Event publication status, start date and organization.
- Registration event/status/submitted time.
- Normalized phone/email hashes where duplicate detection is enabled.
- Attendance event/check-in time.
- News publication status/date.
- Audit organization/actor/time/action.
- Full-text indexes for public event and news search where PostgreSQL search is used.

## Retention

Retention periods must be configurable by data category. Permanent deletion requires authorization, an audit event and removal from derived export/storage locations where feasible.
