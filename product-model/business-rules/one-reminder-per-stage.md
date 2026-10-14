---
appliesTo:
- type: capability
  id: send-automatic-payment-reminders
  contexts:
  - {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/MessageHandler/SendInvoiceReminderHandler.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Repository/InvoiceReminderRepository.php
---

# Each automatic reminder is sent at most once per invoice

The pre-due reminder and the 1, 7 and 14 day overdue reminders are each sent once for an invoice, only while it is pending (pre-due) or pending or overdue (overdue stages), and only while the company has automatic reminders on. Manual reminders do not count towards the schedule.
