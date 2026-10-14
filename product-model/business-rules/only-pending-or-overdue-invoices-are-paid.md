---
appliesTo:
- type: capability
  id: pay-invoice
  contexts:
  - {place: 'web::company-workspace'}
  - {place: 'web::shared-documents'}
references:
- kind: code
  role: implementation
  target: config/packages/workflow.php
- kind: code
  role: implementation
  target: src/PaymentBundle/Action/Prepare.php
---

# Only pending or overdue invoices take payments

Drafts, paid, cancelled and archived invoices refuse payment wherever it is attempted.
