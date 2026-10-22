# Data Subject Rights Case Management · Implementation Spec

**Epic ID:** `epic:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:data-subject-rights-case-management`  
**Confidence:** inferred (high)  

## Summary

Support intake and processing of data subject rights requests (e.g., access, deletion) including case tracking, task assignment, evidence collection, and overdue/SLA monitoring.

## Modules & responsibilities

- `app/api/v1/rights.py`
  - Defines FastAPI API endpoints for managing 'rights' cases, including listing, creating, retrieving, and updating cases, as well as managing associated tasks and evidence.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/api/v1/rights.py`
- `app/models/rights.py`
  - Defines the RightsCase database model, including its fields and helper methods (days_left, is_overdue) for tracking deadlines and overdue status of a rights-related case.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/models/rights.py`
- `app/jobs/sla_sweep.py`
  - This module implements a scheduled job (run function) that sweeps through tenant records in the database to check and enforce SLA (Service Level Agreement) compliance, likely flagging or acting on breaches.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/jobs/sla_sweep.py`

## Story → module map

### Handler manages a rights request case to completion

As a case handler, I can create a rights case, update its status, add tasks and evidence, and see whether it is overdue, so I can respond within regulatory timeframes.

Grounded modules:
- `app/api/v1/rights.py` — Defines FastAPI API endpoints for managing 'rights' cases, including listing, creating, retrieving, and updating cases, as well as managing associated tasks and evidence.
- `app/models/rights.py` — Defines the RightsCase database model, including its fields and helper methods (days_left, is_overdue) for tracking deadlines and overdue status of a rights-related case.

### Manage data subject rights cases and tasks

As a rights case handler, I can create and update cases, list/create case tasks, and manage supporting evidence for DSR cases.

Grounded modules:
- `app/api/v1/rights.py` — Defines FastAPI API endpoints for managing 'rights' cases, including listing, creating, retrieving, and updating cases, as well as managing associated tasks and evidence.

## Constraints (business rules & NFRs)

- **[Business Rule] SLA sweep job enforces time-bound case deadlines** _(`business_rule:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:sla-sweep-job-enforces-time-bound-case-deadlines`, inferred (high))_: A scheduled sla_sweep job runs to detect and act on cases/breaches/notices approaching or exceeding SLA deadlines, implementing the automated SLA sweeping NFR.
- **[NFR] Automated SLA sweeping for time-bound cases** _(`nfr:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:automated-sla-sweeping-for-time-bound-cases`, inferred (medium))_: A background job periodically sweeps rights cases and other time-bound records to detect and flag overdue items, ensuring compliance deadlines are proactively surfaced rather than missed.

---
_Generated from `15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be` v9._
