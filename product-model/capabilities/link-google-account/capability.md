---
domain: profile
availability:
- {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/UserBundle/Action/Security/OAuthConnect.php
- kind: code
  role: implementation
  target: src/UserBundle/Action/Security/OAuthConnectCheck.php
---

# Link a Google account

Connect one's account to a Google identity, where Google sign-in is configured.
