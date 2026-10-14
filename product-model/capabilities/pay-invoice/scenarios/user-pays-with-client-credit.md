---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses Pay Now on a pending invoice
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Balance]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: The User picks Credit and enters an amount within the client's credit and the invoice balance
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Balance]}
  - {entity: client, effect: reads, facts: [Credit balance]}
  - {entity: payment-method, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::invoice-payment'}
- text: The Product records the payment as captured and takes the amount off the client's credit balance
  kind: product
  actor: user
  entities:
  - {entity: payment, effect: creates, to: Captured, facts: [Amount, Currency, Reference, Notes, Completed at]}
  - {entity: client, effect: changes, facts: [Credit balance]}
  - {entity: payment-method, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::invoice-payment'}
- text: The Product marks the invoice paid because captured payments now cover its total
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: changes, from: Pending, to: Paid, facts: [Balance, Paid date]}
  - {entity: payment, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# A user pays an invoice with the client's credit

## Trigger

The client has credit on account.

## Outcome

The payment is Captured, the client's credit is lower by the amount, and the invoice is Paid.

## Edge cases

- Credit can pay part of an invoice, the rest paid by another method.
