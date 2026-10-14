---
kind: validation
routes:
  web: Web
steps:
- text: The User tries to delete the only contact of a client
  kind: actor
  actor: user
  entities:
  - {entity: contact, effect: reads, facts: [First name, Last name]}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
- text: The Product refuses because a client always keeps at least one contact
  kind: condition
  actor: user
  entities:
  - {entity: client, effect: reads, facts: []}
  - {entity: contact, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
---

# Keep a client's last contact

## Trigger

The User removes the last remaining contact.

## Outcome

The contact stays.
