---
kind: primary
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
- text: The Contact picks an online payment method and keeps the full balance as the amount
  kind: actor
  actor: contact
  entities:
  - {entity: invoice, effect: reads, facts: [Balance, Currency]}
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
- text: The Product marks the invoice paid because captured payments now cover its total
  kind: product
  actor: contact
  entities:
  - {entity: invoice, effect: changes, from: Pending, to: Paid, facts: [Balance, Paid date]}
  - {entity: payment, effect: reads, facts: []}
  contexts:
    web: {place: 'web::shared-documents::shared-invoice'}
---

# A contact pays an invoice in full online

## Trigger

A contact wants to settle an invoice from the email.

## Outcome

The payment is Captured, the invoice is Paid with today's paid date, and the contact is back on the invoice with a confirmation.

## Edge cases

- An overdue invoice is paid the same way.
- Internal payment methods are never offered from the link.
