---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the name, settings, enabled or internal switch and saves
  kind: actor
  actor: user
  entities:
  - {entity: payment-method, effect: reads, facts: [Name, Enabled, Internal]}
  contexts:
    web: {place: 'web::company-workspace::payment-methods'}
- text: The Product saves the payment method
  kind: product
  actor: user
  entities:
  - {entity: payment-method, effect: changes, facts: [Name, Enabled, Internal, Gateway settings]}
  contexts:
    web: {place: 'web::company-workspace::payment-methods'}
---

# Edit a payment method

## Trigger

Gateway credentials or availability change.

## Outcome

Payments use the new settings; a disabled method is no longer offered.
