---
kind: primary
routes:
  web: Web
steps:
- text: The User enters the email of the person to invite
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::users'}
- text: The Product records the invitation and emails the link
  kind: product
  actor: user
  entities:
  - {entity: invitation, effect: creates, to: Pending, facts: [Email, Expires at]}
  contexts:
    web: {place: 'web::company-workspace::users'}
---

# Invite someone to the company

## Trigger

Someone else should work in the company.

## Outcome

The invitation is Pending and the person has the link.
