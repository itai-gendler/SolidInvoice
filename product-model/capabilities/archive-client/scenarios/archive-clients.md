---
kind: primary
routes:
  web: Web
steps:
- text: The User selects one or more active clients and chooses Archive
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::client-list'}
- text: The Product archives the selected clients
  kind: product
  actor: user
  entities:
  - {entity: client, effect: changes, from: Active, to: Archived, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-list'}
---

# Archive clients from the client list

## Trigger

The company no longer works with a client.

## Outcome

The clients move to the Archived tab and are no longer offered for new quotes and invoices; their documents remain.
