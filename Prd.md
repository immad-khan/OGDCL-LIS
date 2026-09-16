## Legal Information System

Product Requirements Document

LIS / v1.0 / Approval Draft

## A SINGLE, AUTHORITATIVE LITIGATION RECORD

## From case registration to executive visibility.

An on-premise legal operations platform for Oil & Gas Development Company Limited, designed for an isolated Head Office intranet.

27 SCREENS

Administrator + Legal User

For Review & Approval

MVP target 16 September 2026

Deployment On-premise | Isolated intranet | Head Office only

Target server Intel i7 | 32 GB RAM | 1 TB storage

Windows Server 2019 environment

## 02 LOGIN ROLES

OFFLINE FIRST

MVP prototype delivery

No external runtime calls

Phase 2: live integrations and extended governance.


## MANDATE & DOCUMENT BASELINE

## 1 | Document Control

| Field | Value |
| --- | --- |
| Product name | OGDCL Legal Information System (LIS) |
| Client | Oil & Gas Development Company Limited — Law & Legal Services |
|   | Directorate |
| Document version | v1.0 (Approval Draft) |
| Status | For Review & Approval |
| Deployment model | On-premise, isolated intranet, Head Office only |
| Target server | Intel i7, 32 GB RAM, 1 TB storage; Windows Server 2019 environment |
| MVP target date | 16 September 2026 (16-09-2026) |
| Regulatory references Petroleum Division letter dated 4 September 2026 (04-09-2026): |   |
|   | Nature/Type of Case taxonomy; letter dated 31 August 2026 (31-08-2026): |
|   | Clubbing/Linking of cases |

## 2 | Executive Summary

The OGDCL Legal Information System (LIS) is an on-premise, isolated-intranet web application that centralizes the Law & Legal Services Directorate’s end-to-end litigation lifecycle — from case registration through hearing diary updates, financial exposure tracking, and executive reporting.

The system is designed to run with no internet connectivity, using a limited number of authorized Legal

Users for all operational work and a single Administrator who manages login accounts and audit visibility. All other stakeholders, including departments and ministry contacts, receive updates via SMTP email only and are not given login access.

The system includes 5-phase future-ready integration placeholders (Court Integration and e-Office), whose backends will be connected when OGDCL provides API/data feeds.

## Core operating boundary

Legal Users perform operational work. The Administrator manages accounts and views audit records only. External stakeholders receive email; they do not log in.


## OUTCOMES & ACCESS MODEL

## 3 | Objectives

- 1. Provide a single, authoritative record of all OGDCL litigation.

- 2. Enable executive visibility through a dashboard covering ageing, financial exposure, compliance status, and forthcoming hearings.

- 3. Reduce manual effort through guided workflows: 5-step case registration, diary entry, and bulk CSV import.

- 4. Ensure compliance with Petroleum Division taxonomy directives (4 September 2026) and clubbing/linking directives (31 August 2026).

- 5. Maintain a reliable audit trail of all data entries and uploads.

- 6. Enable offline, secure, fully self-hosted operation.

- 7. Provide a foundation for Phase 2 integrations with court websites and e-Office without redesign.

## 4 | Users & Roles

## Two login-enabled roles only

One Administrator account and a small, trusted group of Legal Users. No departmental, ministry, or external-counsel login access.

## 4.1 Administrator (1 account)

| Capability | Detail |
| --- | --- |
| User account management | Create, edit, disable/enable, and reset passwords. |
| Login credential control | Only accounts created by the Administrator can log in. |
| Activity & upload audit | View-only: who uploaded what data and when. |
| No operational access | The Administrator does not perform case, diary, financial, or reporting |
|   | actions. |


## ACCESS MODEL / CONTINUED

## Legal Users & non-login stakeholders

## 4.2 Legal User (small, trusted group)

| Capability | Detail |
| --- | --- |
| Case management | Register, search, view, and update cases. |
| Case diary | Enter hearing outcomes, attachments, and bench notes. |
| Advocate directory | Add, edit, view, and print advocate profiles. |
| Financial tracking | Add/edit financial records and monthly exposure updates. |
| Limitation tracker | View deadlines and mark them completed. |
| CSV data import | Bulk-import historical records. |
| Reports & analytics | Generate, export, and print management reports. |
| Alerts & reminders | Configure reminders; dispatch via SMTP. |
| Departmental cases | Assign cases to departments and trigger email updates. |
| Court Integration (Mock) | Preview cause lists, hearings, and documents; backend in Phase 2. |
| e-Office Integration (Mock) | Preview dispatch workflows; backend in Phase 2. |
| AI summary | Generate/regenerate an extractive case summary in Phase 1. |

