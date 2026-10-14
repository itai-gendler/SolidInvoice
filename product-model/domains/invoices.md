---
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Menu/InvoiceMenu.php
---

# Invoices

Invoices from draft to paid: issuing, sending, reminding, paying, cancelling and archiving, including what happens to them on schedule.

## Boundary

Owns one-off invoices and their payments. It does not own the recurring invoices that generate invoices, the tax rates they draw on, or the payment methods a company sets up.
