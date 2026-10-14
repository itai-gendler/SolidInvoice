---
entities:
- entity: invoice
  shows:
  - Invoice number
  - Invoice date
  - Payment terms
  - Due date
  - Line items
  - Discount
  - Withholding and adjustments
  - Terms
  - Notes
  - Custom field values
  collects:
  - Invoice number
  - Invoice date
  - Payment terms
  - Due date
  - Line items
  - Discount
  - Withholding and adjustments
  - Terms
  - Notes
  - Custom field values
- entity: client
  shows:
  - Name
  collects:
  - Name
- entity: contact
  shows: &id001
  - First name
  - Last name
  - Email
  collects: *id001
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Twig/Components/CreateInvoice.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Form/Type/InvoiceType.php
---

# Invoice editor

Preparing a new invoice or changing one: its client and recipients, dates and payment terms, line items with their taxes, discount, withholding and adjustments, terms and notes.
