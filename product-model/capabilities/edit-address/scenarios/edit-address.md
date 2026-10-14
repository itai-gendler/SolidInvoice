---
kind: primary
routes:
  web: Web
steps:
- text: The User changes an address and saves
  kind: actor
  actor: user
  entities:
  - {entity: address, effect: reads, facts: [Street, City, State, Zip, Country]}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
- text: The Product saves the address
  kind: product
  actor: user
  entities:
  - {entity: address, effect: changes, facts: [Street, City, State, Zip, Country]}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
---

# Edit an address

## Trigger

A client moved.

## Outcome

Documents prepared from now on show the new address.
