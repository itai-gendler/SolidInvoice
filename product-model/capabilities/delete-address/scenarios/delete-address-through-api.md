---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to delete a client address
  kind: actor
  actor: user
  entities:
  - {entity: address, effect: reads, facts: []}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product removes the address
  kind: product
  actor: user
  entities:
  - {entity: address, effect: removes}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Entity/Address.php
- kind: code
  role: implementation
  target: src/ClientBundle/Twig/Components/AddressCollection.php
---

# Delete an address through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The address is gone.
