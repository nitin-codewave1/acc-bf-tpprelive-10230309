# Breach Incident Management

## Test Cases

### Staff reports and manages a breach incident

  - **Breach reporting creates record and triggers notification threshold checks** _(`test_case:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:breach-reporting-creates-record-and-triggers-notif`, inferred (medium))_: Calling report() in app/api/v1/breaches.py with breach details should persist a new breach via breach_service.py, and if severity/impact fields cross configured notification thresholds, should enqueue/trigger notifications. Validates breach creation, impact assessment fields (from migration 1516dc950ea5), and notification threshold logic (from migration b7f4c1a29d05).

---
_Generated from `15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be` v9._
