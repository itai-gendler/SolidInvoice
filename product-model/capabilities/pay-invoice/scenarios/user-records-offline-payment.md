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
- text: The User picks an offline method such as cash or bank transfer, enters the amount, a reference and notes
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Balance, Currency]}
  - {entity: payment-method, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::invoice-payment'}
- text: The Product records the payment as captured
  kind: product
  actor: user
  entities:
  - {entity: payment, effect: creates, to: Captured, facts: [Amount, Currency, Reference, Notes, Completed at]}
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

# A user records an offline payment

## Trigger

The client paid outside SolidInvoice.

## Outcome

The payment is Captured and the invoice is Paid.

## Edge cases

- A partial amount lowers the balance and leaves the invoice Pending.
- A User may also choose an online method and complete it at the gateway, as a contact does.
