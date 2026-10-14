---
kind: validation
routes:
  web: Web
steps:
- text: The User chooses Send on an invoice that has no contacts chosen
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  - {entity: contact, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: The Product refuses because there is nobody to send it to
  kind: condition
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  - {entity: contact, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# Refuse to send an invoice with no recipients

## Trigger

The invoice has no recipients.

## Outcome

Nothing is emailed and the invoice is unchanged.
