---
entities:
- entity: user
  shows:
  - Name
  - Email
  - Mobile
  - Google account
  collects:
  - Name
  - Email
  - Mobile
  - Password
references:
- kind: code
  role: implementation
  target: src/UserBundle/Action/Profile.php
- kind: code
  role: implementation
  target: src/UserBundle/Action/EditProfile.php
- kind: code
  role: implementation
  target: src/UserBundle/Action/Security/ChangePassword.php
---

# Profile

The User's own details, password and linked Google account.
