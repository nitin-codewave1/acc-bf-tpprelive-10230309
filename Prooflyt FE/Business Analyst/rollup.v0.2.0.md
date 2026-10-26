---
id: agent-ba/prooflyt_fe/rollup.md
type: spec
project: 2355a1a6-0cde-4feb-8bd0-f037f7c23507
version: 0.2.0
author: acd154e9-7d7c-493d-b538-c1e75f4fcbbe
produces: agent-ba/prooflyt_fe/rollup.md
depends_on: []
commit_kind: fork
confidence: agent
run_id: 7bc040f8-ceb4-5e7d-b2ce-fa11f722edc7
---

# Business Analysis — D-COPSCAR

## Discovery

**Brief Quality:** ? (Problem: ?, Outcomes: ?, Stakeholders: ?)

**Declaration:** N/A

## Business Objectives

### OBJ-001: Enable Data Protection Compliance Management
- **Leading KPI:** 
- **Lagging KPI:** N/A
- **Target:** N/A
- **Impact:** N/A

### OBJ-002: Secure Access and Identity Management
- **Leading KPI:** 
- **Lagging KPI:** N/A
- **Target:** N/A
- **Impact:** N/A

## EP-001: Audit Trail and Reporting (→ OBJ-001)
Provide audit log listing, verification, exporting, faceted search, and compliance report generation/viewing.

### US-001-01: As a compliance manager, I want to to browse a list of reports and view/generate a specific report with charts, so I can summarize compliance status for stakeholders, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-001-01**: ReportDetailPage generates and renders report data
- **TC-001-02**: Reports listing page renders report list and navigation links

### US-001-02: As a compliance officer, I want to to verify the integrity of audit records and export them, and view audit entries scoped to a specific target, so I can prove compliance during reviews, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-001-03**: auditApi: verifyAudit and exportAudit call correct endpoints and handle responses

### US-001-03: As a compliance officer, I want to to list and filter audit log entries with facets so I can investigate activity across the system, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-001-04**: auditApi: buildQuery and normalizeList produce correct query params

## EP-002: Authentication and Password Recovery (→ OBJ-002)
Enable users to log in, recover forgotten passwords, reset passwords, and set initial passwords securely.

### US-002-01: As a user, I want to to log in via a login page/view with validation, and have my session restored and profile managed via an auth context, so I can securely access the app, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-002-01**: AuthContext login/logout/restore session lifecycle
- **TC-002-02**: Login page renders LoginPage view and handles route-level session redirect

### US-002-02: As a user, I want to to log in with my email and password, with client-side validation, so I can securely access the system, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-002-03**: LoginPage validates email format before submit

### US-002-03: As a user, I want to to request a password reset, reset my password, and set a new password on first use, so I can regain or establish account access securely, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-002-04**: Forgot password page renders form and triggers password recovery request
- **TC-002-05**: Reset password page validates and submits new password
- **TC-002-06**: SetPasswordPage submits new password and handles failure

### US-002-04: As a invited or forgetful user, I want to to set or reset my password through a dedicated flow with visibility toggles and error handling, so I can regain secure access to my account, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-002-07**: SetPasswordPage validation and submit handling

### US-002-05: As a user, I want to to log in with my email and password, with client-side validation, so I can securely access the application and my session is restored on reload, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-002-08**: AuthContext login/logout/restore session handling
- **TC-002-09**: LoginPage email validation and submit flow

## EP-003: Breach Reporting and Management (→ OBJ-001)
Support reporting, updating, linking evidence, assigning tasks, and closing data breach incidents.

### US-003-01: As a incident responder, I want to to create, assign, and set status on tasks tied to breaches (and cases), so remediation work is tracked to completion, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-003-01**: tasksApi: createCaseTask/createBreachTask create tasks linked to correct entity

### US-003-02: As a DPO, I want to to report a breach, link supporting evidence, and close it once resolved, so incident handling is fully tracked, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-003-02**: breachesApi full lifecycle: report, link evidence, close

