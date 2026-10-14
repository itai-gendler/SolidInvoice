---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to read a client with its contacts, quotes, invoices or payments
  kind: actor
  actor: user
  entities:
  - {entity: payment, effect: reads, facts: []}
  - {entity: invoice, effect: reads, facts: []}
  - {entity: quote, effect: reads, facts: []}
  - {entity: client, effect: reads, facts: []}
  - {entity: contact, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product returns the client and what was asked of it
  kind: product
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Name, Website, Currency]}
  - {entity: contact, effect: reads, facts: [Email]}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Entity/Client.php
---

# Read a client through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The integration has the client.
