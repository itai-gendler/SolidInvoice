---
kind: validation
routes:
  web: Web
steps:
- text: The User opens the invitation form
  kind: actor
  actor: user
  entities:
  - {entity: invitation, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::users'}
- text: On the hosted service, the company's users and pending invitations already fill its plan's seats
  kind: condition
  actor: user
  entities:
  - {entity: user, effect: reads, facts: []}
  - {entity: invitation, effect: reads, facts: []}
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::users'}
- text: The Product offers an upgrade instead of the form
  kind: product
  actor: user
  entities:
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::users'}
---

# Refuse an invitation beyond the plan's seats

## Trigger

A hosted company has no free seat.

## Outcome

No invitation is sent.
