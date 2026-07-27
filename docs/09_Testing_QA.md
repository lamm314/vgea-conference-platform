# Testing and Quality Assurance

## Quality gates

Every pull request must pass:

- TypeScript type checking;
- linting and formatting checks;
- unit tests;
- relevant integration tests;
- production build;
- migration/schema validation;
- secret and dependency scanning where configured.

## Test layers

### Unit tests

Test domain rules, validation schemas, permission evaluation, status transitions, builder schema parsing, token utilities and export field selection.

### Integration tests

Use a real test database for repositories and API modules. Cover authentication, organization/event scope, registration creation, form-version preservation, status history, check-in idempotency, export job creation and audit writes.

### End-to-end tests

Critical journeys:

1. Administrator creates and publishes an event.
2. User opens the event by deep link and registers.
3. Administrator reviews and approves the registration.
4. User views the valid QR code.
5. Check-in staff scans the code once and receives a duplicate warning on repeat.
6. Authorized administrator exports the filtered registration list.
7. Unauthorized role cannot view or export protected fields.

### UI tests

Test responsive layout, keyboard access, focus behavior, builders, table filters, long Vietnamese content, empty/loading/error states and unsaved-change warnings.

### Performance tests

Measure public event lists, event detail, registration submission, admin pagination, QR validation and 10,000-row export jobs. Avoid unrealistic production claims without recorded test conditions.

### Security tests

Cover broken object-level authorization, role escalation, cross-organization access, injection, XSS in CMS content, malicious upload metadata, token reuse, refresh-token rotation, rate limits and sensitive-data leakage.

## Test data

Use deterministic factories and seeds. Never use production personal data in development or test environments.

## Release acceptance

A release candidate requires zero open critical/high-severity defects, documented handling of medium defects, successful smoke tests in the target environment and verified backup/rollback readiness.
