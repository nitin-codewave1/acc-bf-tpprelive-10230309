# Data Source Discovery & Column Classification

## Test Cases

### Upload data sources and classify/review columns

  - **Source upload and column review/approval workflow** _(`test_case:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:source-upload-and-column-review-approval-workflow`, inferred (medium))_: Verify app/api/v1/sources.py's upload_source stores a new source with unreviewed columns, update_column/set_columns_included correctly mutate column metadata, review_column/unapprove_column toggle approval state, and submit_source is blocked until all required columns are reviewed.

### User uploads a data source and reviews classified columns

  - **Classification job assigns data classification based on source content** _(`test_case:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:classification-job-assigns-data-classification-bas`, inferred (low))_: app/jobs/classify.py, using app/services/classification.py, should correctly classify ingested source/register data (e.g. tagging PII categories) and persist results to the register model. Ensures automated classification pipeline behaves deterministically for known inputs.
  - **SourceJob model tracks classification job lifecycle states** _(`test_case:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:sourcejob-model-tracks-classification-job-lifecycl`, inferred (medium))_: Verify that app/models/source_job.py correctly represents job state transitions (queued, running, done, failed) consumed by app/jobs/classify.py's run/_fail/_still_queued/requeue_orphans functions, ensuring stuck or orphaned jobs are detected and requeued as expected.

---
_Generated from `15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be` v9._
