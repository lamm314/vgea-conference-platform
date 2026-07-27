# UI/UX Design System

## 1. Design direction

The product should use the reference theme below as visual inspiration:

`http://preview.themeforest.net/item/inconfe-conference-and-event-summit-elementor-template-kit/full_screen_preview/64104189`

The implementation must not copy the reference theme's source code, copyrighted images, icons or proprietary assets. Recreate the visual principles with original components and VGEA-approved assets.

The design language should communicate:

- an important professional conference;
- modern energy and sustainability;
- institutional trust;
- clear event information;
- energetic but controlled visual movement;
- strong calls to register without making the interface feel like an advertisement.

## 2. Visual characteristics inspired by the reference

### 2.1 High-impact hero composition

Use a tall, immersive hero that combines event imagery, oversized editorial headings, event metadata and a clear registration action. The hero may use layered shapes, gradients, subtle grid textures and controlled decorative elements.

For the Zalo Mini App, reduce decorative density and maintain text legibility within a narrow mobile viewport. The primary content must remain visible without depending on hover effects.

### 2.2 Alternating visual rhythm

Alternate light content sections with darker or brand-colored feature sections. The sequence should create a conference landing-page rhythm rather than a continuous list of identical cards.

### 2.3 Editorial typography

Headings should be bold and compact, with deliberate line breaks. Supporting text should be neutral and highly readable. Dates and small labels may use uppercase styling with increased letter spacing.

### 2.4 Rounded media cards

Use large event and speaker imagery with medium-to-large corner radii, clipped overlays and restrained shadows. Cards should have clear hierarchy: category, title, metadata and action.

### 2.5 Timeline and schedule emphasis

The agenda should resemble a curated event program. Day tabs, track labels, time blocks, speaker thumbnails and room details must be visually scannable.

### 2.6 Sponsor and partner presentation

Logos should appear in a consistent monochrome or neutral treatment where possible, transitioning to full color only where interaction is supported. Mobile layouts should use balanced grids and avoid tiny unreadable logos.

## 3. Design tokens

All values must be exposed through centrally managed design tokens. CMS theme settings may select from validated token values but may not inject arbitrary CSS.

### 3.1 Color roles

- `brand.primary`: VGEA primary brand color.
- `brand.secondary`: supporting energy/sustainability color.
- `accent`: high-visibility event action color.
- `surface.default`: primary page background.
- `surface.muted`: secondary section background.
- `surface.inverse`: dark conference section.
- `text.primary`: high-emphasis text.
- `text.secondary`: supporting content.
- `text.inverse`: text on dark surfaces.
- `border.default`: standard border.
- `status.success`, `status.warning`, `status.error`, `status.info`.

Do not rely on color alone to communicate status.

### 3.2 Typography scale

Recommended responsive roles:

- Display XL: hero event title.
- Display L: major landing-page statement.
- Heading 1: page title.
- Heading 2: section title.
- Heading 3: card and subsection title.
- Body L: introduction and key descriptions.
- Body M: normal content.
- Body S: metadata and helper text.
- Label: tabs, tags and controls.

Use no more than two production font families. Provide Vietnamese glyph coverage and reliable system fallbacks.

### 3.3 Spacing

Use an 8-point base system with compact exceptions for icons and form internals. Typical values: 4, 8, 12, 16, 24, 32, 48, 64 and 96 px.

### 3.4 Radius

- Small controls: 8 px.
- Inputs and buttons: 10–12 px.
- Standard cards: 16 px.
- Feature cards and hero media: 20–28 px.
- Pills: fully rounded.

### 3.5 Elevation

Use borders for most administrative surfaces. Use soft shadows for floating public cards, overlays and dialogs. Avoid strong shadows on every element.

## 4. Public Mini App layout

### 4.1 Header

The mobile header contains the VGEA mark, page title when relevant and one contextual action. Avoid desktop-style mega navigation. Use a bottom navigation for Home, Events, News and My Registrations when supported by the information architecture.

### 4.2 Home hero

Required content:

- background image or approved video poster;
- event category or organizer label;
- event title;
- date and location;
- primary Register CTA;
- secondary View details CTA;
- optional countdown for a featured upcoming event.

The hero should occupy approximately 70–85% of the initial mobile viewport while keeping the primary CTA reachable. Use a dark image overlay that adapts to image luminance.

