---
appliesTo:
- type: capability
  id: mark-overdue-invoices
  contexts:
  - {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Repository/InvoiceRepository.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Message/Handler/MarkInvoiceOverdueHandler.php
---

# The hourly check marks overdue only pending invoices whose due date has passed

An invoice without a due date is never marked overdue by the check.
