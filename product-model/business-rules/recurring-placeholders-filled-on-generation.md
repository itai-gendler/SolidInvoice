---
appliesTo:
- type: capability
  id: generate-recurring-invoices
- type: capability
  id: create-recurring-invoice
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Manager/InvoiceManager.php
- kind: doc
  role: intent
  target: docs/docs/recurring-invoices/creating-a-recurring-invoice.md
---

# Date placeholders in recurring line items are filled in on the day an invoice is generated

{day}, {day_name}, {month} and {year} in a recurring invoice's line item names and descriptions become the generation day's values on the generated invoice.