### 4.3 Featured event section

Use one prominent horizontal or stacked card rather than multiple equal cards. Include cover, date badge, title, short summary, location, capacity state and CTA.

### 4.4 Upcoming event cards

Mobile card anatomy:

1. 16:9 or 4:3 cover image.
2. Category chip and registration status.
3. Event title, limited to three lines.
4. Date, time and location.
5. Seats remaining only when configured.
6. Registration or details action.

### 4.5 About VGEA

Use a strong statement, concise association introduction, one representative image and numeric impact indicators. Link to a dedicated About page for full information.

### 4.6 Statistics

Use two-column mobile counters and a four-column desktop layout. Statistics must include a label and context; do not display unexplained large numbers.

### 4.7 Speakers

Use portrait cards with image, full name, role and organization. Speaker detail appears in a full screen or page, not in a cramped tooltip.

### 4.8 Agenda preview

Provide date tabs followed by compact schedule cards. A session card shows start/end time, title, track/room and speaker. Highlight current or next session only when real-time event state is reliable.

### 4.9 News and association activities

Use one featured article and a compact list of recent articles. Show publication date and category. Article pages must support rich content, media and related events.

### 4.10 Footer/contact

In the Mini App, use a compact contact block rather than a large website footer. Include official address, hotline/email, website link and relevant Zalo OA action.

## 5. Event detail screen

Recommended order:

1. Hero and event identity.
2. Sticky registration action.
3. Essential date, time, venue and organizer facts.
4. Overview and objectives.
5. Target audience and participation benefits.
6. Agenda.
7. Speakers.
8. Venue/map and access instructions.
9. Documents.
10. Sponsors and partners.
11. FAQs.
12. Contact and related events.

The sticky CTA must not obstruct Zalo system controls or important content.

## 6. Registration experience

- Show progress only for forms with multiple meaningful steps.
- Place identity/contact fields before organizational and custom fields.
- Validate inline after interaction, not on every initial keystroke.
- Preserve input when the app is temporarily backgrounded where feasible.
- Present consent text with a link to the full privacy policy.
- On success, show registration reference, current status and next action.
- Do not imply approval when the event uses manual approval.

## 7. Administration portal layout

### 7.1 Shell

Desktop-first responsive shell with collapsible left navigation, top bar, breadcrumbs, environment indicator, notification center and user menu.

### 7.2 Dashboard

Use a restrained analytics layout:

- four to six primary KPI cards;
- one registration trend chart;
- one capacity/attendance visualization;
- upcoming events table;
- recent activity panel;
- integration or job warnings.

Avoid decorative charts without an operational decision attached.

### 7.3 Data tables

Tables must support server-side pagination, filters, saved views, column visibility, row selection and export of the filtered set. Personal fields require permission-aware columns.

### 7.4 Editors and builders

Use a three-area pattern where appropriate:

- left: available blocks or form fields;
- center: page/form canvas;
- right: selected block settings.

All changes require schema validation. Support draft, preview, publish and revision history.

### 7.5 Forms

Use logical sections, clear labels, helper text and a persistent save action for long forms. Warn about unsaved changes. Destructive actions require confirmation and clearly name the affected object.

## 8. Motion and interaction

- Use 150–250 ms transitions for standard controls.
- Use 300–500 ms for major public section reveals.
- Avoid parallax and continuous motion in the Mini App.
- Provide reduced-motion alternatives.
- Skeletons should resemble final content geometry.
- Do not block the full screen for background export or notification jobs.

## 9. Responsive breakpoints

Design mobile-first for public screens. Validate at minimum:

- 320 px narrow mobile;
- 375–430 px common phones;
- tablet portrait and landscape;
- 1280 px administration desktop;
- 1440 px and above wide desktop.

## 10. Required states

Every component must define:

- default;
- hover where applicable;
- focus-visible;
- active/selected;
- disabled;
- loading;
- empty;
- validation error;
- API error;
- permission denied;
- offline or retry state where relevant.

## 11. Accessibility checklist

- Semantic headings follow a logical hierarchy.
- Inputs have programmatic labels.
- Error summaries link to invalid fields.
- Focus is trapped and restored for dialogs.
- Touch targets are at least 44 by 44 CSS pixels where practical.
- Text contrast meets WCAG AA targets.
- Important actions are usable without hover.
- Data visualizations have text equivalents.
