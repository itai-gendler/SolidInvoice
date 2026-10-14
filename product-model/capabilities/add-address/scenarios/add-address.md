---
kind: primary
routes:
  web: Web
steps:
- text: The User enters the street, city, state, zip and country of a new address
  kind: actor
  actor: user
  entities:
  - {entity: address, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
- text: The Product adds the address to the client
  kind: product
  actor: user
  entities:
  - {entity: address, effect: creates, facts: [Street, City, State, Zip, Country]}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
---

# Add an address to a client

## Trigger

The client has another address.

## Outcome

The address is listed on the client; the first address is the one documents use.
