---
domain: profile
availability:
- {place: 'web::sign-in'}
references:
- kind: code
  role: implementation
  target: src/UserBundle/Action/ForgotPassword/Request.php
- kind: code
  role: implementation
  target: src/UserBundle/Action/ForgotPassword/Reset.php
---

# Reset a password

Choose a new password through an emailed link.
