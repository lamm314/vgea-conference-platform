# Administration Portal Specification

## Access

- Domain: `https://hoithao-hiephoi.vkesys.com`
- Target server: `192.168.40.94:3003`
- Public DNS and reverse proxy must terminate TLS and forward only approved traffic.

## Modules

### Dashboard

KPI cards, registration trend, capacity, check-in progress, upcoming events, recent actions, failed jobs and integration status.

### Event management

Wizard or sectioned editor for identity, dates, venue, content, registration rules, form, agenda, speakers, sponsors, documents, SEO, sharing and publication.

### Registration management

Permission-aware table with filters for event, status, date, tags, attendance, company, province/city and custom answers. Support saved views, bulk status updates, notes and detail history.

### Export center

- Export XLSX, CSV and PDF.
- Select fields and current filters.
- Mask or omit sensitive fields based on permission.
- Queue large exports.
- Provide time-limited download links.
- Log requester, fields, filters, row count and download events.

### Import center

Download templates, upload files, map columns, validate rows, preview changes, confirm import and download error results.

### QR check-in

Event selector, scanner mode, manual search, recent scan history, success/error feedback, duplicate warning, offline queue indicator and real-time totals.

### CMS

Manage homepage sections, static pages, news, menus, VGEA profile, contact details, partners, sponsors, media and documents. Content supports draft, preview, publish and revision rollback.

### Form builder

Drag-and-drop field ordering with field settings, validation rules, conditional visibility, consent blocks and preview. Published form versions become immutable when used by submissions.

### Agenda and speakers

Multiple event days and tracks, session editing, conflict warnings, speaker assignments and printable agenda output.

### Communications

Template editor, audience filters, preview, test send, scheduling, delivery logs, retry and cancellation where the channel supports it.

### Reports

Registration funnel, approval status, attendee segmentation, source attribution, capacity utilization, attendance, no-show, session interest and operational exports.

### User and access management

Users, roles, permissions, event assignments, account status, session revocation and permission-change audit history.

### Settings

Organization profile, theme tokens, Zalo configuration, OA integration, SMTP/email, storage, map provider, export retention, privacy settings and feature flags.

## Table requirements

- Server-side data operations.
- Search debouncing.
- Filter chips and clear-all action.
- Persisted column preferences per user.
- Accessible selection and keyboard navigation.
- Empty, loading, error and permission-denied states.

## Destructive actions

Soft delete by default. Confirmation must identify the affected record and consequences. High-risk actions require a reason and may require elevated permission.
