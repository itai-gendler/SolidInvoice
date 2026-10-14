---
kind: primary
routes:
  web: Web
steps:
- text: The User picks, for each event the Product can notify about, the channels to be notified through, and saves
  kind: actor
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Notification preferences]}
  - {entity: notification-channel, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::notification-settings'}
- text: The Product saves the User's choices
  kind: product
  actor: user
  entities:
  - {entity: user, effect: changes, facts: [Notification preferences]}
  contexts:
    web: {place: 'web::company-workspace::notification-settings'}
---

# Change notification settings

## Trigger

The User wants to hear about some events and not others.

## Outcome

Notifications follow the new choices; email is always one of the channels on offer.