### US-003-03: As a DPO, I want to to report new breaches, update, link, and close breach records so that incidents are tracked to resolution, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-003-03**: breachesApi lifecycle: report, update, link evidence, close

## EP-004: Data Source Onboarding and Column Review (→ OBJ-001)
Enable upload of data sources, review and approval of individual columns for inclusion, and submission of sources for compliance sign-off.

### US-004-01: As a reviewer, I want to to review individual columns of a data source, mark them included or excluded, and approve or unapprove them, so the source can be properly classified before submission, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-004-02: As a data steward, I want to to submit a reviewed data source so it is locked from further column edits and moves into the compliance approval pipeline, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-004-03: As a data steward, I want to to upload a new data source so its columns can be catalogued and reviewed for compliance purposes, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

## EP-005: Data Subject Rights Case Handling (→ OBJ-001)
Enable creation and tracking of data subject rights requests (cases), including status, priority, right type, and linked evidence.

### US-005-01: As a case handler, I want to to create tasks linked to a rights case or a breach, assign them to team members, and update their status, so remediation work is tracked to completion, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-005-01**: tasksApi: taskLabel returns correct human-readable label for task states

### US-005-02: As a rights handler, I want to to create, list, view, and update data subject rights cases, and view case evidence, so that subject requests are processed and documented
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-005-02**: rightsApi case creation and label helpers

### US-005-03: As a case handler, I want to to create and update a data subject rights case with status, priority, and linked evidence, so requests are resolved within compliance timelines, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-005-03**: rightsApi case creation and update preserves status/priority/right labels

## EP-006: Evidence Management (→ OBJ-001)
Allow uploading, listing, updating, replacing, and linking evidence files to breaches, cases, processors, and register entries.

### US-006-01: As a compliance officer, I want to to link evidence records to breaches, rights cases, and processors and page/list evidence, so that all related proof is discoverable from the relevant record
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-006-01**: evidenceApi: replaceEvidenceFile and linkEvidence update associations correctly

### US-006-02: As a data owner, I want to to upload, update, replace, and delete evidence files, so I can maintain proof supporting compliance activities, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-006-02**: evidenceApi: uploadEvidence sends multipart file data and handles success/error

### US-006-03: As a compliance officer, I want to see a clear empty state with a heading, help text and an upload button when no proofs exist, and open the existing upload dialog from it, so that I can add the first proof without searching for the upload action
**Priority:** Should Have

**Acceptance Criteria:**
- Given the proofs list has no proofs, when the proofs page loads, then an empty state is shown with an illustration, a heading, help text and an upload button
- Given the empty state is shown, when I click the upload button, then the existing upload dialog opens
- Given the proofs list contains at least one proof, when the page loads, then the empty state is not shown and the list is displayed

**Test Cases:**
- **TC-006-06**: the proofs page loads
- **TC-006-07**: I click the upload button
- **TC-006-08**: the page loads

## EP-007: Notices Workflow (→ OBJ-001)
Support drafting, submitting, approving, and rejecting privacy notices with block-level content management.

### US-007-01: As a content owner, I want to to create, edit, submit, approve, or reject privacy notices and their blocks, so published notices go through a controlled workflow, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-007-01**: noticesApi approval workflow (submit/approve/reject)

### US-007-02: As a content author, I want to to draft a notice with blocks, submit it for review, and have an approver approve or reject it, so published notices are vetted, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-007-02**: noticesApi submit/approve/reject workflow transitions

## EP-008: Processing Activity Register Management (→ OBJ-001)
Allow users to view, update, and approve entries in the register of processing activities, ensuring evidence is attached before approval.

### US-008-01: As a compliance officer, I want to to approve a register entry only if required evidence is attached, so that approvals are backed by proof
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-008-01**: registerApi.canApprove blocks approval without evidence

