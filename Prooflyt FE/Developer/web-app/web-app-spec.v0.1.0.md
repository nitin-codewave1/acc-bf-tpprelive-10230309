---
id: agent-developer/prooflyt_fe/web-app/WEB-APP-SPEC.md
type: spec
project: 2355a1a6-0cde-4feb-8bd0-f037f7c23507
version: 0.1.0
author: acd154e9-7d7c-493d-b538-c1e75f4fcbbe
produces: agent-developer/prooflyt_fe/web-app/WEB-APP-SPEC.md
depends_on: [US-006-03, US-006-01, US-006-02, US-008-04, US-011-01, US-011-03, US-011-04, US-002-01, US-002-05, US-011-02, US-001-01, US-001-02, US-001-03, US-002-02, US-002-03, US-002-04, US-003-01, US-003-02, US-003-03, US-004-01, US-004-02, US-004-03, US-005-01, US-005-02, US-005-03, US-007-01, US-007-02, US-008-01, US-008-02, US-008-03, US-009-01, US-009-02, US-009-03, US-010-01, US-010-02, US-011-05, US-016-02]
commit_kind: append
confidence: agent
run_id: 9547af9a-51c6-515a-8ce9-048bf28b523c
okf_id: web-app/WEB-APP-SPEC.md
---

<!-- SECTION: web-app.overview | status: DRAFT-UNVERIFIED -->
## Overview

**Purpose.** This document specifies the Prooflyt web application as far as the supplied inputs allow. This run is incremental and carries change request **CR-109** (`feedback.md`). CR-109 adds an empty state to the proofs list in the web frontend. Its only acceptance criteria are US-006-03 in `stories.md`, which this run traces to.

**Run status: HALTED (HALT-CRITICAL-CONTRADICTION).** Three Critical contradictions were found at intake (CON-WEB-001 to CON-WEB-003). The sections that depend on them are marked `BLOCKED`. The remaining sections are written as far as the inputs allow. The run stops here until those contradictions are resolved by the human.

**Baseline.** The run is incremental, but no approved `WEB-APP-SPEC` was supplied. `RUN-CONTEXT.existing` lists only `GAPS.md`, `INTAKE.md`, `READINESS.md` and `SELF-CHECK.md`. There is therefore no approved content to preserve for sections CR-109 does not touch. Every section below is written from the supplied inputs.

**Constraints from CR-109.**
- Frontend only. The empty state is built from existing proofs data with no backend change (US-006-03, AC1).
- The upload action opens the existing upload dialog (US-006-03, AC2). This run does not redesign that dialog.

**Terminology (ASM-WEB-001).** CR-109 and US-006-03 say "proofs". EP-006 says "evidence", and US-006-01 and US-006-02 use "evidence records" and "evidence files". This run treats the two terms as the same entity. Confirming artefact: product owner confirmation.

**Primary actors.** The actors named in `stories.md` are listed below. The inputs do not say which of them use the web application and which use the admin surface (Q-WEB-001).
- Compliance manager, compliance officer, compliance administrator, legal administrator (EP-001, EP-006, EP-010)
- User (EP-002, EP-011)
- Incident responder, DPO (EP-003)
- Reviewer, data steward (EP-004, EP-008)
- Case handler, rights handler, handler (EP-005, EP-013 in the backend reference only)
- Data owner (US-006-02)
- Content owner, content author, approver (EP-007)
- Data protection officer (US-008-04)
- Administrator (US-011-01, US-011-03)
- Staff (US-011-04 names "logged-in user"; no separate "staff" story is in `stories.md`)

**Explicitly out of scope for this document.**
- Any backend change. CR-109 forbids it, and no backend operation is specified here.
- The admin surface. Its requirements are not in this run's surface (I-1).
- The internal behaviour of the existing evidence upload dialog, including its fields, validation and submission (GAP-WEB-004).
- Upload, update, replace and delete of evidence files (US-006-02). CR-109 only opens the existing dialog.
- Stories with no acceptance criteria (35 of 36). They are listed in `web-app.coverage` and not specified.
- Production of the illustration asset.
- Notifications, real-time push design, and any NFR target.

