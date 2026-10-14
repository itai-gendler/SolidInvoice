---
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Menu/RecurringInvoiceMenu.php
---

# Recurring invoices

Invoice templates that generate invoices for a client on a schedule.

## Boundary

Owns recurring invoices and their schedule. It does not own the invoices they generate once those exist, which belong to Invoices.
