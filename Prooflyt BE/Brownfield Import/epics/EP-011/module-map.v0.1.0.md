# Breach Incident Management · Implementation Spec

**Epic ID:** `epic:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:breach-incident-management`  
**Confidence:** inferred (high)  

## Summary

Allow staff to report, track, edit, and manage data breach incidents including impact assessments, remediation tasks, and supporting evidence, with SLA tracking against notification deadlines.

## Modules & responsibilities

- `app/api/v1/breaches.py`
  - Defines FastAPI API v1 endpoints for managing data breaches, including listing, reporting, retrieving, editing, deleting, closing, and linking breaches, as well as managing their associated tasks and evidence.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/api/v1/breaches.py`
- `app/models/breach.py`
  - Defines the Breach SQLAlchemy model representing a data/security breach record, including fields and helper properties for time remaining to respond and human-readable names for the reporter, department, and handler.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/models/breach.py`
- `alembic/versions/1516dc950ea5_breach_impact_assessment_fields.py`
  - This Alembic migration module adds and removes database schema fields related to breach impact assessment, via its upgrade and downgrade functions.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/alembic/versions/1516dc950ea5_breach_impact_assessment_fields.py`

## Story → module map

### Capture breach impact assessment details

As a compliance officer, I can record impact assessment fields on a breach record to support regulatory risk evaluation.

Grounded modules:
- `alembic/versions/1516dc950ea5_breach_impact_assessment_fields.py` — This Alembic migration module adds and removes database schema fields related to breach impact assessment, via its upgrade and downgrade functions.

### Cross-cutting task assignment and status tracking

As a case/task owner across breach, rights, and other workflows, I can list tasks, view task detail, assign owners, and set status.

Grounded modules:
- `app/api/v1/tasks.py` — Defines FastAPI API v1 endpoints for listing, retrieving, assigning, and updating the status of tasks, delegating business logic to services with permission and database dependencies.

### Report, edit, and track breach incidents with tasks and evidence

As a compliance officer, I can report a breach, edit/delete it, manage its remediation tasks, and attach supporting evidence.

Grounded modules:
- `app/api/v1/breaches.py` — Defines FastAPI API v1 endpoints for managing data breaches, including listing, reporting, retrieving, editing, deleting, closing, and linking breaches, as well as managing their associated tasks and evidence.

### Staff reports and manages a breach incident

As a staff member, I can report a new breach, view/edit its details, assign remediation tasks, and attach evidence, so the organization can respond and document the incident.

Grounded modules:
- `app/api/v1/breaches.py` — Defines FastAPI API v1 endpoints for managing data breaches, including listing, reporting, retrieving, editing, deleting, closing, and linking breaches, as well as managing their associated tasks and evidence.

## Constraints (business rules & NFRs)

- **[Business Rule] Breach notification countdown is time-bound** _(`business_rule:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:breach-notification-countdown-is-time-bound`, inferred (medium))_: Each breach tracks hours remaining until the regulatory notification deadline, computed from the incident timestamp, ensuring timely regulatory notification per compliance requirements.
- **[Business Rule] SLA sweep job enforces time-bound case deadlines** _(`business_rule:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:sla-sweep-job-enforces-time-bound-case-deadlines`, inferred (high))_: A scheduled sla_sweep job runs to detect and act on cases/breaches/notices approaching or exceeding SLA deadlines, implementing the automated SLA sweeping NFR.
- **[NFR] Automated SLA sweeping for time-bound cases** _(`nfr:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:automated-sla-sweeping-for-time-bound-cases`, inferred (medium))_: A background job periodically sweeps rights cases and other time-bound records to detect and flag overdue items, ensuring compliance deadlines are proactively surfaced rather than missed.

---
_Generated from `15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be` v9._
