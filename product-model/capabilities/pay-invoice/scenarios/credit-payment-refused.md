---
kind: validation
routes:
  web: Web
steps:
- text: The User picks Credit and enters more than the client's credit balance or the invoice balance
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Balance]}
  - {entity: client, effect: reads, facts: [Credit balance]}
  - {entity: payment-method, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::invoice-payment'}
- text: The Product refuses, saying there is not enough credit or the amount exceeds the invoice balance
  kind: condition
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Credit balance]}
  - {entity: invoice, effect: reads, facts: [Balance]}
  contexts:
    web: {place: 'web::company-workspace::invoice-payment'}
---

# Refuse a credit payment beyond the credit or the balance

## Trigger

The credit amount is too high.

## Outcome

No payment is recorded; the form stays open.
