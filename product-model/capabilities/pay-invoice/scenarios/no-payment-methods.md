---
kind: edge
routes:
  web: Web
steps:
- text: The Contact chooses Pay Now on a pending invoice
  kind: actor
  actor: contact
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  contexts:
    web: {place: 'web::shared-documents::shared-invoice'}
- text: The company has no enabled payment method the Contact may use
  kind: condition
  actor: contact
  entities:
  - {entity: payment-method, effect: reads, facts: []}
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::shared-documents::invoice-payment'}
- text: The Product returns the Contact to the invoice saying no payment methods are available
  kind: product
  actor: contact
  entities:
  - {entity: invoice, effect: reads, facts: []}
  - {entity: payment-method, effect: reads, facts: []}
  contexts:
    web: {place: 'web::shared-documents::shared-invoice'}
---

# Refuse payment when no method is available

## Trigger

The company has not set up a method its contacts can use.

## Outcome

No payment is recorded.
