---
entities:
- entity: api-token
  shows:
  - Name
  - Description
  - Token
  - Usage count
  - Last used
  - Request history
  collects:
  - Name
  - Description
references:
- kind: code
  role: implementation
  target: src/UserBundle/Action/ApiIndex.php
- kind: code
  role: implementation
  target: src/UserBundle/Twig/Components/ApiTokens.php
---

# API tokens

The User's API tokens for the current company, their usage and request history.
