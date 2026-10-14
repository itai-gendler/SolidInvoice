---
kind: validation
routes:
  web: Web
steps:
- text: The User chooses Delete on a payment method that has been used to pay, and confirms
  kind: actor
  actor: user
  entities:
  - {entity: payment-method, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::payment-methods'}
- text: The Product refuses because payments are associated with the method
  kind: condition
  actor: user
  entities:
  - {entity: payment, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::payment-methods'}
---

# Keep a payment method that has payments

## Trigger

The User removes a method with history.

## Outcome

The method stays; it can be disabled instead.
