---
entities:
- entity: recurring-invoice
  shows: &id001
  - Start date
  - Recurring type
  - Repeat days
  - End recurrence
  - End date
  - End after occurrences
  - Payment terms
  - Line items
  - Discount
  - Withholding and adjustments
  - Terms
  - Notes
  collects: *id001
- entity: client
  shows:
  - Name
- entity: contact
  shows:
  - First name
  - Last name
  - Email
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Twig/Components/CreateRecurringInvoice.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Form/Type/RecurringInvoiceType.php
---

# Recurring invoice editor

Preparing a new recurring invoice or changing one: its client and recipients, line items, discount, terms and notes, payment terms and its schedule.
