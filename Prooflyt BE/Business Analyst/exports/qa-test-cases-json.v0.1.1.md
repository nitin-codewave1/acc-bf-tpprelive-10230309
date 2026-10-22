[
  {
    "testId": "TC-010-01",
    "title": "require_permission dependency denies user without permission",
    "story": "US-010-01",
    "epic": "EP-010",
    "preconditions": "",
    "steps": "",
    "expectedResult": "Verify that app/core/deps.py's require_permission (and require_all_permissions/require_any_permission) correctly raises a permission-denied AppError when the current user's permissions (from current_permissions) do not include the required permission code, and allows the request through when they do. This is core to enforcing RBAC across all API routes.",
    "module": "authentication--user-profile---rbac",
    "acceptanceCriteria": ""
  },
  {
    "testId": "TC-010-02",
    "title": "Refresh and logout invalidate/rotate tokens correctly",
    "story": "US-010-05",
    "epic": "EP-010",
    "preconditions": "",
    "steps": "",
    "expectedResult": "Calling refresh with a valid refresh token should issue a new access token; calling logout should invalidate the session/token so subsequent authenticated requests fail. Ensures auth_token model and auth.py session lifecycle work together.",
    "module": "authentication--user-profile---rbac",
    "acceptanceCriteria": ""
  },
  {
    "testId": "TC-010-03",
    "title": "Login issues tokens for valid credentials and rejects invalid ones",
    "story": "US-010-06",
    "epic": "EP-010",
    "preconditions": "",
    "steps": "",
    "expectedResult": "POST to the login endpoint in app/api/v1/auth.py with valid tenant user credentials should return access/refresh tokens (via _session helper), while invalid credentials should return a 401/403 error. Verifies core authentication flow used by all other endpoints.",
    "module": "authentication--user-profile---rbac",
    "acceptanceCriteria": ""
  },
  {
    "testId": "TC-011-01",
    "title": "Breach reporting creates record and triggers notification threshold checks",
    "story": "US-011-04",
    "epic": "EP-011",
    "preconditions": "",
    "steps": "",
    "expectedResult": "Calling report() in app/api/v1/breaches.py with breach details should persist a new breach via breach_service.py, and if severity/impact fields cross configured notification thresholds, should enqueue/trigger notifications. Validates breach creation, impact assessment fields (from migration 1516dc950ea5), and notification threshold logic (from migration b7f4c1a29d05).",
    "module": "breach-incident-management",
    "acceptanceCriteria": ""
  },
  {
    "testId": "TC-012-01",
    "title": "Source upload and column review/approval workflow",
    "story": "US-012-02",
    "epic": "EP-012",
    "preconditions": "",
    "steps": "",
    "expectedResult": "Verify app/api/v1/sources.py's upload_source stores a new source with unreviewed columns, update_column/set_columns_included correctly mutate column metadata, review_column/unapprove_column toggle approval state, and submit_source is blocked until all required columns are reviewed.",
    "module": "data-source-discovery---column-classific",
    "acceptanceCriteria": ""
  },
  {
    "testId": "TC-012-02",
    "title": "Classification job assigns data classification based on source content",
    "story": "US-012-03",
    "epic": "EP-012",
    "preconditions": "",
    "steps": "",
    "expectedResult": "app/jobs/classify.py, using app/services/classification.py, should correctly classify ingested source/register data (e.g. tagging PII categories) and persist results to the register model. Ensures automated classification pipeline behaves deterministically for known inputs.",
    "module": "data-source-discovery---column-classific",
    "acceptanceCriteria": ""
  },
  {
    "testId": "TC-012-03",
    "title": "SourceJob model tracks classification job lifecycle states",
    "story": "US-012-03",
    "epic": "EP-012",
    "preconditions": "",
    "steps": "",
    "expectedResult": "Verify that app/models/source_job.py correctly represents job state transitions (queued, running, done, failed) consumed by app/jobs/classify.py's run/_fail/_still_queued/requeue_orphans functions, ensuring stuck or orphaned jobs are detected and requeued as expected.",
    "module": "data-source-discovery---column-classific",
    "acceptanceCriteria": ""
  },
  {
    "testId": "TC-013-01",
    "title": "SLA sweep job escalates or notifies for overdue tasks",
    "story": "US-013-01",
    "epic": "EP-013",
    "preconditions": "",
    "steps": "",
    "expectedResult": "Running app/jobs/sla_sweep.py against tasks/rights requests past their SLA deadline should trigger notification or escalation logic, updating task_service.py records accordingly. Verifies background job correctness for time-sensitive compliance obligations.",
    "module": "data-subject-rights-case-management",
    "acceptanceCriteria": ""
  },
  {
    "testId": "TC-014-01",
    "title": "Notice lifecycle: create, submit, reject, approve transitions",
    "story": "US-014-02",
    "epic": "EP-014",
    "preconditions": "",
    "steps": "",
    "expectedResult": "Verify app/api/v1/notices.py endpoints enforce correct state transitions: a newly created notice can be submitted, a submitted notice can be rejected (returning to draft/edit state) or approved (finalizing it), and invalid transitions (e.g., approving a draft directly) are rejected with an error.",
    "module": "privacy-notice-authoring---approval-work",
    "acceptanceCriteria": ""
  }
]