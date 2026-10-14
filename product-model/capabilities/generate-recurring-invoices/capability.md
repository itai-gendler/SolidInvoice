---
domain: recurring-invoices
availability:
- {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Command/SendRecurringInvoicesCommand.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Message/Handler/CreateInvoiceFromRecurringHandler.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Manager/InvoiceManager.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Recurring/RecurringSchedule.php
- kind: doc
  role: intent
  target: docs/docs/recurring-invoices/understanding-the-schedule.md
---

# Generate recurring invoices

Every hour, issue an invoice from each active recurring invoice whose schedule matches today, and complete schedules that have reached their end.
