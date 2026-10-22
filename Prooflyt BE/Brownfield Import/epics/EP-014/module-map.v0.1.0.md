# Privacy Notice Authoring & Approval Workflow · Implementation Spec

**Epic ID:** `epic:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:privacy-notice-authoring-approval-workflow`  
**Confidence:** inferred (high)  

## Summary

Enable creation, editing, submission, review, and approval/rejection of privacy notices composed of content blocks, tracking completeness and ownership.

## Modules & responsibilities

- `app/api/v1/notices.py`
  - Defines the FastAPI API routes for managing notices, including listing, creating, updating, and handling their workflow lifecycle (submit, reject, approve, publish, retire) as well as retrieving blocks and downloading notice content.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/api/v1/notices.py`
- `app/models/notice.py`
  - Defines the SQLAlchemy Notice model representing a notice record with fields and helper properties/methods for tracking missing blocks, completeness, owner name, and department name.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/models/notice.py`

## Story → module map

### Author drafts and submits a privacy notice for approval

As a notice owner, I can create and edit a privacy notice's content blocks, submit it for review, and have a reviewer approve or reject it.

Grounded modules:
- `app/api/v1/notices.py` — Defines the FastAPI API routes for managing notices, including listing, creating, updating, and handling their workflow lifecycle (submit, reject, approve, publish, retire) as well as retrieving blocks and downloading notice content.

### Author, submit, and approve privacy notices

As a privacy officer, I can create a privacy notice from blocks, list/view notices, update draft content, submit for review, and either approve or reject it, driving the notice through its approval workflow.

Grounded modules:
- `app/api/v1/notices.py` — Defines the FastAPI API routes for managing notices, including listing, creating, updating, and handling their workflow lifecycle (submit, reject, approve, publish, retire) as well as retrieving blocks and downloading notice content.

### Manage supporting evidence uploads and linkage

As a reviewer, I can upload evidence files, link them to breaches/notices, review, edit, replace, remove, and list evidence items.

Grounded modules:
- `app/api/v1/evidence.py` — Defines the API v1 endpoints for uploading, linking, reviewing, editing, replacing, removing, and listing evidence records within the application.

## Constraints (business rules & NFRs)

- **[Business Rule] Notice completeness is derived from required blocks** _(`business_rule:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:notice-completeness-is-derived-from-required-block`, inferred (medium))_: A notice's completeness status is computed from which required content blocks are missing, preventing submission of incomplete notices.

---
_Generated from `15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be` v9._
