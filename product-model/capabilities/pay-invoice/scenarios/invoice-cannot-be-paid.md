---
kind: validation
routes:
  web: Web
steps:
- text: The Contact opens the payment page of an invoice that is a draft, paid, cancelled or archived
  kind: actor
  actor: contact
  entities:
  - {entity: payment, effect: reads, facts: []}
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::shared-documents::invoice-payment'}
- text: The Product refuses because the invoice cannot be paid and returns the Contact to the invoice
  kind: condition
  actor: contact
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::shared-documents::shared-invoice'}
---

# Refuse to pay an invoice that is not due for payment

## Trigger

Someone tries to pay an invoice that is not pending or overdue.

## Outcome

No payment is recorded.
