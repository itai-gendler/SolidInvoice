---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete on a payment method nobody has paid with, and confirms
  kind: actor
  actor: user
  entities:
  - {entity: payment-method, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::payment-methods'}
- text: The Product deletes the payment method
  kind: product
  actor: user
  entities:
  - {entity: payment-method, effect: removes}
  contexts:
    web: {place: 'web::company-workspace::payment-methods'}
---

# Delete an unused payment method

## Trigger

A method was set up by mistake.

## Outcome

The method is gone.
