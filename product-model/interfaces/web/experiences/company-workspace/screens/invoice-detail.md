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
  - Total
  - Tax total
  - Balance
  - Paid date
  - Currency
- entity: client
  shows:
  - Name
- entity: contact
  shows:
  - First name
  - Last name
  - Email
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
  target: src/InvoiceBundle/Action/View.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Resources/views/Default/view.html.twig
---

# Invoice detail

One invoice as the client will see it, with its internal notes and the abilities its status allows.
