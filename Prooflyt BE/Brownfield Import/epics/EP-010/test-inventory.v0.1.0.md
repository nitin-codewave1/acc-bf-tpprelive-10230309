# Authentication, User Profile & RBAC

## Test Cases

### Admin configures role permission matrix

  - **require_permission dependency denies user without permission** _(`test_case:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:require-permission-dependency-denies-user-without-`, inferred (high))_: Verify that app/core/deps.py's require_permission (and require_all_permissions/require_any_permission) correctly raises a permission-denied AppError when the current user's permissions (from current_permissions) do not include the required permission code, and allows the request through when they do. This is core to enforcing RBAC across all API routes.

### User login, session refresh, and logout

  - **Refresh and logout invalidate/rotate tokens correctly** _(`test_case:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:refresh-and-logout-invalidate-rotate-tokens-correc`, inferred (medium))_: Calling refresh with a valid refresh token should issue a new access token; calling logout should invalidate the session/token so subsequent authenticated requests fail. Ensures auth_token model and auth.py session lifecycle work together.

### User logs in and manages their session

  - **Login issues tokens for valid credentials and rejects invalid ones** _(`test_case:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:login-issues-tokens-for-valid-credentials-and-reje`, inferred (high))_: POST to the login endpoint in app/api/v1/auth.py with valid tenant user credentials should return access/refresh tokens (via _session helper), while invalid credentials should return a 401/403 error. Verifies core authentication flow used by all other endpoints.

---
_Generated from `15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be` v9._
