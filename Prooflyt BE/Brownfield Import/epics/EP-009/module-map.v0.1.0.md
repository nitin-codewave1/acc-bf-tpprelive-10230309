# Audit Trail & Compliance Reporting · Implementation Spec

**Epic ID:** `epic:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:audit-trail-compliance-reporting`  
**Confidence:** inferred (high)  

## Summary

Provide a searchable, filterable audit log of platform actions with facets by module/actor, exportable for compliance reporting, plus real-time event notifications via websocket and outbound notification thresholds.

## Modules & responsibilities

- `app/api/v1/audit.py`
  - This module implements the FastAPI v1 audit API, providing endpoints to list, filter/facet, export, and verify audit log records along with their response schemas.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/api/v1/audit.py`
- `app/models/audit.py`
  - Defines the AuditEvent SQLAlchemy model for persisting audit log records (e.g., tracking user or system actions) in the application's database.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/models/audit.py`
- `app/api/v1/ws.py`
  - Implements a FastAPI WebSocket endpoint that authenticates tenant/user context and streams real-time events (via Redis pub/sub) to clients while managing heartbeat and message pump/drain tasks.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/api/v1/ws.py`
- `alembic/versions/b7f4c1a29d05_notification_thresholds.py`
  - This Alembic migration module defines upgrade/downgrade functions to add and remove notification threshold-related schema changes in the database.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/alembic/versions/b7f4c1a29d05_notification_thresholds.py`

## Story → module map

### Admin reviews and exports the audit trail

As an administrator, I can list audit events, filter by module/actor facets, export the results, and verify the integrity of the audit log.

Grounded modules:
- `app/api/v1/audit.py` — This module implements the FastAPI v1 audit API, providing endpoints to list, filter/facet, export, and verify audit log records along with their response schemas.

### Browse, filter, export, and verify audit log integrity

As an auditor, I can list audit entries with module/actor facets, export the audit log, and verify its integrity/tamper-evidence.

Grounded modules:
- `app/api/v1/audit.py` — This module implements the FastAPI v1 audit API, providing endpoints to list, filter/facet, export, and verify audit log records along with their response schemas.

## Constraints (business rules & NFRs)

- **[NFR] Tenant-scoped WebSocket event streaming** _(`nfr:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:tenant-scoped-websocket-event-streaming`, inferred (high))_: The system pushes real-time domain events to connected clients over a tenant-scoped WebSocket channel, with heartbeat and drain handling for connection lifecycle management.

---
_Generated from `15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be` v9._
