---
domain: profile
availability:
- {place: 'web::sign-in'}
references:
- kind: code
  role: implementation
  target: src/UserBundle/Action/Register.php
- kind: code
  role: implementation
  target: config/packages/toggler.php
---

# Register

Create an account: open to everyone while registration is allowed, and always to someone following an invitation.
