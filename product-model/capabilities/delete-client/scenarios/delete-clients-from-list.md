---
kind: alternative
routes:
  web: Web
steps:
- text: The User selects one or more archived clients and chooses Delete
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::client-list'}
- text: The Product deletes the selected clients with their contacts, addresses and tax identifiers
  kind: product
  actor: user
  entities:
  - {entity: client, effect: removes, from: Archived}
  - {entity: contact, effect: removes, with: client}
  - {entity: address, effect: removes, with: client}
  - {entity: tax-identifier, effect: removes, with: client}
  contexts:
    web: {place: 'web::company-workspace::client-list'}
---

# Delete clients from the client list

## Trigger

The company clears out clients it no longer needs.

## Outcome

The selected clients and everything kept for them are gone.

## Edge cases

- Active clients can be deleted from the Active tab the same way; archiving first is not required.