**Contract status.** `contract_source` is `in-run-backend`, and `contract_path` is readable. The supplied content is a backend coverage document, not an API contract. It contains no verified method, path, request shape or response shape. Its own API index states: "No `api_docs` input was supplied, so no method, path or status code below is verified." The contract indexes no operation that returns evidence or proofs. Every API dependency in this document is therefore `none pinned` (GAP-WEB-005). The supplied `contract_pin` (`sha256:f2da645491f3`) cannot be checked against the content.

<!-- /SECTION: web-app.overview -->
<!-- SECTION: web-app.routing | status: BLOCKED -->
## Routing

**Blocked.** No route path, route table, layout hierarchy or redirect target is supplied in any input. The design brief names screens (for example `LoginPage`, `EvidenceListScreen`, `RootPage`) but gives no paths. Screen titles are not routes.

**Known, cited facts only.**
- `RootPage` (M11) exists as a screen in the design brief. Its routing role is not stated.
- `LoginPage` (M2) and `SetPasswordPage` (M2) exist as screens (`design-brief.md`, screens inventory).
- The proofs list route is unknown. The closest candidate screen is `EvidenceListScreen` (M6), which is unconfirmed (ASM-WEB-002).

**Unblocks with:**
- **GAP-WEB-010.** Route table with paths, layout nesting, protected-route list, and the proofs list path. Closing artefact: route table from the product owner or the design project.
- The unauthenticated redirect target is also part of GAP-WEB-010. No input states it, so no redirect is assumed.

<!-- /SECTION: web-app.routing -->
<!-- SECTION: web-app.module-map | status: DRAFT-UNVERIFIED -->
## Module map

The design brief groups screens into modules M1 to M11 (`design-brief.md`, screens inventory). The brief does not map these modules to epics. The epic column below is a candidate mapping from story titles (ASM-WEB-005).

| Module | Screens (design brief) | Candidate epic (ASM-WEB-005) | Route ownership |
|---|---|---|---|
| M1 | AuditIntegrityScreen, AuditLogListScreen, AuditTargetEntriesScreen, ReportDetailPage, ReportsListingPage | EP-001 | BLOCKED (GAP-WEB-010) |
| M2 | LoginPage, SetPasswordPage | EP-002 | BLOCKED (GAP-WEB-010) |
| M3 | BreachDetailScreen, BreachListScreen, BreachReportScreen | EP-003 | BLOCKED (GAP-WEB-010) |
| M4 | DataSourceColumnReviewScreen, DataSourceDetailScreen, DataSourceUploadScreen | EP-004 | BLOCKED (GAP-WEB-010) |
| M5 | CaseEvidenceScreen, RightsCaseCreateScreen, RightsCaseDetailScreen, RightsCaseListScreen, TaskCreateScreen, TaskListScreen | EP-005 | BLOCKED (GAP-WEB-010) |
| M6 | EvidenceListScreen (Default, Error), EvidenceDetailScreen (Default, Error) | EP-006 (the proofs area for CR-109) | BLOCKED (GAP-WEB-010) |
| M7 | NoticeApprovalScreen, NoticeEditorScreen | EP-007 | BLOCKED (GAP-WEB-010) |
| M8 | ProcessorsListScreen, RegisterEntryScreen | EP-008 and EP-009 | BLOCKED (GAP-WEB-010) |
| M9 | ProcessorDetailScreen, ProcessorComplianceScreen | EP-009 (and EP-008 for ProcessorDetailScreen, per stories-map) | BLOCKED (GAP-WEB-010) |
| M10 | RetentionRulesScreen, LegalHoldsScreen, PurgeTasksScreen | EP-010 | BLOCKED (GAP-WEB-010) |
| M11 | RoleAwareDashboardScreen, RolesScreen, RootPage, PermissionMatrixScreen, MyPermissionsScreen, MyActivityScreen | EP-011 | BLOCKED (GAP-WEB-010) |

**Proofs area for CR-109.** The empty state belongs to the proofs list. No screen named "proofs" exists in the design brief. The candidate screen is `EvidenceListScreen` (M6). Its variants are Default and Error. It has no Empty variant. The empty state is therefore not yet designed (GAP-WEB-003).

