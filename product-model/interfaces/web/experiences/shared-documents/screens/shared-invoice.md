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
  - Custom field values
  - Total
  - Tax total
  - Balance
  - Currency
- entity: client
  shows:
  - Name
- entity: company
  shows:
  - Name
  - Logo
  - Address
  - Email address
  - Phone number
- entity: address
  shows:
  - Street
  - City
  - State
  - Zip
  - Country
- entity: tax-identifier
  shows:
  - Type
  - Number
  - Primary
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Action/ViewBilling.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Resources/views/external_invoice_view.html.twig
---

# Shared invoice

An invoice as its client sees it from the emailed link, with its PDF and, while it can be paid, the way to pay it.
