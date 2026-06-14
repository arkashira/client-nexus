# STORIES.md

## Epic 1 – Core CRM Foundations (MVP)

| # | User Story |
|---|------------|
| 1 | **As a small‑business owner**, I want to **create and edit client profiles** (name, contact, service history), so that I can keep accurate records of every customer. |
| 2 | **As a sales representative**, I want to **log interactions (calls, emails, meetings)** against a client record, so that the whole team sees the latest communication context. |
| 3 | **As a support agent**, I want to **view a timeline of all client activities**, so that I can quickly understand the client’s journey and respond appropriately. |
| 4 | **As a system administrator**, I want to **define custom fields for client records**, so that the CRM can adapt to industry‑specific data without code changes. |
| 5 | **As a business owner**, I want to **search and filter clients** by any field (e.g., location, last interaction date), so that I can segment my customer base for targeted outreach. |

### Acceptance Criteria (applies to all stories in Epic 1)

- All CRUD operations are performed via a responsive web UI.
- Data is persisted in the PostgreSQL database with proper indexing for search fields.
- Validation errors are shown inline with clear messages.
- UI follows the company design system (components, spacing, color palette).
- All actions are logged for audit purposes (user, timestamp, operation).

---

## Epic 2 – Communication & Automation

| # | User Story |
|---|------------|
| 6 | **As a sales representative**, I want to **schedule follow‑up reminders** for a client, so that I never miss a promised call or email. |
| 7 | **As a support agent**, I want to **send templated email replies** directly from a client record, so that I can respond faster and maintain consistent messaging. |
| 8 | **As a marketing manager**, I want to **trigger automated email sequences** based on client status changes (e.g., “new lead” → “welcome series”), so that leads are nurtured without manual effort. |
| 9 | **As a system administrator**, I want to **configure webhook endpoints**, so that external tools (e.g., Slack, accounting software) receive real‑time updates when a client record changes. |

### Acceptance Criteria (Epic 2)

- Reminder UI shows date‑picker, time‑zone handling, and optional recurrence.
- Email templates support merge fields (e.g., `{{client.name}}`) and are editable via a WYSIWYG editor.
- Automation engine provides a visual rule builder (trigger → condition → action) and persists rules in the DB.
- Webhooks are sent with signed payloads; delivery failures are retried up to 3 times and logged.
- End‑to‑end tests cover the full flow: trigger → action → external system receipt.

---

## Epic 3 – Reporting & Insights

| # | User Story |
|---|------------|
| 10 | **As a business owner**, I want to **view a dashboard of key metrics** (total clients, new leads this month, average response time), so that I can gauge business health at a glance. |
| 11 | **As a sales manager**, I want to **export client lists and interaction logs** to CSV, so that I can perform offline analysis or share with stakeholders. |
| 12 | **As a support lead**, I want to **generate a report of tickets resolved per agent**, so that I can assess team performance and identify training needs. |

### Acceptance Criteria (Epic 3)

- Dashboard widgets are configurable (add/remove, reorder) and refresh automatically every 5 minutes.
- Export respects current filters and includes all visible columns.
- Reports are generated on demand, with progress indicator for datasets > 10 k rows, and downloadable as CSV.
- All reports respect user permissions (e.g., only managers can see team‑wide performance data).

---

## Epic 4 – Permissions & Security (Post‑MVP)

| # | User Story |
|---|------------|
| 13 | **As an admin**, I want to **assign role‑based permissions** (view, edit, delete) to users per module, so that data access follows the principle of least privilege. |
| 14 | **As a compliance officer**, I want to **export an audit log** of all data changes, so that we can satisfy regulatory requirements. |
| 15 | **As a user**, I want to **enable two‑factor authentication (2FA)** on my account, so that my login is more secure. |

### Acceptance Criteria (Epic 4)

- Role definitions are stored in the DB and can be edited via an admin UI.
- Permission checks are enforced on every API endpoint and UI component.
- Audit log entries include user ID, timestamp, affected entity, and before/after snapshots.
- 2FA supports TOTP apps (e.g., Google Authenticator) with QR‑code enrollment flow.
- Security tests (penetration, OWASP Top 10) are part of the CI pipeline.

---

## Prioritization Order (MVP)

1. Epic 1 – Core CRM Foundations (Stories 1‑5)  
2. Epic 2 – Communication & Automation (Stories 6‑9)  
3. Epic 3 – Reporting & Insights (Stories 10‑12)  

*Epics 4 (Permissions & Security) will be addressed after the MVP to ensure a solid, usable product is in the hands of early customers while still planning for enterprise‑grade controls.*