## 4.3 Non-Login Stakeholders

| Stakeholder | Interaction |
| --- | --- |
| Departments (Finance, HR, etc.) | Receive case updates via SMTP email. |
| Ministry / Petroleum Division contacts | Receive notifications via SMTP email. |
| External counsel / other parties | No system access; email only. |

## Separation of responsibilities

Operational modules belong to Legal Users. Administrator audit visibility is read-only and does not confer operational permissions.


## DELIVERY BOUNDARY

## 5 | Scope

## 5.1 In Scope (MVP)

- Login with local credential authentication.

- Enhanced Dashboard: ageing buckets, financial exposure, compliance status, subject-wise litigation, upcoming hearings, and daily alert count.

- Advocate Management: directory, profile modal, and Add New Advocate.

- Case Management: search, details, 5-step registration wizard, and diary update.

- Departmental Case Assignment and email preview.

- Court Integration UI: mock data, red-flagged.

- e-Office Integration UI: mock data, red-flagged.

- Financial Tracking: records list, Add/Edit form, and monthly update.

- Limitation Tracker: deadlines and rule configuration preview.

- Alerts & Reminders: alarm dashboard and Add Reminder.

- Reports & Analytics: generator, executive summary, and printable output.

- Data Import (CSV): Legal User capability.

- AI Summary: Phase 1 extractive, summary-only, on-premise.

- Admin Side: user accounts, Add/Manage User modals, and Activity & Upload Audit.

## 5.2 Out of Scope (MVP)

- Live API integration with court websites or e-Office: Phase 2, using Company-provided data.

- SMS gateway: Phase 2.

- Confidentiality classification enforcement: Phase 2.

- AI keyword extraction, precedent matching, or risk scoring.

- Mobile native application.

- Migration from a prior LIS: no legacy system exists.

Court Integration and e-Office screens must visibly identify mock data in red.

## INTEGRATION BOUNDARY / MVP previews are not live connections.


## FUNCTIONAL SPECIFICATION / 01

## 6 | Functional Requirements by Module

## 6.1 Login

- Local credential authentication against the application database.

- No SSO, AD/LDAP, CAPTCHA, or 2FA in the isolated environment.

- Admin-issued credentials; forced password change on first login.

- Failed-login lockout; activity logged locally.

## 6.2 Dashboard

All widgets are fed from internal LIS records.

| Widget | Requirement |
| --- | --- |
| Daily Court Schedule strip | Next 6 days, with click-through. |
| Pending Diary / Daily Tasks | Pending Diary alert bar and Daily Tasks counter. |
| Ageing of Cases | 0–30 / 31–90 / 90+ days. |
| Financial Exposure | Claim, liability, recoveries; monthly update supported for |
|   | levy/tax matters. |
| Compliance Status | Compliance status visibility. |
| Subject-Wise Litigation | Petroleum Division taxonomy: 15 categories. |
| Upcoming Hearings / Alerts | Next 5 hearings and Daily Alert Count. |
| Year-Wise Case Detail | Year-wise case detail chart. |
| Court-Wise Pending Cases | Donut chart. |
| Most Important Cases | Highlighted important cases. |
| Missing Nature or Counsel | Data integrity alert. |
| Total Cases Filed by Year | Annual case filing chart. |

## 6.3 Advocate Management

- Search by region, keyword, and panel status; table with Details action per row.

- Profile modal: identity, enrollment, contact, tenure, and print.

- Add New Advocate form.

## Manual conflict verification

Conflict verification is a manual GM Legal step. There is no automatic clearance.


## FUNCTIONAL SPECIFICATION / 02

## Case lifecycle

## 6.4 Case Management

## Search filters

Against/By; Case Type; Nature (15-category Petroleum Division taxonomy); Court; District; Year From/To; Region; Advocate; Legal Stage; Court No.; Clubbing Status; Interlinked Cases; Ministry/Petroleum Division Party Status; Keywords.

