---
appliesTo:
- type: capability
  id: generate-recurring-invoices
  contexts:
  - {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Entity/RecurringInvoice.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Message/Handler/CreateInvoiceFromRecurringHandler.php
---

# A recurring invoice generates at most one invoice a day

An active recurring invoice that already has an invoice dated today generates no other that day, however often the schedule runs.
