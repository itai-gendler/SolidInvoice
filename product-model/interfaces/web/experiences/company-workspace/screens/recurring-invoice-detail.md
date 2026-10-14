---
entities:
- entity: recurring-invoice
  shows:
  - Recurring type
  - Repeat days
  - Start date
  - End date
  - Payment terms
  - Line items
  - Total
  - Tax total
- entity: invoice
  shows:
  - Invoice number
  - Total
- entity: client
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Action/ViewRecurring.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Resources/views/Default/view_recurring.html.twig
---

# Recurring invoice detail

One recurring invoice: its template, its schedule and upcoming dates, and the invoices it has generated, with the abilities its status allows.
