# Authentication, User Profile & RBAC · Implementation Spec

**Epic ID:** `epic:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:authentication-user-profile-rbac`  
**Confidence:** inferred (high)  

## Summary

Support secure login/logout/refresh, session management, user profile self-service (avatar, phone, activity), and a fine-grained role/permission matrix for controlling access to platform modules.

## Modules & responsibilities

- `app/api/v1/auth.py`
  - This module implements the API endpoints for authentication and user account management, including login/logout/token refresh, password reset and change, invite acceptance, and profile/avatar management.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/api/v1/auth.py`
- `app/api/v1/roles.py`
  - This module defines FastAPI API endpoints for managing and querying roles, permissions, and the role-permission matrix, including listing roles/permissions, viewing and resetting the permission matrix, checking current user permissions, and getting/replacing/patching a role's permissions.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/api/v1/roles.py`
- `app/core/security.py`
  - Provides security utility functions for password hashing/verification, password policy enforcement, JWT access token creation/decoding, and generation/hashing of secure link tokens.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/core/security.py`
- `app/core/deps.py`
  - Provides FastAPI dependency functions for authenticating the current user and enforcing permission-based authorization on protected routes.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/core/deps.py`
- `app/models/rbac.py`
  - Defines SQLAlchemy ORM models (Role, Permission, RolePermission, UserRole) implementing role-based access control (RBAC) data structures and their relationships for the application.
  - ontology: `code_module:046a011d-54b4-4f2a-a4b7-aa24400b64cb/app/models/rbac.py`

## Story → module map

### Admin configures role permission matrix

As an administrator, I can view and edit the permission matrix mapping roles to module permissions, reset it to defaults, and check my own effective permissions.

Grounded modules:
- `app/api/v1/roles.py` — This module defines FastAPI API endpoints for managing and querying roles, permissions, and the role-permission matrix, including listing roles/permissions, viewing and resetting the permission matrix, checking current user permissions, and getting/replacing/patching a role's permissions.
- `app/core/permissions.py` — Defines the application's permission system, including module and permission enumerations and a PermissionSpec class used to declare and check access control rules.

### Administer roles and granular permission matrix

As an admin, I can view roles/permissions, edit the permission matrix, reset to defaults, and inspect my own effective permissions, so RBAC can be tuned per tenant.

Grounded modules:
- `app/api/v1/roles.py` — This module defines FastAPI API endpoints for managing and querying roles, permissions, and the role-permission matrix, including listing roles/permissions, viewing and resetting the permission matrix, checking current user permissions, and getting/replacing/patching a role's permissions.
- `app/core/permissions.py` — Defines the application's permission system, including module and permission enumerations and a PermissionSpec class used to declare and check access control rules.
- `app/core/deps.py` — Provides FastAPI dependency functions for authenticating the current user and enforcing permission-based authorization on protected routes.

### Manage user profile including avatar and activity history

As a user, I can view and update my profile (including uploading an avatar) and review my own activity history.

Grounded modules:
- `app/api/v1/auth.py` — This module implements the API endpoints for authentication and user account management, including login/logout/token refresh, password reset and change, invite acceptance, and profile/avatar management.
- `alembic/versions/eceea0446070_user_avatar_url.py` — This Alembic migration script adds (and on downgrade removes) an 'avatar_url' column to the user table in the database schema.
- `alembic/versions/e53bedadd1b9_user_phone.py` — This Alembic migration module adds (and can revert) a phone column to the user table in the database schema, via its upgrade and downgrade functions.

### Onboard and manage tenant users

As an org admin, I can invite users, resend invites, edit user details, set roles, activate/deactivate, and remove users, and get an org overview.

Grounded modules:
- `app/api/v1/foundation.py` — Defines FastAPI API v1 endpoints for foundational administrative operations, including user management (overview, invite, activity, roles, activation, removal) and department management (list, get, add, edit, remove).

### User login, session refresh, and logout

As a user, I can log in with credentials, receive a session/access token, refresh it, and log out, so I can securely access the platform across sessions.

Grounded modules:
- `app/api/v1/auth.py` — This module implements the API endpoints for authentication and user account management, including login/logout/token refresh, password reset and change, invite acceptance, and profile/avatar management.
- `app/core/security.py` — Provides security utility functions for password hashing/verification, password policy enforcement, JWT access token creation/decoding, and generation/hashing of secure link tokens.

### User logs in and manages their session

As a user, I can log in with credentials, receive an access token, refresh it, and log out, so that I can securely access the platform within my tenant.

Grounded modules:
- `app/api/v1/auth.py` — This module implements the API endpoints for authentication and user account management, including login/logout/token refresh, password reset and change, invite acceptance, and profile/avatar management.

### User manages their own profile

As a user, I can view and update my profile information, upload an avatar, and review my recent activity history.

Grounded modules:
- `app/api/v1/auth.py` — This module implements the API endpoints for authentication and user account management, including login/logout/token refresh, password reset and change, invite acceptance, and profile/avatar management.
- `alembic/versions/eceea0446070_user_avatar_url.py` — This Alembic migration script adds (and on downgrade removes) an 'avatar_url' column to the user table in the database schema.

## Constraints (business rules & NFRs)

- **[Business Rule] Password policy enforced at credential/token layer** _(`business_rule:15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be:password-policy-enforced-at-credential-token-layer`, inferred (high))_: Password hashing/verification and password_policy_error enforce strength/security policy, and link tokens are generated/hashed securely for invite/reset flows.

---
_Generated from `15fb1dcc-6f47-421a-b3c6-23fbcc168227/gitlab-codewave-com-web-prooflyt-be` v9._
