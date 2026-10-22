# Privacy Notice Authoring & Approval Workflow

## Test Cases

### Author, submit, and approve privacy notices

  - **Notice lifecycle: create, submit, reject, approve transitions** _(`test_case:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:notice-lifecycle-create-submit-reject-approve-tran`, inferred (medium))_: Verify app/api/v1/notices.py endpoints enforce correct state transitions: a newly created notice can be submitted, a submitted notice can be rejected (returning to draft/edit state) or approved (finalizing it), and invalid transitions (e.g., approving a draft directly) are rejected with an error.

---
_Generated from `15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be` v9._
