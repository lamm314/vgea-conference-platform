# VGEA Conference Platform — Project Overview

## 1. Purpose

Build a dynamic conference ecosystem for the Vietnam Green Energy Association (VGEA) with two user-facing products sharing one backend and database:

1. A public Zalo Mini App for discovering and registering for conferences.
2. A secure administration portal for managing content, registrations, check-in, reports, exports, notifications and platform settings.

## 2. Main endpoints

- Administration portal: `https://hoithao-hiephoi.vkesys.com`
- Target application server: `192.168.40.94:3003`
- Official association website: `https://vgea.com.vn/`

The public domain, private IP, port, database credentials, Zalo credentials and all secrets must be configured through environment variables.

## 3. Product principles

- No event data is hardcoded.
- All public content is CMS-managed.
- The Mini App and Admin Portal use versioned REST APIs.
- The system is mobile-first and optimized for the Zalo WebView.
- The architecture is prepared for multiple organizations and unlimited events.
- Every sensitive administrative action is permission-controlled and audited.

## 4. Proposed technical stack

### Public Zalo Mini App

- React
- TypeScript
- Vite
- Zalo Mini App SDK and ZMP UI
- TanStack Query
- React Hook Form + Zod

### Administration portal

- Next.js
- TypeScript
- Tailwind CSS
- Accessible component primitives
- TanStack Query and TanStack Table
- Drag-and-drop page and form builders

### Backend

- NestJS
- PostgreSQL
- Prisma ORM
- Redis
- BullMQ-compatible job processing
- JWT access and refresh tokens
- OpenAPI/Swagger

## 5. Documentation map

- `01_Product_Requirements.md`: product scope, actors, workflows and acceptance criteria.
- `02_UI_UX_Design_System.md`: visual system and detailed interface guidance.
- `03_Information_Architecture_User_Flows.md`: navigation and user flows.
- `04_Database_Design.md`: entities, relations and database rules.
- `05_Backend_API_Specification.md`: API conventions and endpoint catalogue.
- `06_Admin_Portal.md`: administration modules and screens.
- `07_Zalo_Mini_App.md`: public Mini App screens and behavior.
- `08_Deployment_Operations.md`: deployment, security, backup and monitoring.
- `09_Testing_QA.md`: testing strategy and quality gates.
- `10_AI_Coding_Rules_Master_Prompt.md`: implementation rules for Codex or another coding agent.

## 6. Delivery strategy

Implementation must be iterative. For each module:

1. Confirm requirements and data model.
2. Implement backend contracts.
3. Implement frontend screens.
4. Add automated tests.
5. Run type checks, linting and tests.
6. Fix all defects.
7. Update documentation.
8. Mark the module complete only after meeting its Definition of Done.
