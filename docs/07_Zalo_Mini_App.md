# Zalo Mini App Specification

## Purpose

Provide a fast, mobile-first interface for VGEA conference discovery, registration and attendee self-service inside Zalo.

## Main screens

- Splash/bootstrap state
- Home
- Event listing
- Event detail
- Registration form
- Registration success/status
- My registrations
- QR code detail
- News listing/detail
- About VGEA
- Membership information
- Contact
- Notifications
- Profile and consent settings

## Zalo integration

- Use the official Zalo Mini App SDK for supported identity and platform capabilities.
- Request only permissions required by the current user action.
- Do not assume phone number or profile information is always available.
- Provide clear fallback form fields and error handling when permission is denied.
- Deep links must resolve to event detail or a safe landing route.
- OA actions and notification integration must be configurable by environment and organization settings.

## Dynamic rendering

The home page consumes a validated section schema from the backend. Supported initial section types:

- hero
- featured-event
- upcoming-events
- event-categories
- about-vgea
- statistics
- speakers
- agenda-preview
- sponsors
- partners
- news
- gallery
- faq
- contact

Unknown section types must fail safely and be reported, not execute arbitrary content.

## Registration behavior

- Load the active published form version for the event.
- Persist a temporary local draft for recoverable navigation interruptions.
- Validate on client and server.
- Submit with an idempotency key.
- Show the actual status returned by the API.
- Display QR only when the registration state permits it.
- Allow cancellation only under event rules.

## Performance

- Lazy-load noncritical sections.
- Use responsive images and cached query data.
- Avoid large animation libraries.
- Keep initial JavaScript and image payloads minimal.
- Provide skeletons for event lists and detail content.

## Error handling

Define explicit states for no network, slow network, expired session, denied Zalo permission, full event, closed registration, duplicate registration, invalid deep link and unpublished event.

## Privacy

Show privacy and consent information before collecting personal data. Do not place personal data in URLs, analytics events or client logs.
