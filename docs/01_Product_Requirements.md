# Product Requirements Document

## 1. Product statement

VGEA Conference Platform is a centralized system for publishing conferences, accepting registrations, communicating with attendees, operating check-in and producing reports. It replaces fragmented forms, spreadsheets and manual communication with a single source of truth.

## 2. Business objectives

- Let a visitor find and register for a relevant event inside Zalo in less than two minutes.
- Let an authorized administrator create and publish an event without changing source code.
- Consolidate registrations and attendee history in one database.
- Support filtered exports to XLSX, CSV and print-ready PDF.
- Improve event operations through QR check-in, capacity controls, waitlists and live statistics.
- Present VGEA information, news, activities and official contact details consistently with `vgea.com.vn`.
- Prepare the product for reuse across multiple associations and event organizers.

## 3. Actors

### Visitor

Can browse public content, search events, view event details and share deep links.

### Attendee

Can register, receive confirmation, view registration status, access a personal QR code, save events, view notifications and download permitted materials.

### Check-in staff

Can scan or manually validate attendee check-in for assigned events, without access to unrelated personal information.

### Content editor

Can manage pages, news, media, banners and public VGEA information but cannot access sensitive registration exports unless separately permitted.

### Event manager

Can create events, configure forms, manage speakers, schedules, capacity, registrations, communications and reports for assigned events.

### Administrator

Can manage platform users, roles, global content and system configuration.

### Super administrator

Can manage organizations, security configuration, integrations, audit logs, API credentials and operational settings.

## 4. Public Mini App requirements

### PR-001 Event discovery

The system shall show featured, upcoming, ongoing and past events according to publication rules.

### PR-002 Event search and filters

Users shall search by keyword and filter by date, category, delivery format, province/city, registration status and organizer.

### PR-003 Deep linking

Every published event shall have a stable shareable path that opens its detail screen directly in the Mini App where supported, with a browser fallback when required.

### PR-004 Event detail

An event detail page shall support title, subtitle, cover media, date/time, venue, map, organizer, summary, rich description, objectives, audience, agenda, speakers, sponsors, documents, FAQs, related news, contact details and registration CTA.

### PR-005 Registration

Registration shall use a dynamic form configured per event. Field types include text, email, phone, select, radio, checkbox, date, textarea, consent and file upload where allowed.

### PR-006 Registration lifecycle

Statuses include draft, submitted, pending review, approved, waitlisted, rejected, cancelled, checked-in and no-show. Status transitions must be recorded.

### PR-007 Capacity and waitlist

The system shall prevent approved registrations from exceeding capacity and shall optionally place additional registrants on a waitlist.

### PR-008 Confirmation and QR

Upon successful submission or approval, according to event configuration, the system shall generate a registration code and signed QR token.

### PR-009 User center

Authenticated users shall see their registrations, status, QR code, event materials, certificates and notification history.

### PR-010 VGEA content

The Mini App shall contain CMS-managed About VGEA, mission, vision, leadership/organization information, membership information, projects, news and contact details.

## 5. Administration portal requirements

### PR-011 Dashboard

The dashboard shall show total and recent registrations, active/upcoming events, capacity utilization, check-in statistics, registration trends, recent activity and integration status. Data must respect permission scope.

### PR-012 Event management

Authorized users can create, edit, duplicate, preview, schedule, publish, unpublish, archive and soft-delete events.

### PR-013 Registration form builder

Authorized users can add, reorder, configure and validate form fields. The form builder supports required fields, option lists, helper text, conditional visibility and consent records.

### PR-014 Registration management

The portal shall provide server-side search, filters, sorting, saved views, column controls, bulk actions, tags, internal notes and status history.

### PR-015 Export center

Authorized users can export the current filtered result set to XLSX and CSV, and generate printable PDF reports. Exports must be auditable and must not expose fields outside the user's permission scope.

### PR-016 Import center

Authorized users can import attendees, speakers, agenda items and selected reference data using validated XLSX/CSV templates. Import results shall show accepted and rejected rows with reasons.

### PR-017 QR check-in

Staff can scan QR codes, search manually, undo an erroneous check-in with a reason and see duplicate or invalid token warnings. The server is the source of truth.

### PR-018 Content management

Authorized editors can manage news, static pages, FAQs, menus, homepage sections, media, documents, partners, sponsors and association information.

### PR-019 Homepage builder

Administrators can enable, disable, reorder and configure supported homepage sections. Configuration shall be stored as validated structured data, not executable HTML or JavaScript.

### PR-020 Speaker and agenda management

Events support multiple days, tracks, sessions and speakers. One speaker may participate in multiple events and sessions.

### PR-021 Communication

Authorized users can create templates and send or schedule event communications using configured channels such as Zalo OA and email. Delivery attempts and outcomes must be recorded.

### PR-022 Reports

Reports include registration funnel, attendee segmentation, capacity, attendance, no-show rate, source attribution, form answers and export history.

### PR-023 Users and RBAC

The system shall support configurable roles and granular permissions, including organization and event scope.

### PR-024 Audit log

Login events, data changes, exports, imports, permission changes, bulk actions and communications must be written to an immutable application audit trail.

## 6. Core business rules

- Published event slugs are unique per organization.
- Unpublished events are not visible through public APIs.
- Personal data is returned only when required for an authorized workflow.
- A registration must preserve the event form schema version used at submission time.
- Check-in is idempotent; repeated scans do not create multiple attendance records.
- Exports use queued jobs for large datasets and record the initiator, filters, fields and completion state.
- Deleting business records uses soft deletion unless a documented retention workflow authorizes permanent deletion.
- User consent text and timestamp must be retained with the registration.

## 7. Non-functional requirements

### Performance

- Cached public read endpoints target a p95 response time below 300 ms under normal operating load.
- Paginated administration tables must not fetch unbounded datasets.
- Images use responsive sizes and modern formats where practical.

### Security

- TLS is required for public traffic.
- Passwords use a modern adaptive password hash.
- Access tokens are short-lived; refresh tokens are rotatable and revocable.
- Input validation occurs at API boundaries.
- Uploads are validated by extension, MIME type, size and storage policy.
- Rate limits protect authentication, registration and public search endpoints.

### Accessibility

- Meaningful contrast, keyboard navigation, visible focus states and accessible labels are required.
- Motion respects reduced-motion preferences.

### Reliability

- Database backups and restore procedures are documented and tested.
- Long-running exports and notifications are queued and retryable.
- Health endpoints distinguish liveness and readiness.

## 8. Success metrics

- At least 80% registration completion among users who begin an eligible form.
- An event manager can configure and publish a standard event without developer intervention.
- A filtered XLSX export of 10,000 registrations completes reliably through the job system.
- Median check-in confirmation is below two seconds under event network conditions.
- No unresolved high-severity security defects at production release.

## 9. Definition of Done

A feature is complete only when:

- requirements and acceptance criteria are implemented;
- authorization and validation are covered;
- TypeScript, lint and automated tests pass;
- empty, loading, error and permission-denied states exist;
- responsive behavior is verified;
- audit behavior is implemented where applicable;
- API and user documentation are updated;
- no placeholder logic or unresolved TODO remains in the delivered scope.
