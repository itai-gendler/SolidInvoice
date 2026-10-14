---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to add an address to a client
  kind: actor
  actor: user
  entities:
  - {entity: address, effect: reads, facts: []}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product adds the address to the client
  kind: product
  actor: user
  entities:
  - {entity: address, effect: creates, facts: [Street, City, State, Zip, Country]}
  - {entity: client, effect: reads, facts: []}
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

# Add an address through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The address is listed on the client.
