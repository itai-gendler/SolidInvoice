---
references:
- kind: code
  role: implementation
  target: src/UserBundle/Entity/ApiToken.php
- kind: code
  role: implementation
  target: src/UserBundle/Entity/ApiTokenHistory.php
- kind: doc
  role: context
  target: docs/docs/api/rest-api.md
---

# API token

A personal token that authenticates REST API requests as one User in one company.

## Information kept

- **Name** — a label identifying where the token is used
- **Description** — a longer note about its purpose
- **Token** — the secret value, shown once when the token is created
- **Usage count** — how many requests the token has made
- **Last used** — when the token last made a request
- **Request history** — the successful requests made with the token: date, method, endpoint, status, IP address and user agent
