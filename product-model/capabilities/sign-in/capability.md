---
availability:
- {place: 'web::sign-in'}
references:
- kind: code
  role: implementation
  target: src/UserBundle/Action/Security/Login.php
- kind: code
  role: implementation
  target: src/UserBundle/Security/OAuth/OAuthAuthenticator.php
- kind: code
  role: implementation
  target: config/packages/security.php
- kind: doc
  role: intent
  target: docs/docs/integrations/google-oauth.md
---

# Sign in

Sign in with an email and password, or with a linked Google account where Google sign-in is configured, completing a second factor when the account uses one.
