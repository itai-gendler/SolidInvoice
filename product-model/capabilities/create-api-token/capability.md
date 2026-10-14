---
domain: profile
availability:
- {place: 'web::company-workspace'}
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
---

# Create an API token

Create a personal token for the REST API in the current company.
