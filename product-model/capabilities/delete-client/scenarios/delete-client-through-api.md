---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to delete a client
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product deletes the client with its contacts, addresses and tax identifiers
  kind: product
  actor: user
  entities:
  - {entity: client, effect: removes, from: Active}
  - {entity: contact, effect: removes, with: client}
  - {entity: address, effect: removes, with: client}
  - {entity: tax-identifier, effect: removes, with: client}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Entity/Client.php
---

# Delete a client through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The client and everything kept for it are gone.
