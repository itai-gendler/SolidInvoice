---
kind: primary
routes:
  web: Web
steps:
- text: The User removes a tax identifier row on the client form and saves
  kind: actor
  actor: user
  entities:
  - {entity: tax-identifier, effect: reads, facts: [Type, Number]}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-form'}
- text: The Product removes the tax identifier
  kind: product
  actor: user
  entities:
  - {entity: tax-identifier, effect: removes}
  contexts:
    web: {place: 'web::company-workspace::client-form'}
---

# Remove a tax identifier from a client

## Trigger

A client is no longer registered.

## Outcome

The number no longer appears on the client's documents.
