---
kind: validation
routes:
  web: Web
steps:
- text: The User enters a client name that is already in use, by an archived client or an active one
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-form'}
- text: The User saves the client
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-form'}
- text: The Product refuses the save and asks for a different name
  kind: condition
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::client-form'}
---

# Refuse a client name already used

## Trigger

The User adds a client under a name that is already in use.

## Outcome

No client is created; the form stays open with the name flagged.
