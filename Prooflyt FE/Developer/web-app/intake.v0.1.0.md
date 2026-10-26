---
id: agent-developer/prooflyt_fe/web-app/INTAKE.md
type: intake
project: 2355a1a6-0cde-4feb-8bd0-f037f7c23507
version: 0.1.0
author: acd154e9-7d7c-493d-b538-c1e75f4fcbbe
produces: agent-developer/prooflyt_fe/web-app/INTAKE.md
depends_on: []
commit_kind: append
confidence: agent
run_id: 9547af9a-51c6-515a-8ce9-048bf28b523c
okf_id: web-app/INTAKE.md
---

<!-- SECTION: web-app.intake | status: VERIFIED -->
## What this run read

| Input | Role(s) | Parsed | Taken from it | How the role was decided |
|---|---|---|---|---|
| `backend-api.md` | api_docs | yes | 23,903 bytes, 16 identifier(s) | declared in INPUTS.yaml |
| `design-brief.md` | design_brief | yes | 11,968 bytes, 11 identifier(s) | declared in INPUTS.yaml |
| `feedback.md` | feedback | yes | 556 bytes, 0 identifier(s) | declared in INPUTS.yaml |
| `requirements.md` | requirements | yes | 2,501 bytes, 4 identifier(s) | declared in INPUTS.yaml |
| `stories.md` | user_stories | yes | 7,385 bytes, 11 identifier(s) | declared in INPUTS.yaml |

## Inputs expected

| Role | Status |
|---|---|
| `requirements` | supplied (1 file(s)) |
| `user_stories` | supplied (1 file(s)) |
| `design_brief` | supplied (1 file(s)) |
| `platform` | not supplied — the run degrades, see GAPS.md |
| `api_docs` | supplied (1 file(s)) |
| `feedback` | supplied (1 file(s)) |

## Identifiers

- Distinct identifiers found: **11**
- Of those, user stories: **11**
- With established acceptance detail: **1** (9%, floor 60%)
  - counted when a story carries inline criteria, **or** a `§` reference that resolves to a real requirements section
- Requirements sections available to resolve against: **0**

Roles were declared in `INPUTS.yaml`.
<!-- /SECTION: web-app.intake -->
