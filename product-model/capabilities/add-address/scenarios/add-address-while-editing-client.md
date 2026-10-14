---
kind: alternative
routes:
  web: Web
steps:
- text: The User adds an address row on the client form and saves
  kind: actor
  actor: user
  entities:
  - {entity: address, effect: reads, facts: []}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-form'}
- text: The Product adds the address to the client
  kind: product
  actor: user
  entities:
  - {entity: address, effect: creates, facts: [Street, City, State, Zip, Country]}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-form'}
---

# Add an address while editing a client

## Trigger

The User updates a client and its addresses together.

## Outcome

The address is listed on the client.
