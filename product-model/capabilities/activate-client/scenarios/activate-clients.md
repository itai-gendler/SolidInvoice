---
kind: primary
routes:
  web: Web
steps:
- text: The User selects one or more archived clients and chooses Activate
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::client-list'}
- text: The Product makes the selected clients active again
  kind: product
  actor: user
  entities:
  - {entity: client, effect: changes, from: Archived, to: Active, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-list'}
---

# Activate archived clients

## Trigger

The company starts working with an archived client again.

## Outcome

The clients are back on the Active tab and can be billed again.
