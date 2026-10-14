---
kind: primary
routes:
  web: Web
steps:
- text: The User adds a tax identifier row with its type and number on the client form, marks it primary if it is the main one, and saves
  kind: actor
  actor: user
  entities:
  - {entity: tax-identifier, effect: reads, facts: []}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-form'}
- text: The Product adds the tax identifier to the client
  kind: product
  actor: user
  entities:
  - {entity: tax-identifier, effect: creates, facts: [Type, Number, Primary]}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-form'}
---

# Add a tax identifier to a client

## Trigger

A client is registered for VAT or another tax.

## Outcome

The number appears on documents sent to the client.
