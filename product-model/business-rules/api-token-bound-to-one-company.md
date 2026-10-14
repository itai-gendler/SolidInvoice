---
appliesTo:
- type: capability
  id: create-api-token
- type: context
  context: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: doc
  role: intent
  target: docs/docs/api/rest-api.md
---

# An API token acts as one User in one company

A token is created in the company that is active at the time, and its requests see and change only that company's data.
