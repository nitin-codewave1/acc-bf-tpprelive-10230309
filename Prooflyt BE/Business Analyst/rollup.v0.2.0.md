---
id: agent-ba/prooflyt_be/rollup.md
type: spec
project: 2355a1a6-0cde-4feb-8bd0-f037f7c23507
version: 0.2.0
author: acd154e9-7d7c-493d-b538-c1e75f4fcbbe
produces: agent-ba/prooflyt_be/rollup.md
depends_on: []
commit_kind: fork
confidence: agent
run_id: 63c069a0-dc81-584d-96a1-c9a33326ccd5
---

# Business Analysis — D-COPSCAR

## Discovery

**Brief Quality:** ? (Problem: ?, Outcomes: ?, Stakeholders: ?)

**Declaration:** N/A

## Business Objectives

### OBJ-002: Enable organizations to manage end-to-end data privacy compliance operations
- **Leading KPI:** 
- **Lagging KPI:** N/A
- **Target:** N/A
- **Impact:** N/A

## EP-009: Audit Trail & Compliance Reporting (→ OBJ-002)
Provide a searchable, filterable audit log of platform actions with facets by module/actor, exportable for compliance reporting, plus real-time event notifications via websocket and outbound notification thresholds.

### US-009-01: As a user, I want to Admin reviews and exports the audit trail, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-009-02: As a user, I want to Browse, filter, export, and verify audit log integrity, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-009-03: As a user, I want to Have each logout recorded as an audit log entry, so that the audit trail shows when every user session ended
**Priority:** Must Have

**Acceptance Criteria:**
- Given a logged-in user, when the user logs out, then an audit log entry is written recording the user, tenant, and logout timestamp.
- Given a logout request fails to complete, when the failure occurs, then no logout audit entry is written for that request and the failure is logged.
- Given an audit log entry for a logout, when it is viewed in the audit trail, then it is listed with the event type 'logout'.

**Test Cases:**
- **TC-009-01**: the user logs out
- **TC-009-02**: the failure occurs
- **TC-009-03**: it is viewed in the audit trail

## EP-010: Authentication, User Profile & RBAC (→ OBJ-002)
Support secure login/logout/refresh, session management, user profile self-service (avatar, phone, activity), and a fine-grained role/permission matrix for controlling access to platform modules.

### US-010-01: As a user, I want to Admin configures role permission matrix, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-010-01**: require_permission dependency denies user without permission

### US-010-02: As a user, I want to Administer roles and granular permission matrix, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-010-03: As a user, I want to Manage user profile including avatar and activity history, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-010-04: As a user, I want to Onboard and manage tenant users, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-010-05: As a user, I want to User login, session refresh, and logout, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-010-02**: Refresh and logout invalidate/rotate tokens correctly

### US-010-06: As a user, I want to User logs in and manages their session, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-010-03**: Login issues tokens for valid credentials and rejects invalid ones

### US-010-07: As a user, I want to User manages their own profile, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

## EP-011: Breach Incident Management (→ OBJ-002)
Allow staff to report, track, edit, and manage data breach incidents including impact assessments, remediation tasks, and supporting evidence, with SLA tracking against notification deadlines.

### US-011-01: As a user, I want to Capture breach impact assessment details, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-011-02: As a user, I want to Cross-cutting task assignment and status tracking, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-011-03: As a user, I want to Report, edit, and track breach incidents with tasks and evidence, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-011-04: As a user, I want to Staff reports and manages a breach incident, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-011-01**: Breach reporting creates record and triggers notification threshold checks

## EP-012: Data Source Discovery & Column Classification (→ OBJ-002)
Allow users to upload data sources, automatically classify their columns via background jobs, review/approve/include columns, and submit sources into the data register.

### US-012-01: As a user, I want to Maintain a compliance register of data processing entries, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-012-02: As a user, I want to Upload data sources and classify/review columns, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-012-01**: Source upload and column review/approval workflow

### US-012-03: As a user, I want to User uploads a data source and reviews classified columns, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-012-02**: Classification job assigns data classification based on source content
- **TC-012-03**: SourceJob model tracks classification job lifecycle states

## EP-013: Data Subject Rights Case Management (→ OBJ-002)
Support intake and processing of data subject rights requests (e.g., access, deletion) including case tracking, task assignment, evidence collection, and overdue/SLA monitoring.

### US-013-01: As a user, I want to Handler manages a rights request case to completion, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-013-01**: SLA sweep job escalates or notifies for overdue tasks

### US-013-02: As a user, I want to Manage data subject rights cases and tasks, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

## EP-014: Privacy Notice Authoring & Approval Workflow (→ OBJ-002)
Enable creation, editing, submission, review, and approval/rejection of privacy notices composed of content blocks, tracking completeness and ownership.

### US-014-01: As a user, I want to Author drafts and submits a privacy notice for approval, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-014-02: As a user, I want to Author, submit, and approve privacy notices, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**
- **TC-014-01**: Notice lifecycle: create, submit, reject, approve transitions

### US-014-03: As a user, I want to Manage supporting evidence uploads and linkage, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

## EP-015: Retention Rules & Legal Hold Enforcement (→ OBJ-002)
Enable configuration of data retention rules, execution of deletion tasks per rule, and placement/release of legal holds to prevent premature deletion of data under litigation or investigation.

### US-015-01: As a user, I want to Compliance officer configures and runs retention rules, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-015-02: As a user, I want to Configure retention rules and enforce legal holds, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

## EP-016: Third-Party Processor Oversight (→ OBJ-002)
Track third-party data processors, their associated evidence and linked breaches, data processing agreement (DPA) status, and purge acknowledgements, plus assess sharing risk.

### US-016-01: As a user, I want to Compliance officer tracks processor DPA and purge status, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

### US-016-02: As a user, I want to Track processors, their DPAs, and purge acknowledgements, so that 
**Priority:** 

**Acceptance Criteria:**

**Test Cases:**

## Business Rules

### BR-007: Breach notification countdown is time-bound
**Rationale:**  | **Enforcement:** 

### BR-008: Notice completeness is derived from required blocks
**Rationale:**  | **Enforcement:** 

### BR-009: Orphaned classification jobs are requeued
**Rationale:**  | **Enforcement:** 

### BR-010: Password policy enforced at credential/token layer
**Rationale:**  | **Enforcement:** 

### BR-011: SLA sweep job enforces time-bound case deadlines
**Rationale:**  | **Enforcement:** 

## Non-Functional Requirements

### NFR-003: Automated SLA sweeping for time-bound cases
**Category:**  | **Target:**  | **Priority:** 

### NFR-004: Tenant-scoped WebSocket event streaming
**Category:**  | **Target:**  | **Priority:**
