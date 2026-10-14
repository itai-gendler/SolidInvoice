---
entities:
- entity: user
  shows:
  - Name
  - Email
- entity: invitation
  shows:
  - Email
  - Expires at
  collects:
  - Email
references:
- kind: code
  role: implementation
  target: src/UserBundle/Action/Users.php
- kind: code
  role: implementation
  target: src/UserBundle/Action/InviteUser.php
---

# Users

The people in the company and the invitations waiting to be accepted.