## Case Details sections

Overview metadata; Clubbed & Interlinked Cases; Parties; Counsel; Electronic Case File; Case Diary; Financial Exposure Snapshot; Limitation & Compliance; AI Summary.

## 5-Step Registration Wizard

| Step | Screen | Required content |
| --- | --- | --- |
| 01 | Case Information | Ministry Party Status, Clubbing Status, Interlinked Cases, and |
|   |   | Amount Involved / Financial Exposure. |
| 02 | Counsel Information | Our versus Opposite counsel; directory selection. |
| 03 | Case Parties | Party details, with the OGDCL row highlighted. |
| 04 | Case Attachments | Category-tagged, versioned attachments. |
| 05 | Review & Submit | Confirmation, physical file details, and email preview. |

## Diary Update

Capture hearing date, legal stage, bench, proceedings, attachment, and departmental notification. Diary updates update the hearing schedule in the UI. Email is queued via SMTP (mock in the wireframe).

## Cross-module consistency

The Petroleum Division Nature taxonomy and case-linking fields carry through registration, search, and case details. Financial exposure supports the monthly-update workflow.


## FUNCTIONAL SPECIFICATION / 03

## Financials, deadlines & communication

## 6.5 Financial Tracking

- Records list with filters, subject/type, exposure, recoveries, and expenditure.

- Add/Edit form with Update Frequency: One-time / Monthly / Quarterly.

- Monthly update support for levy/tax matters; historical values preserved.

## 6.6 Limitation Tracker

- Deadline list: Reply / Appeal / Review / Compliance.

- Rule configuration preview: statutory windows per case type.

- Overdue flags, priority, and days-left countdown.

## 6.7 Alerts & Reminders

- Alarm Dashboard: due today / overdue / active.

- Filters by type, priority, due date, and search.

- Add New Reminder form.

- SMTP email; “Email queued (mock)” status.

## 6.8 Departmental Cases

- Assignment of cases to departments through a dropdown.

- Preview of email update: To, Subject, Body, and attachment.

- Notify Department via Email (Mock).

- No departmental login access.

## Email delivery boundary

SMTP email is the MVP notification channel. Preview and queued statuses in the wireframe are mock; deployed delivery uses the internal mail server.


## FUNCTIONAL SPECIFICATION / 04

## Integration previews, reports & intelligence

## 6.9 Court Integration (UI — Mock)

MOCK DATA — Pending Court API Integration

Connection and sync status card (Mock). Tabs: Cause List/Hearings and Orders & Judgments. The backend uses a Company-provided data feed in Phase 2.

## 6.10 e-Office Integration (UI — Mock)

MOCK UI — e-Office backend pending Phase 2 integration

Sync status card; Work Queues for Inbound, Outbound, and Dispatch History; Correspondence Draft Builder (Mock). Backend: Company-provided API in Phase 2.

## 6.11 Reports & Analytics

- Report Library: Hearing, Multiple Status, Missing Data, Status, Dormant, PAC.

- Multi-parametric filter panel and results table with Actions.

- Export to MS Word / PDF / Excel, plus Print.

- Executive Summary view for Minister / Secretary.

- Generated Report Output: print-friendly.

## 6.12 Data Import (CSV) — Legal User

- Data Type selector: Cases / Advocates / Parties / Financial / Diary.

- CSV template download.

- Upload, column mapping, and validation preview.

- Import valid records; download error report; retain import activity log.

## 6.13 AI Summary (Phase 1)

Extractive, on-premise, CPU-friendly. Summary only: no keywords, no citations, and no risk scoring.

Displayed as an “AI Case Summary” card in Case Details.

Actions Regenerate / View Source Documents / Mark as Reviewed


## FUNCTIONAL SPECIFICATION / 05

## Administration & data foundation

## 6.14 Admin Side

## User Accounts

- KPI cards: Total / Active / Suspended / Administrators.

- Filters and user table with Actions: Edit, Reset Password, Enable/Disable.

- Add New User modal: initial password and forced change option.

- Manage User modal: edit role, status, password, and change log.

## Activity & Upload Audit (view-only)

- KPI cards: Uploads This Month, Active Uploaders, CSV Imports, Rejected.

- Filters: user, module, date range, and search.

