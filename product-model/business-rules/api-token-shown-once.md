---
appliesTo:
- type: capability
  id: create-api-token
  contexts:
  - {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/UserBundle/Twig/Components/CreateApiToken.php
---

# An API token's value is shown only once

The value is shown when the token is created and never again; a lost token is revoked and replaced.
