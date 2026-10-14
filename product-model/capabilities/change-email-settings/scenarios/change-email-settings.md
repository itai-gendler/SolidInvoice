---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the sender name, sender email or delivery method in the email section and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::settings'}
- text: The Product saves the email settings
  kind: product
  actor: user
  entities:
  - {entity: company, effect: changes, facts: [Sender name, Sender address, Mail delivery]}
  contexts:
    web: {place: 'web::company-workspace::settings'}
---

# Change email settings

## Trigger

The company wants mail to come from its own address.

## Outcome

Emails to clients use the new sender and delivery.