### US-008-02: As a data steward, I want to to upload data sources, update and review/unapprove columns, set which columns are included, and submit sources, so the data inventory feeding the register is accurate, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-008-02**: sourcesApi column review workflow (approve/unapprove/submit)

### US-008-03: As a compliance officer, I want to to list and register processors, set DPA status, acknowledge purge obligations, and view processor evidence/breaches, so third-party data processing is governed, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-008-03**: processorsApi: listProcessorEvidence and listProcessorBreaches return linked records
- **TC-008-04**: processorsApi: setDpa and setPurgeAck update processor compliance flags

### US-008-04: As a data protection officer, I want to to list, view, update, and approve processing activity register entries with attached evidence, so the register reflects verified activities, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-008-05**: evidenceApi upload, update, replace, and link evidence

## EP-009: Processor and Data Processing Agreement Oversight (→ OBJ-001)
Manage third-party processors, track their Data Processing Agreements (DPAs), purge acknowledgements, and associated evidence and breaches, to ensure vendor compliance with data protection obligations.

### US-009-01: As a compliance officer, I want to to list all registered data processors and view their details so I can track vendor compliance status, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-009-02: As a compliance officer, I want to to record whether a processor has a signed DPA and whether they have acknowledged purge requests, so I can track contractual compliance, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-009-03: As a compliance officer, I want to to see all evidence and breach records linked to a given processor so I can assess their overall risk profile, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

## EP-010: Retention Rules and Legal Holds (→ OBJ-001)
Manage data retention rules, execute retention/purge tasks, and place or release legal holds on data.

### US-010-01: As a compliance administrator, I want to to create retention rules, toggle them, run them, and execute purge tasks, so that data is retained and disposed of according to policy
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-010-01**: retentionApi rule execution and legal hold flow

### US-010-02: As a legal administrator, I want to to create and release legal holds on data, so that data subject to litigation or investigation is preserved beyond normal retention rules
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-010-02**: retentionApi rule execution and legal hold lifecycle

## EP-011: Role-Based Permissions and Navigation (→ OBJ-002)
Manage role-based permission matrices and dynamically render sidebar navigation based on user permissions.

### US-011-01: As a administrator, I want to to view roles, get/reset the default permission matrix, and replace or patch role permissions, so I can control what each role can do, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-011-02: As a user, I want to the app to load my permissions and render sidebar navigation based on my role, so I only see and access functions I'm authorized for, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-011-01**: foundationApi: roleLabel/rolesLabel/roleCodes map role data consistently

### US-011-03: As a administrator, I want to to view and edit the permission matrix per role, reset to default permissions, and see my own effective permissions, so access control aligns with organizational policy, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-011-04: As a logged-in user, I want to the navigation sidebar to reflect only the sections I'm permitted to access, so I don't see unauthorized areas, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-011-02**: permissionsApi holds() and getSidebarNavigation reflect loaded permissions

### US-011-05: As a user, I want to to view my own recent activity and land on a role-aware dashboard, so I have visibility into my actions and a relevant home view, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-011-03**: foundationApi: getUserActivity and getMyActivity fetch correct activity records
- **TC-011-04**: RootPage redirects to correct route based on auth/session state

## Business Rules

### BR-001: Notices require submission and approval before publication
**Rationale:**  | **Enforcement:** 

### BR-002: Register entry approval requires attached evidence
**Rationale:**  | **Enforcement:** 

### BR-003: Retention rules govern automated purge execution
**Rationale:**  | **Enforcement:** 

## Non-Functional Requirements

### NFR-001: Auditability and traceability of all actions
**Category:**  | **Target:**  | **Priority:** 

### NFR-002: Real-time event and notification streaming
**Category:**  | **Target:**  | **Priority:** 

### NFR-003: Real-time in-app notification delivery
**Category:**  | **Target:**  | **Priority:** 

### NFR-004: Real-time notification and event delivery
**Category:**  | **Target:**  | **Priority:**
