---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes an address
  kind: actor
  actor: user
  entities:
  - {entity: address, effect: reads, facts: [Street, City]}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
- text: The Product removes the address
  kind: product
  actor: user
  entities:
  - {entity: address, effect: removes}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
---

# Delete an address

## Trigger

An address is no longer used.

## Outcome

The address is gone from the client.
