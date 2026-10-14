---
kind: validation
routes:
  web: Web
steps:
- text: The User opens a new recurring invoice
  kind: actor
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-editor'}
- text: On the hosted service, the company's plan does not include recurring invoices
  kind: condition
  actor: user
  entities:
  - {entity: company, effect: reads, facts: [Plan includes recurring invoices]}
  - {entity: recurring-invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-editor'}
- text: The Product offers an upgrade instead of the recurring invoice form
  kind: product
  actor: user
  entities:
  - {entity: company, effect: reads, facts: [Plan includes recurring invoices]}
  - {entity: recurring-invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-editor'}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Action/CreateRecurring.php
---

# Refuse recurring invoices on a plan without them

## Trigger

A hosted company on a plan without recurring invoices starts one.

## Outcome

No recurring invoice is created.
