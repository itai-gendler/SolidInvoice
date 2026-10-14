---
domain: users
availability:
- {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/UserBundle/Action/InviteUser.php
- kind: code
  role: implementation
  target: src/UserBundle/Action/ResendUserInvite.php
- kind: code
  role: implementation
  target: src/UserBundle/Action/DeleteUserInvite.php
- kind: doc
  role: context
  target: docs/docs/companies/overview.md
---

# Resend an invitation

Send a pending invitation again with a fresh expiry.
