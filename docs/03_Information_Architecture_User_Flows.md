# Information Architecture and User Flows

## Public Mini App navigation

- Home
- Events
  - Featured
  - Upcoming
  - Ongoing
  - Past
  - Categories
- Event Detail
- News
- About VGEA
- Membership
- Contact
- My Area
  - My Registrations
  - QR Codes
  - Certificates
  - Saved Events
  - Notifications
  - Profile

## Administration navigation

- Dashboard
- Events
  - Events
  - Categories
  - Agenda
  - Speakers
  - Sponsors and Partners
- Registrations
  - All Registrations
  - Check-in
  - Waitlists
  - Imports
  - Exports
- Communications
  - Templates
  - Campaigns
  - Delivery Logs
- Content
  - Homepage
  - Pages
  - News
  - Media
  - Documents
  - Menus
- Reports
- Users and Roles
- Audit Logs
- Integrations
- Settings

## Primary flows

### Event discovery and registration

Open Mini App → Browse/search → Event detail → Register → Authenticate/consent → Complete dynamic form → Submit → Receive reference/status → Receive QR when eligible → View in My Registrations.

### Event creation

Login → Events → Create → Enter core details → Configure content → Build registration form → Set capacity and approval rules → Add agenda/speakers → Preview → Publish/schedule → Monitor registrations.

### Registration review

Registrations → Select event/view → Apply filters → Open registration → Review answers/history → Approve, waitlist or reject → Record reason where required → Trigger configured communication.

### Check-in

Select assigned event → Open scanner → Scan signed QR → Server validates registration/event/status → Record idempotent check-in → Show success or actionable warning → Allow reasoned undo based on permission.

### Export

Open registrations/report → Apply filters and visible fields → Request export → Validate permission → Queue job → Notify when ready → Download time-limited file → Record audit event.

## URL strategy

Public entities use stable slugs and IDs. Deep-link routes must not expose personal information. Admin routes use opaque IDs for editing. All routes must support permission-aware 403 and not-found states.