**Surface ownership.** M11 contains role-management screens (`RolesScreen`, `PermissionMatrixScreen`) that stories assign to administrators (US-011-01, US-011-03). These may belong to the admin surface and not this one. The two end-user screens in M11 (`MyPermissionsScreen` for US-011-03's "see my own effective permissions", and `RoleAwareDashboardScreen`, `MyActivityScreen`) are in the web app's likely scope. Ownership is unresolved (Q-WEB-001).

<!-- /SECTION: web-app.module-map -->
<!-- SECTION: web-app.state-management | status: DRAFT-UNVERIFIED -->
## State management

**Server state.** The proofs list is server state. Its data comes from existing proofs data (US-006-03, AC1). The operation that returns it is not in the contract (GAP-WEB-005), so its cache key, parameters and pagination are unknown.

**Client state.** The upload dialog's open or closed state is client state. Nothing else in the empty-state behaviour requires client state beyond this.

**Empty-state trigger.** The empty state is shown only when the proofs query has completed successfully and returned zero proofs (`WEB-PROOFS-FR-001`). It is not shown while the query is loading, and it is not shown when the query fails. Those are separate states (`WEB-PROOFS-FR-004`). This follows the state rule in the web role: loading, empty, populated and error must be distinct.

**Cache invalidation (DERIVED).** After an upload completes, the proofs list must reflect the new proof. Otherwise the empty state would remain visible after a proof exists, which contradicts US-006-03, AC3. The invalidation trigger and the mechanism are not specified. The upload dialog's completion behaviour is unknown (GAP-WEB-004), so the invalidation policy is `DRAFT-UNVERIFIED` (`WEB-PROOFS-FR-005`).

**Real-time updates: BLOCKED.** NFR-002, NFR-003 and NFR-004 in `requirements.md` call for real-time event and notification streaming. Their targets are blank (`requirements.md`). None says whether the proofs list must update live when another user adds a proof. The tenant scoping of the real-time channel is also contradicted (CON-WEB-003). This part of the section is blocked. Closing artefact: GAP-WEB-016.

<!-- /SECTION: web-app.state-management -->
<!-- SECTION: web-app.auth-flows | status: BLOCKED -->
## Auth flows

**Blocked.** Login, refresh, session expiry, logout and mid-flow expiry behaviour cannot be specified from the supplied inputs.

**Cited facts.**
- `LoginPage` and `SetPasswordPage` exist as screens. `SetPasswordPage` has Default and Error variants (`design-brief.md`).
- US-002-01 says the session is "restored" and that the profile is managed "via an auth context". US-002-05 says the session "is restored on reload". No acceptance criteria are given for either.
- A logout operation is named in the backend coverage document as `API-AUTH-002@1`. It has no method, no path and no response shape (`backend-api.md`, ASM-BE-012). The same document describes the logout audit behaviour through a feedback reference that does not appear in the supplied `feedback.md` (CON-WEB-002).

**Why this is blocked.** The session end state, the expiry signal and the logout behaviour depend on the contradicted backend reference. CON-WEB-001 and CON-WEB-002 are both Critical, because they concern the session state machine and the audit trail. Writing auth behaviour now would mean choosing one reading of the contradiction.

**Unblocks with:**
- Resolution of CON-WEB-001 and CON-WEB-002.
- **GAP-WEB-011.** Session lifecycle specification: refresh, expiry, logout, and the web-app response to each. Closing artefact: session specification plus a pinned logout operation.

<!-- /SECTION: web-app.auth-flows -->
<!-- SECTION: web-app.authorization-ui | status: BLOCKED -->
## Authorization UI

**Blocked.** The role catalogue is not supplied. No input lists the roles that can sign in to the web application. No permission matrix is supplied for any role and any screen. The mapping from role to navigation to action cannot be written.

**Cited facts.**
- Actor nouns in `stories.md` are listed in `web-app.overview`. They are names taken from the story text, with no permissions attached.
- US-011-02 and US-011-04 require that navigation reflect the user's permissions. US-011-01 and US-011-03 require administrators to manage those permissions. The inputs do not say which of these are web-app concerns (Q-WEB-001).
- The upload button in the empty state (US-006-03, AC2) has no stated permission. Its visibility by role is unknown (GAP-WEB-008, Q-WEB-002).

**Roles excluded from this spec.** None can be excluded yet, because no role list exists. Once a list is supplied, each role will be checked against whether it has a web-app route. Roles with no web-app route will be excluded and named here, with the reason (I-1).

**Unblocks with:** **GAP-WEB-009.** Role catalogue, default permission matrix, and the surface assignment of each role. Closing artefact: role list from the product owner, marked by surface.

<!-- /SECTION: web-app.authorization-ui -->
<!-- SECTION: web-app.design-system | status: DRAFT-UNVERIFIED -->
## Design system

**Figma status.** Figma MCP is not connected (`RUN-CONTEXT.inputs.figma_mcp`). The design brief is present. The spec mode is therefore `FULL-FROM-BRIEF`. Every frame ID and token name below is an unverified claim taken from the brief.

**Tokens (IDs only).** The design brief lists 71 token IDs (`design-brief.md`, Counts; `tokens-index.md`). Their values are not inlined in any input. The families are:
- `UI/border/*`
- `UI/color/*`
- `UI/icon/*`
- `UI/surface/*`, including `UI/surface/button/*` and `UI/surface/card`
- `UI/text/*`, including `UI/text/primary`, `UI/text/secondary` and `UI/text/placeholder`

No token is mapped to an empty-state element. The brief gives no mapping, so none is assumed. No token value is written in this document.

**Components.** The components inventory lists three components (`components-inventory.md`):
- `Card/Item` (container, 1 variant)
- `Input/Password` (entry, 5 variants)
- `Input/Segmented` (entry, 5 variants)

The inventory contains **no button component, no heading component, no empty-state component and no illustration component.** CR-109 requires an upload button, a heading and an illustration slot. The existing button component that the upload button would reuse is not identified (GAP-WEB-018).

**Type scale, spacing and breakpoints: BLOCKED.** No type scale, spacing scale or breakpoint is supplied. The token index lists IDs and path references only. The values are not in the inputs (GAP-WEB-013).

**Unblocks with:** GAP-WEB-013 (token values), GAP-WEB-018 (button and empty-state components), GAP-WEB-007 (illustration asset and token).

<!-- /SECTION: web-app.design-system -->
<!-- SECTION: web-app.responsive | status: BLOCKED -->
## Responsive

**Blocked.** No breakpoint, layout change or responsive rule is supplied. The design brief contains no breakpoint token and no per-breakpoint frame. The empty-state layout at any width is unknown.

**Unblocks with:** **GAP-WEB-013.** Breakpoints and the layout change at each, from the design project.

<!-- /SECTION: web-app.responsive -->
<!-- SECTION: web-app.browser-support | status: BLOCKED -->
## Browser support

**Blocked.** No input names a supported browser or version. Nothing is assumed.

**Unblocks with:** **GAP-WEB-012.** Supported browser matrix from the product owner.

<!-- /SECTION: web-app.browser-support -->
<!-- SECTION: web-app.accessibility | status: BLOCKED -->
## Accessibility

**Blocked.** No accessibility standard, conformance level or verification method is supplied in any input. No standard is cited here, and none is assumed.

**Cited facts.** The components inventory records Focused and Error states for `Input/Password` and `Input/Segmented` (`components-inventory.md`). The design brief contains no accessibility annotation.

**Unblocks with:** **GAP-WEB-014.** Target standard, conformance level, and how it is verified.

<!-- /SECTION: web-app.accessibility -->
<!-- SECTION: web-app.performance | status: BLOCKED -->
## Performance

**Blocked.** Three items cannot be written.

- **Bundle budget.** No budget is supplied. NFR targets are blank in `requirements.md` (NFR-001 to NFR-004).
- **Route-level code splitting.** Route paths are unknown (GAP-WEB-010), so splitting cannot be assigned to routes.
- **Largest-payload route.** Unknown. The proofs list's payload size is unknown because the list operation is not in the contract (GAP-WEB-005).

**Unblocks with:** **GAP-WEB-015.** NFR targets with sources, a bundle budget, and the route inventory needed to identify the largest payload.

<!-- /SECTION: web-app.performance -->
<!-- SECTION: web-app.coverage | status: DRAFT-UNVERIFIED -->
## Coverage

### Requirements written in this run

Each requirement carries its traces, its verification and the API it depends on. The API is `none pinned` wherever the contract has no operation (GAP-WEB-005).

**WEB-PROOFS-FR-001.** Given the proofs list has no proofs, when the proofs page loads, then an empty state is shown with an illustration slot, a heading, help text and an upload button.
- Traces to: US-006-03, AC1 (`stories.md`); CR-109 (`feedback.md`)
- Verification: (planned) `proofs_empty_state_shown_when_list_empty`
- API: none pinned (GAP-WEB-005)
- Note: the design for the empty state is absent (GAP-WEB-003). The element content and layout are not specified here. The element types are given only as the story names them.

**WEB-PROOFS-FR-002.** Given the empty state is shown, when the user clicks the upload button, then the existing upload dialog opens.
- Traces to: US-006-03, AC2
- Verification: (planned) `empty_state_upload_button_opens_existing_dialog`
- API: none (frontend-only behaviour)
- Note: the dialog is not specified (GAP-WEB-004). Its visibility by role is not specified (GAP-WEB-008). Under ASM-WEB-003 the button is shown whenever the empty state is shown.

**WEB-PROOFS-FR-003.** Given the proofs list contains at least one proof, when the page loads, then the empty state is not shown and the list is displayed.
- Traces to: US-006-03, AC3
- Verification: (planned) `empty_state_hidden_when_list_has_proof`
- API: none pinned (GAP-WEB-005)

**WEB-PROOFS-FR-004.** The empty state is not shown while the proofs query is loading or when it has failed.
- Traces to: DERIVED from US-006-03, AC1 ("has no proofs" requires a successful, complete response), and from the state rule in the web role (loading, empty, populated and error are distinct)
- Verification: (planned) `empty_state_not_shown_while_loading_or_on_error`
- API: none pinned (GAP-WEB-005)
- Status: DERIVED. The error presentation is not specified (EvidenceListScreen has an Error variant; its content is not supplied).

**WEB-PROOFS-FR-005.** After a proof is added through the upload dialog, the proofs list reflects it, so the empty state is no longer shown.
- Traces to: DERIVED from US-006-03, AC3; the upload dialog's completion behaviour is GAP-WEB-004
- Verification: (planned) `proofs_list_refreshes_after_upload_hides_empty_state`
- API: none pinned. The upload operation (US-006-02) is not in the contract.
- Status: DRAFT-UNVERIFIED until GAP-WEB-004 closes.

### Invariants

- **INV-WEB-001.** The empty state and the populated list are mutually exclusive for a given query result. Derived from US-006-03, AC1 and AC3.
- **INV-WEB-002.** The empty state's upload button opens the existing upload dialog and creates no separate upload path. Derived from US-006-03, AC2.

### Story coverage

All 36 stories in `stories.md` are listed. Column "Screen (design map)" comes from `stories-map.md`. Only US-006-03 has acceptance criteria.

| Story | Epic | Screen (design map) | Covered by | Status |
|---|---|---|---|---|
| US-001-01 | EP-001 | ReportDetailPage | None | Not covered: no AC (GAP-WEB-017) |
| US-001-02 | EP-001 | AuditTargetEntriesScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-001-03 | EP-001 | AuditLogListScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-002-01 | EP-002 | LoginPage | None | Not covered: no AC; auth BLOCKED (GAP-WEB-011) |
| US-002-02 | EP-002 | LoginPage (listed twice in map) | None | Not covered: no AC; duplicate row (CON-WEB-004) |
| US-002-03 | EP-002 | SetPasswordPage | None | Not covered: no AC (GAP-WEB-017) |
| US-002-04 | EP-002 | SetPasswordPage | None | Not covered: no AC (GAP-WEB-017) |
| US-002-05 | EP-002 | Not mapped in design brief | None | Not covered: no AC; not in design map (CON-WEB-004) |
| US-003-01 | EP-003 | TaskListScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-003-02 | EP-003 | BreachDetailScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-003-03 | EP-003 | BreachDetailScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-004-01 | EP-004 | DataSourceColumnReviewScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-004-02 | EP-004 | DataSourceDetailScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-004-03 | EP-004 | DataSourceUploadScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-005-01 | EP-005 | TaskListScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-005-02 | EP-005 | CaseEvidenceScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-005-03 | EP-005 | RightsCaseCreateScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-006-01 | EP-006 | EvidenceDetailScreen | None | Not covered: no AC; outside CR-109 (GAP-WEB-017) |
| US-006-02 | EP-006 | EvidenceDetailScreen | None | Not covered: no AC; upload dialog unspecified (GAP-WEB-004, GAP-WEB-017) |
| US-006-03 | EP-006 | None (stories-map has "-") | WEB-PROOFS-FR-001, 002, 003, 004, 005 | Covered by this run (no design frame: GAP-WEB-003) |
| US-007-01 | EP-007 | NoticeApprovalScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-007-02 | EP-007 | NoticeApprovalScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-008-01 | EP-008 | RegisterEntryScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-008-02 | EP-008 | DataSourceDetailScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-008-03 | EP-008 | ProcessorDetailScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-008-04 | EP-008 | RegisterEntryScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-009-01 | EP-009 | ProcessorDetailScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-009-02 | EP-009 | ProcessorComplianceScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-009-03 | EP-009 | ProcessorDetailScreen | None | Not covered: no AC; identifier collision (CON-WEB-001) |
| US-010-01 | EP-010 | PurgeTasksScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-010-02 | EP-010 | LegalHoldsScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-011-01 | EP-011 | PermissionMatrixScreen | None | Not covered: no AC; surface ownership (Q-WEB-001) |
| US-011-02 | EP-011 | RoleAwareDashboardScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-011-03 | EP-011 | MyPermissionsScreen | None | Not covered: no AC; surface ownership (Q-WEB-001) |
| US-011-04 | EP-011 | RoleAwareDashboardScreen | None | Not covered: no AC (GAP-WEB-017) |
| US-011-05 | EP-011 | MyActivityScreen | None | Not covered: no AC (GAP-WEB-017) |

**Count.** 36 stories supplied. 1 covered (US-006-03). 35 not covered. Of the 35, 34 lack acceptance criteria and are not covered in this run. US-002-05 is absent from the design map.

**Requirements not traced to a story.** BR-001 to BR-003 and NFR-001 to NFR-004 in `requirements.md` have blank rationale, enforcement and targets. They are not traced here. Their gaps are GAP-WEB-015 and GAP-WEB-017.

### Contradictions

| ID | Rank | Claim A | Claim B | Consequence of each reading | Affected sections |
|---|---|---|---|---|---|
| CON-WEB-001 | Critical | `backend-api.md` uses EP-009 to EP-016 and US-009-01 to US-016-02, where US-009-03 is the logout audit criteria AC-009-03-01 to 03. | `stories.md` uses the same identifiers for different stories. US-009-03 there is "see all evidence and breach records linked to a given processor". | Reading the backend reference gives a session-end and audit model this spec has no authority to adopt. Reading `stories.md` leaves session behaviour unspecified. Both readings are unverified. | `auth-flows`, `authorization-ui` |
| CON-WEB-002 | Critical | `backend-api.md` attributes CR-101 and its preflight answer to `feedback.md`. | The supplied `feedback.md` contains only CR-109. CR-101 does not appear in it. | If the reference is accepted, session-end audit behaviour is inherited without a source. If rejected, the logout operation has no behaviour. | `auth-flows` |
| CON-WEB-003 | Critical | `backend-api.md` cites `requirements.md` NFR-004 as "tenant-scoped" WebSocket streaming. | `requirements.md` NFR-004 reads "Real-time notification and event delivery" and mentions no tenant scope. | If tenant scoping applies, the real-time channel needs tenant isolation. If it does not, that is an authorization gap. Either way the channel's tenancy is unstated. | `state-management`, `authorization-ui` |
| CON-WEB-004 | Non-critical | `stories.md` contains US-002-02 and US-002-05 with the same text. | `stories-map.md` lists US-002-02 twice and does not list US-002-05. | Reading US-002-05 as a duplicate leaves it unmapped. Reading it as distinct leaves a story with no design. The reading chosen here is the more cited one: both are listed, and US-002-05 is unmapped. | `coverage`, `auth-flows` (section status DRAFT-UNVERIFIED) |

**Halt.** CON-WEB-001, CON-WEB-002 and CON-WEB-003 are Critical. The run halts at the end of intake (`HALT-CRITICAL-CONTRADICTION`). Sections that depend on them are `BLOCKED`.

### Gaps and assumptions raised in this document

| ID | Subject | Closing artefact |
|---|---|---|
| GAP-WEB-003 | No design frame for the proofs empty state. `stories-map.md` maps US-006-03 to no screen, and `EvidenceListScreen` has no Empty variant. | Design frame for the empty state |
| GAP-WEB-004 | The "existing upload dialog" is not in the design brief. `DataSourceUploadScreen` is for data sources (US-004-03), not evidence, and is not treated as the same dialog. | Dialog specification and design frame |
| GAP-WEB-005 | The contract has no operation that returns proofs or evidence, and no evidence upload operation. Every API dependency is `none pinned`. | Contract entries for the evidence list and upload operations, from the backend |
| GAP-WEB-006 | Copy for the heading, help text and button label is not supplied. | Copy deck with i18n keys |
| GAP-WEB-007 | No illustration asset and no illustration token is supplied. | Illustration asset and token |
| GAP-WEB-008 | No permission is stated for the empty-state upload button. | Permission matrix covering evidence upload |
| GAP-WEB-009 | No role catalogue, and no statement of which roles sign in to the web application. | Role list marked by surface |
| GAP-WEB-010 | No route table, no protected-route list, no proofs path, no unauthenticated redirect target. | Route table |
| GAP-WEB-011 | No session lifecycle: refresh, expiry, logout and the web response to each. The logout operation has no path or method. | Session specification and pinned logout operation |
| GAP-WEB-012 | No supported browser list. | Browser matrix |
| GAP-WEB-013 | No breakpoints, type scale or spacing values. Token values are not supplied. | Design token values and breakpoints |
| GAP-WEB-014 | No accessibility standard or verification method. | Accessibility requirement |
| GAP-WEB-015 | No NFR targets, no bundle budget, and no route inventory for payload analysis. | NFR targets with sources; route inventory |
| GAP-WEB-016 | No statement on whether the proofs list updates live, or how the real-time channel behaves. | Real-time behaviour requirement |
| GAP-WEB-017 | 35 of 36 stories have no acceptance criteria. | Acceptance criteria for each story |
| GAP-WEB-018 | The components inventory has no button, heading or empty-state component. The existing button the upload button would reuse is not identified. | Components inventory including button and empty-state components |
| ASM-WEB-001 | "Proofs" means evidence records (EP-006). | Product owner confirmation |
| ASM-WEB-002 | `EvidenceListScreen` (M6) is the proofs list screen. | Design frame for the proofs list |
| ASM-WEB-003 | The empty-state upload button is shown whenever the empty state is shown, as US-006-03, AC2 states without condition. | Resolution of GAP-WEB-008 |
| ASM-WEB-004 | Module labels M1 to M11 correspond to the candidate epics in `web-app.module-map`. | Design-to-epic mapping from the design project |
| ASM-WEB-005 | The candidate epic column in `web-app.module-map` is correct. | Design-to-epic mapping from the design project |

**Questions.**
- **Q-WEB-001 (blocking).** Which surface owns the role-management screens (`RolesScreen`, `PermissionMatrixScreen`) and the stories that assign them to administrators (US-011-01, US-011-03)? The answer changes the actors and the authorization model, so it is blocking. Owner: product owner.
- **Q-WEB-002 (degradable).** When a user has no upload permission, should the empty-state upload button be hidden? Default if unanswered: the button is shown, as US-006-03, AC2 states without condition, and this is marked `DRAFT-UNVERIFIED` (ASM-WEB-003). Owner: product owner.

<!-- /SECTION: web-app.coverage -->
