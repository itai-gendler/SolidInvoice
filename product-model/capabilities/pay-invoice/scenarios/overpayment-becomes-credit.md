---
kind: edge
routes:
  web: Web
steps:
- text: The User records an offline payment larger than the invoice balance
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Balance]}
  - {entity: payment-method, effect: reads, facts: [Name]}
  - {entity: payment, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-payment'}
- text: The Product records the payment as captured
  kind: product
  actor: user
  entities:
  - {entity: payment, effect: creates, to: Captured, facts: [Amount, Currency, Reference, Notes, Completed at]}
  contexts:
    web: {place: 'web::company-workspace::invoice-payment'}
- text: The Product marks the invoice paid and adds what was paid beyond the total to the client's credit balance
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: changes, from: Pending, to: Paid, facts: [Balance, Paid date]}
  - {entity: client, effect: changes, facts: [Credit balance]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# Keep an overpayment as client credit

## Trigger

More was received than the invoice asked for.

## Outcome

The invoice is Paid and the surplus waits as client credit.
