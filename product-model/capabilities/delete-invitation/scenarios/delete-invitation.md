---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete on an invitation
  kind: actor
  actor: user
  entities:
  - {entity: invitation, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'web::company-workspace::users'}
- text: The Product removes the invitation
  kind: product
  actor: user
  entities:
  - {entity: invitation, effect: removes, from: Pending}
  contexts:
    web: {place: 'web::company-workspace::users'}
---

# Delete an invitation

## Trigger

The invitation was a mistake.

## Outcome

The link no longer works.
