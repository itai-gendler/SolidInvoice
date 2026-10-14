---
kind: alternative
routes:
  web: Web
steps:
- text: The Contact chooses Pay Now on a pending invoice
  kind: actor
  actor: contact
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Balance]}
  contexts:
    web: {place: 'web::shared-documents::shared-invoice'}
- text: The Contact picks an online payment method and enters less than the balance
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
- text: The Contact completes the payment at the gateway
  kind: actor
  actor: contact
  entities:
  - {entity: payment, effect: reads, facts: []}
  contexts:
    web: {place: 'web::shared-documents::invoice-payment'}
- text: The Product records the gateway's confirmation as captured
  kind: product
  actor: contact
  entities:
  - {entity: payment, effect: changes, from: New, to: Captured, facts: [Completed at]}
  contexts:
    web: {place: 'web::shared-documents::invoice-payment'}
- text: The Product lowers the invoice balance by what has been captured
  kind: product
  actor: contact
  entities:
  - {entity: invoice, effect: changes, facts: [Balance]}
  contexts:
    web: {place: 'web::shared-documents::shared-invoice'}
---

# A contact pays part of an invoice online

## Trigger

A contact pays in instalments.

## Outcome

The payment is Captured and the invoice stays Pending with a lower balance.
