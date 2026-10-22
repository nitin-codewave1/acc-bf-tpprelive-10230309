# Data Source Discovery & Column Classification · Implementation Spec

**Epic ID:** `epic:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:data-source-discovery-column-classification`  
**Confidence:** inferred (high)  

## Summary

Allow users to upload data sources, automatically classify their columns via background jobs, review/approve/include columns, and submit sources into the data register.

## Modules & responsibilities

- `app/api/v1/sources.py`
  - Defines the FastAPI API endpoints for managing data sources, including uploading, listing, retrieving, updating and reviewing/approving their columns, and submitting/approving sources for classification workflows.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/api/v1/sources.py`
- `app/models/source.py`
  - Defines the SQLAlchemy ORM models Source and SourceColumn, representing data sources and their columns along with helper properties for owner/department names and field status counts (found, included, approved, pending) and column code registration.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/models/source.py`
- `app/jobs/classify.py`
  - Implements a background job that classifies sources by running classification jobs, handling failures, and requeuing orphaned jobs that are no longer actually queued.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/jobs/classify.py`
- `app/jobs/queue.py`
  - Provides a Redis-backed RQ job queue setup and a helper function to enqueue classification jobs for asynchronous processing.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/jobs/queue.py`

## Story → module map

### Maintain a compliance register of data processing entries

As a compliance officer, I can list, view, update and approve register entries capturing the organization's data processing activities.

Grounded modules:
- `app/api/v1/register.py` — Defines FastAPI API endpoints for listing, retrieving, updating, and approving register entries, delegating business logic to the app's services and enforcing permissions.

### Upload data sources and classify/review columns

As a data steward, I can upload a data source, view its discovered columns, update/approve/unapprove column classifications, mark columns as included, and submit the source, while classification runs asynchronously via a background job queue.

Grounded modules:
- `app/api/v1/sources.py` — Defines the FastAPI API endpoints for managing data sources, including uploading, listing, retrieving, updating and reviewing/approving their columns, and submitting/approving sources for classification workflows.
- `app/jobs/classify.py` — Implements a background job that classifies sources by running classification jobs, handling failures, and requeuing orphaned jobs that are no longer actually queued.
- `app/jobs/queue.py` — Provides a Redis-backed RQ job queue setup and a helper function to enqueue classification jobs for asynchronous processing.

### User uploads a data source and reviews classified columns

As a data owner, I can upload a source file, have its columns auto-classified asynchronously, review and approve/unapprove each column, decide which to include, and submit the source for registration.

Grounded modules:
- `app/api/v1/sources.py` — Defines the FastAPI API endpoints for managing data sources, including uploading, listing, retrieving, updating and reviewing/approving their columns, and submitting/approving sources for classification workflows.

## Constraints (business rules & NFRs)

- **[Business Rule] Orphaned classification jobs are requeued** _(`business_rule:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:orphaned-classification-jobs-are-requeued`, inferred (medium))_: Classification jobs that remain queued too long without progress are detected and automatically requeued to ensure source columns eventually get classified.

---
_Generated from `15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be` v9._
