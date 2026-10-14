---
kind: primary
routes:
  web: Web
steps:
- text: The User picks a service, names the channel, enters its settings and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::notification-settings'}
- text: The Product adds the channel to the User's channels
  kind: product
  actor: user
  entities:
  - {entity: notification-channel, effect: creates, facts: [Name, Service, Settings]}
  contexts:
    web: {place: 'web::company-workspace::notification-settings'}
---

# Add a notification channel

## Trigger

The User wants notifications by SMS or chat.

## Outcome

The channel can be chosen for any event.
