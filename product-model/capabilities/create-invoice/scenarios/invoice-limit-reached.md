---
kind: validation
routes:
  web: Web
steps:
- text: The User opens a new invoice
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-editor'}
- text: On the hosted service, the company has already created as many invoices this month as its plan allows
  kind: condition
  actor: user
  entities:
  - {entity: company, effect: reads, facts: [Monthly invoice limit, Invoices created this month]}
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-editor'}
- text: The Product offers an upgrade instead of the invoice form
  kind: product
  actor: user
  entities:
  - {entity: company, effect: reads, facts: [Monthly invoice limit]}
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-editor'}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Action/Create.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Validator/Constraints/WithinPlanInvoiceLimitValidator.php
---

# Refuse a new invoice beyond the plan's monthly limit

## Trigger

A hosted company on a plan with a monthly invoice limit starts another invoice.

## Outcome

No invoice is created this month until the plan allows more.
