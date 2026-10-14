---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Resend on a pending invitation
  kind: actor
  actor: user
  entities:
  - {entity: invitation, effect: reads, facts: [Email, Expires at]}
  contexts:
    web: {place: 'web::company-workspace::users'}
- text: The Product renews the invitation and emails the link again
  kind: product
  actor: user
  entities:
  - {entity: invitation, effect: changes, facts: [Expires at]}
  contexts:
    web: {place: 'web::company-workspace::users'}
---

# Resend an invitation

## Trigger

The invited person missed the email.

## Outcome

The person has a new link with a new expiry.
