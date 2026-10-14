---
kind: primary
routes:
  web: Web
steps:
- text: The User changes a channel's name or settings and saves
  kind: actor
  actor: user
  entities:
  - {entity: notification-channel, effect: reads, facts: [Name, Service]}
  contexts:
    web: {place: 'web::company-workspace::notification-settings'}
- text: The Product saves the channel
  kind: product
  actor: user
  entities:
  - {entity: notification-channel, effect: changes, facts: [Name, Settings]}
  contexts:
    web: {place: 'web::company-workspace::notification-settings'}
---

# Edit a notification channel

## Trigger

Credentials change.

## Outcome

Notifications use the new settings.