- Table: Timestamp, User, Role, Module, Action, Reference, Count, Outcome, Details.

- Row action: “View Details”; no edits.

## 7 | Data Entities (Minimum Set)

| Group | Entities / required attributes |
| --- | --- |
| Case & representation | Case; Party; Counsel Assignment; Advocate. |
| Documents & diary | Document (+Category +Version +Keywords +Handling Label); Case Diary |
|   | Entry. |
| Deadlines & financials | Limitation Rule + Calculated Deadline; Financial Record; Reminder/Alert. |
| Access & traceability | User; Audit Log Entry; Data Import Batch. |
| Case relationships | Clubbing Link; Interlink Record. |
| Phase 2 governance | Confidentiality Classification. |

## Audit is visibility, not operational access

The Administrator can inspect activity and upload details but cannot edit audit records or perform legal operations.


## TECHNICAL BOUNDARIES & SERVICE QUALITY

## 8 | Integrations & Dependencies

| External system | Status | Dependency |
| --- | --- | --- |
| Supreme Court of Pakistan | Mock UI in MVP | Company provides data/API feed (Phase 2). |
| Federal Constitutional Court Mock UI in MVP Company provides data/API feed (Phase 2). |   |   |
| All High Courts | Mock UI in MVP | Company provides data/API feed (Phase 2). |
| e-Office | Mock UI in MVP Company provides API/data (Phase 2). |   |
| SMTP Mail | Available in MVP | Internal mail server only; isolated environment. |
| AI Model | MVP | Extractive/local; no external API. |

## Offline deployment notes

- No CDN dependencies; fonts and icons must be self-hosted.

- No telemetry or auto-update endpoints.

- Court-data arrival mechanism for the isolated server is to be defined by OGDCL IT: scheduled import or data exchange.

## 9 | Notifications

SMTP email only for MVP. Trigger events: New case registration, Diary entry, Reminder due, Limitation

deadline, Compliance pending, and Departmental update.

SMS gateway is deferred to Phase 2; vendor to be engaged after the email proof-of-concept.

## 10 | Non-Functional Requirements

| Quality | Requirement |
| --- | --- |
| Security | Local authentication; view-only admin audit; role-restricted operations. |
| Auditability | All data entries and uploads logged with user, timestamp, action, and outcome. |
| Performance | Dashboard renders in less than 3 seconds on internal LAN; tables paginated. |
| Usability | Consistent OGDCL branding; responsive layout; keyboard-navigable. |
| Reliability | Daily automatic database backup, to be configured by IT. |
| Isolation | No external network calls from application runtime. |


## RELEASE PLAN & VERIFICATION

## 11 | Phasing Roadmap

| Phase 1 — MVP | Phase 2 — Integration & Governance |
| --- | --- |
| All modules listed in scope, with Court Integration and e-Office as Mock/UI-only. | Court Integration backend (SC, FCC, HCs); e-Office backend; Confidentiality Classification enforcement; SMS gateway; optional AI upgrade if infrastructure permits. |

## 12 | Acceptance Criteria (For Sign-Off)

- 1. All 27 screens delivered with OGDCL branding and end-to-end clickable flow.

- 2. Case Registration 5-step wizard functional with validation.

- 3. Dashboard widgets display correct internal LIS-derived values.

- 4. Petroleum Division 15-category taxonomy applied across Case Registration, Search, Details, Reports, Dashboard, and Admin Config.

- 5. Clubbing and Interlinking fields present in Case Registration, Search, and Details.

- 6. Ministry/Petroleum Division Direct Party field present in Case Registration and Search.

- 7. Amount Involved / Financial Exposure supports monthly update.

- 8. Admin can create accounts; only those accounts can log in.

- 9. Admin can view, read-only, all data entries and uploads.

- 10. No screen implies live external integration unless mock-flagged in red.

- 11. AI Summary is extractive and summary-only.

- 12. CSV import works fully offline and logs its activity.

- 13. All exports (Word/PDF/Excel) and Print functions present.

- 14. Full offline operation on the isolated intranet.


## DELIVERY READINESS

## 13 | Assumptions & Risks

## Assumptions

