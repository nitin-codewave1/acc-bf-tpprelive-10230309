---
id: agent-developer/prooflyt_be/backend/SELF-CHECK.md
type: self-check
project: 2355a1a6-0cde-4feb-8bd0-f037f7c23507
version: 0.2.0
author: acd154e9-7d7c-493d-b538-c1e75f4fcbbe
produces: agent-developer/prooflyt_be/backend/SELF-CHECK.md
depends_on: []
commit_kind: fork
confidence: agent
run_id: 63c069a0-dc81-584d-96a1-c9a33326ccd5
okf_id: backend/SELF-CHECK.md
---

<!-- SECTION: backend.self-check | status: VERIFIED -->
## Verification pass

| # | Check | Result | Detail |
|---|---|---|---|
| 1 | anchors open and close; ids unique and well-formed | **PASS** | 11 section(s); all 11 sections present, in order |
| 2 | every referenced id resolves | **PASS** | every id cited carries this run's surface code |
| 3 | every minted id carries this surface's code | **PASS** | 30 minted, all carrying `BE` |
| 4 | no VERIFIED section contains an uncited claim | **NOT RUN** | a judgement about prose; the document's own verification pass covers it |
| 5 | locked sections reproduced byte-for-byte | **PASS** | the document is written through the locking engine |
| 6 | every story this document answers for appears in the coverage table | **FAIL** | 8 in scope, 6 not found in the document: US-010, US-011, US-012, US-013, US-014, US-015 |
| 7 | no schema is restated | **NOT RUN** | a judgement about prose, not a pattern this module can assert |
| 8 | no file written outside output_root | **PASS** | every write is jailed to `/tmp/qbit/specialist/63c069a0-dc81-584d-96a1-c9a33326ccd5/001_prooflyt_be-1-agent-developer_agent-developer/devagent/output/backend` |
| 9 | every Q- has a class; every GAP- names its closing artefact | **NOT RUN** | 20 GAP- id(s) are defined in the specification's prose; whether each names a closing artefact is the document's own verification pass |
| 10 | no GAP- raised for a condition that cannot occur | **NOT RUN** | a judgement about the condition, not the id |

**5 passed, 1 failed, 4 not run.**

A check marked `NOT RUN` has nothing to check yet at this milestone — no specification sections exist. It is reported as not run rather than as a pass: reporting a pass that was never performed is invariant I-2 broken against ourselves.
<!-- /SECTION: backend.self-check -->
