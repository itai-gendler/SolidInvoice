---
domain: profile
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/UserBundle/Twig/Components/CreateApiToken.php
- kind: code
  role: implementation
  target: src/UserBundle/Twig/Components/ApiTokens.php
- kind: doc
  role: intent
  target: docs/docs/api/rest-api.md
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: code
  role: implementation
  target: src/UserBundle/Entity/ApiToken.php
---

# Revoke an API token

Delete an API token so it stops working.
