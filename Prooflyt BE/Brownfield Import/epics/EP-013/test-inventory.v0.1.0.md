# Data Subject Rights Case Management

## Test Cases

### Handler manages a rights request case to completion

  - **SLA sweep job escalates or notifies for overdue tasks** _(`test_case:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:sla-sweep-job-escalates-or-notifies-for-overdue-ta`, inferred (low))_: Running app/jobs/sla_sweep.py against tasks/rights requests past their SLA deadline should trigger notification or escalation logic, updating task_service.py records accordingly. Verifies background job correctness for time-sensitive compliance obligations.

---
_Generated from `15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be` v9._
