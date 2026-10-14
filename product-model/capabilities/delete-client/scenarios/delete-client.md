---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete on the client and confirms
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
- text: The Product deletes the client with its contacts, addresses and tax identifiers
  kind: product
  actor: user
  entities:
  - {entity: client, effect: removes, from: Active}
  - {entity: contact, effect: removes, with: client}
  - {entity: address, effect: removes, with: client}
  - {entity: tax-identifier, effect: removes, with: client}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
- text: The Product returns to the client list
  kind: product
  actor: user
  entities:
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-list'}
---

# Delete a client from its page

## Trigger

A client was added by mistake or must be erased.

## Outcome

The client and its contacts are gone, and with them its quotes, invoices, recurring invoices and payments.
