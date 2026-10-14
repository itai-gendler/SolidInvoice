---
kind: edge
routes:
  web: Web
steps:
- text: The User chooses Send on a pending invoice
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: The mail server does not accept the email
  kind: condition
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  - {entity: contact, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: The Product reports that the email could not be sent
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# Report an invoice email that could not be sent

## Trigger

Email delivery is unavailable.

## Outcome

The User is told the email failed; the invoice keeps its status.

## Edge cases

- A draft sent this way is issued as Pending before the email is attempted and stays Pending.
