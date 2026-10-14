---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to record an offline payment of the full balance of a pending invoice, in its currency
  kind: actor
  actor: user
  entities:
  - {entity: payment, effect: reads, facts: []}
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product records the payment as captured and marks the invoice paid
  kind: product
  actor: user
  entities:
  - {entity: payment, effect: creates, to: Captured, facts: [Amount, Currency, Reference, Notes, Completed at]}
  - {entity: invoice, effect: changes, from: Pending, to: Paid, facts: [Paid date]}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/RecordPaymentProcessor.php
---

# Record a payment through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The payment is Captured and the invoice is Paid.

## Edge cases

- A payment in another currency than the invoice's is refused.
