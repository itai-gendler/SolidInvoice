---
kind: edge
routes:
  web: Web
steps:
- text: The Contact picks an online payment method and confirms the amount
  kind: actor
  actor: contact
  entities:
  - {entity: invoice, effect: reads, facts: [Balance]}
  - {entity: payment-method, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::shared-documents::invoice-payment'}
- text: The Product records a new payment for the invoice and hands the Contact to the payment gateway
  kind: product
  actor: contact
  entities:
  - {entity: payment, effect: creates, to: New, facts: [Amount, Currency]}
  - {entity: payment-method, effect: reads, facts: [Name]}
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::shared-documents::invoice-payment'}
- text: The gateway reports that the payment failed
  kind: condition
  actor: contact
  entities:
  - {entity: payment, effect: reads, facts: []}
  contexts:
    web: {place: 'web::shared-documents::invoice-payment'}
- text: The Product records the payment as failed and tells the Contact
  kind: product
  actor: contact
  entities:
  - {entity: payment, effect: changes, from: New, to: Failed, facts: [Completed at]}
  - {entity: invoice, effect: reads, facts: [Balance]}
  contexts:
    web: {place: 'web::shared-documents::shared-invoice'}
---

# An online payment does not go through

## Trigger

The gateway declines or the payment errors.

## Outcome

The payment is Failed and the invoice balance is unchanged.

## Edge cases

- Cancelled, expired, pending and other gateway outcomes are recorded on the payment the same way and leave the balance unchanged.