| Assumption | Impact if invalid |
| --- | --- |
| Company provides court/e-Office data feeds in Phase 2. Mock UI remains; no live benefit. |   |
| Server specification sufficient (i7 / 32 GB / 1 TB). | Extractive AI and dashboard fine; larger LLM not |
|   | viable. |
| Internal SMTP server available. | Alerts fall back to system-only notifications. |
| No legacy migration required; historical records only via | Import framework is ready; not a blocker. |
| CSV. |   |
| Petroleum Division taxonomy is authoritative. | Requires re-mapping if the letter is superseded. |

## Risks

| Risk | Mitigation |
| --- | --- |
| Scope creep from stakeholder requests. | Phase gating: Phase 1 versus Phase 2. |
| Stitch-generated UI needs clean-up in Figma. | Consolidated punch list applied after export. |
| Data quality in CSV imports. | Validation preview with error report before commit. |
| AI expectations beyond extractive. | Explicitly documented: Phase 1 is summary only. |

## 14 | Deliverables

- 1. Wireframe Prototype — 27 screens, OGDCL branded, with mock data.

- 2. This PRD — v1.0 for approval.

- 3. Figma Punch List — cosmetic/template refinements to apply after export.

- 4. Screen Inventory — mapping to modules with Enhancement / New / Mock / Phase 2 tags.

- 5. Development Handover — Stitch exports, Figma flows, and this PRD.


## DELIVERY REFERENCE / SCREEN-TO-MODULE MAPPING

## 14.1 Screen Inventory

Screen names and module assignments follow the supplied screen inventory.

| # | Screen | Module |
| --- | --- | --- |
| 1 | Login | Auth |
| 2 | Dashboard | Dashboard |
| 3 | Advocate Directory | Advocates |
| 4 | Advocate Profile Modal | Advocates |
| 5 | Register New Advocate | Advocates |
| 6 | Case Search | Case Mgmt |
| 7 | Case Details | Case Mgmt |
| 8 | Add New Case — Step 1 | Case Mgmt |
| 9 | Add New Case — Step 2 | Case Mgmt |
| 10 Add New Case — Step 3 |   | Case Mgmt |
| 11 | Add New Case — Step 4 | Case Mgmt |
| 12 Add New Case — Step 5 |   | Case Mgmt |
| 13 | Update Case Diary | Case Mgmt |
| 14 | Departmental Cases | Dept |
| 15 | Court Integration | Court |
| 16 | e-Office Integration | e-Office |
| 17 | Financial Tracking | Financial |
| 18 | Limitation Tracker | Limitation |
| 19 | Alerts & Reminders | Alerts |
| 20 | Reports & Data Export | Reports |
| 21 | Executive Summary | Reports |
| 22 | Generated Report Output | Reports |
| 23 | Data Import (CSV) | Data |
| 24 | User Accounts | Admin |
| 25 | Add New User Modal | Admin |
| 26 | Manage User Modal | Admin |
| 27 | Activity & Upload Audit | Admin |
| 28 | System Config | Admin |

*Mock UI in MVP: screens 15–16; live backends are Phase 2.*

Admin: screens 24–28 are marked administrator-only in the supplied inventory.

## Screen-count reconciliation — for confirmation

The supplied inventory lists 28 screens, including System Config (28), while the PRD baseline specifies 27.

Confirm inclusion of System Config and its permitted administrative functions before updating the MVP count and sign-off criteria.


## DECISION RECORD

## 15 | Approval

Document: OGDCL Legal Information System (LIS)

Status: For Review & Approval

Version: v1.0

MVP target: 16 September 2026

| Role | Name | Signature | Date |
| --- | --- | --- | --- |

Product Owner (OGDCL Legal)

Legal Directorate Approver

IT / Server Owner

Development Lead

## Summary of Locked Decisions

- Two roles only: Admin for user management and audit view; Legal User for all operational work.

- No departmental login: email notifications only.

- Fully isolated environment: no CDN, no external calls, self-hosted fonts and icons.

- AI: extractive, summary-only, CPU-only.

- Phase 2 clearly marked: Court Integration backend, e-Office backend, confidentiality enforcement, and SMS.

- Regulatory compliance: Petroleum Division taxonomy (4 September 2026) and Clubbing/Linking directives (31 August 2026) referenced.

- Screen scope: approximately 27 screens; acceptance target is all 27 screens delivered.
