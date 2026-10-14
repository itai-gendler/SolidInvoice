---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete on a channel and confirms
  kind: actor
  actor: user
  entities:
  - {entity: notification-channel, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::notification-settings'}
- text: The Product removes the channel
  kind: product
  actor: user
  entities:
  - {entity: notification-channel, effect: removes}
  contexts:
    web: {place: 'web::company-workspace::notification-settings'}
---

# Delete a notification channel

## Trigger

The User stops using a service.

## Outcome

Nothing is sent through it any more.
