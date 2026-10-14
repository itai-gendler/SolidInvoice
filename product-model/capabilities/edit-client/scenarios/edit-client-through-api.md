---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to change a client's details
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product saves the client's details
  kind: product
  actor: user
  entities:
  - {entity: client, effect: changes, facts: [Name, Website, Currency, Payment terms]}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Entity/Client.php
---

# Edit a client through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The client shows the new details.
