---
domain: invoices
availability:
- {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Command/MarkOverdueInvoicesCommand.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Message/Handler/MarkInvoiceOverdueHandler.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Listener/InvoiceOverdueListener.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Repository/InvoiceRepository.php
- kind: doc
  role: intent
  target: docs/docs/invoices/overdue-invoices.md
---

# Mark overdue invoices

Every hour, move pending invoices whose due date has passed to overdue and tell the company.
