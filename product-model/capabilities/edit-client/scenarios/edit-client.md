---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the client name, website, currency, due terms or extra field values
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Name, Website, Currency, Payment terms, Custom field values]}
  contexts:
    web: {place: 'web::company-workspace::client-form'}
- text: The User saves the client
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-form'}
- text: The Product saves the client's details
  kind: product
  actor: user
  entities:
  - {entity: client, effect: changes, facts: [Name, Website, Currency, Payment terms, Custom field values]}
  contexts:
    web: {place: 'web::company-workspace::client-form'}
---

# Edit a client's details

## Trigger

A client's details have changed.

## Outcome

The client shows the new details; issued quotes and invoices keep the currency they were issued in.
