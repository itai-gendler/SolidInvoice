---
kind: primary
routes:
  web: Web
steps:
- text: The User picks a gateway, enters its name and settings, and whether it is enabled and internal, and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::payment-methods'}
- text: The Product creates the payment method
  kind: product
  actor: user
  entities:
  - {entity: payment-method, effect: creates, facts: [Name, Gateway, Enabled, Internal, Gateway settings]}
  contexts:
    web: {place: 'web::company-workspace::payment-methods'}
---

# Add a payment method

## Trigger

The company wants to accept payment a new way.

## Outcome

The method is offered when paying while it is enabled: to Users always, to contacts only when it is not internal.
