---
entities:
- entity: user
  collects:
  - Email
  - Password
references:
- kind: code
  role: implementation
  target: src/UserBundle/Action/ForgotPassword/Request.php
- kind: code
  role: implementation
  target: src/UserBundle/Action/ForgotPassword/Reset.php
---

# Password reset

Asking for a reset link and choosing a new password from it.
