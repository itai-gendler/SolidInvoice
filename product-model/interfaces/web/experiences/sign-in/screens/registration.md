---
entities:
- entity: user
  collects:
  - Email
  - Password
- entity: invitation
  shows:
  - Email
references:
- kind: code
  role: implementation
  target: src/UserBundle/Action/Register.php
---

# Registration

Creating an account, open to everyone while registration is allowed and always to someone with an invitation.
