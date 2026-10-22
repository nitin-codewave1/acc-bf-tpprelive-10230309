---
id: agent-developer/prooflyt_be/backend/INTAKE.md
type: intake
project: 2355a1a6-0cde-4feb-8bd0-f037f7c23507
version: 0.3.0
author: acd154e9-7d7c-493d-b538-c1e75f4fcbbe
produces: agent-developer/prooflyt_be/backend/INTAKE.md
depends_on: []
commit_kind: fork
confidence: agent
run_id: d9b27c05-b7a2-58c2-b2f1-253a5d91ea2b
okf_id: backend/INTAKE.md
---

<!-- SECTION: backend.intake | status: VERIFIED -->
## What this run read

| Input | Role(s) | Parsed | Taken from it | How the role was decided |
|---|---|---|---|---|
| `design-brief.md` | design_brief | yes | 1,429 bytes, 1 identifier(s) | declared in INPUTS.yaml |
| `feedback.md` | feedback | yes | 48,102 bytes, 17 identifier(s) | declared in INPUTS.yaml |
| `requirements.md` | requirements | yes | 12,749 bytes, 8 identifier(s) | declared in INPUTS.yaml |
| `stories.md` | user_stories | yes | 3,018 bytes, 8 identifier(s) | declared in INPUTS.yaml |

## Inputs expected

| Role | Status |
|---|---|
| `requirements` | supplied (1 file(s)) |
| `user_stories` | supplied (1 file(s)) |
| `design_brief` | supplied (1 file(s)) |
| `platform` | not supplied — the run degrades, see GAPS.md |
| `api_docs` | not supplied — the run degrades, see GAPS.md |
| `feedback` | supplied (1 file(s)) |

## Identifiers

- Distinct identifiers found: **8**
- Of those, user stories: **8**
- With established acceptance detail: **1** (12%, floor 60%)
  - counted when a story carries inline criteria, **or** a `§` reference that resolves to a real requirements section
- Requirements sections available to resolve against: **0**

Roles were declared in `INPUTS.yaml`.
<!-- /SECTION: backend.intake -->
