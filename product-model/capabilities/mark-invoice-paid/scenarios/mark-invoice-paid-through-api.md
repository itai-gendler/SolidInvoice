---
kind: primary
routes:
  web: Web
steps:
- text: The User's integration sends a request to apply the pay transition to a pending invoice
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product marks the invoice paid with today as its paid date
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: changes, from: Pending, to: Paid, facts: [Paid date]}
  contexts:
    web: {place: rest-api}
---

# Mark an invoice paid through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The invoice is Paid.
