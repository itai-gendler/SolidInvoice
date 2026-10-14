---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to create a client with its contacts
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: []}
  - {entity: contact, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product creates the active client with its contacts
  kind: product
  actor: user
  entities:
  - {entity: client, effect: creates, to: Active, facts: [Name, Website, Currency, Payment terms, Credit balance]}
  - {entity: contact, effect: creates, facts: [First name, Last name, Email], with: client}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Entity/Client.php
---

# Create a client through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The client exists, as if added in the web application.
