---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to delete one of the User's API tokens
  kind: actor
  actor: user
  entities:
  - {entity: api-token, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product deletes the token
  kind: product
  actor: user
  entities:
  - {entity: api-token, effect: removes}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/UserBundle/Entity/ApiToken.php
---

# Revoke an API token through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The token stops working.
