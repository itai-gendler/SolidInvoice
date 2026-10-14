---
entities:
- entity: user
  collects:
  - Email
  - Password
references:
- kind: code
  role: implementation
  target: src/UserBundle/Action/Security/Login.php
- kind: code
  role: implementation
  target: src/UserBundle/Security/OAuth/OAuthAuthenticator.php
---

# Sign-in page

Signing in with an email and password or a linked Google account, and the second-factor check that follows when the account uses one.
