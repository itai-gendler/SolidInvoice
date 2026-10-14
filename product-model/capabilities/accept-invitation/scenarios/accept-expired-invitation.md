---
kind: validation
routes:
  web: Web
steps:
- text: The Visitor follows an invitation link after it expired
  kind: actor
  actor: visitor
  entities:
  - {entity: invitation, effect: reads, facts: [Expires at]}
  contexts:
    web: {place: 'web::sign-in'}
- text: The Product marks the invitation expired and refuses it
  kind: product
  actor: visitor
  entities:
  - {entity: invitation, effect: changes, from: Pending, to: Expired, facts: []}
  contexts:
    web: {place: 'web::sign-in'}
---

# Refuse an expired invitation

## Trigger

An invitation was not used in time.

## Outcome

The person does not join; the company can send a new invitation.
