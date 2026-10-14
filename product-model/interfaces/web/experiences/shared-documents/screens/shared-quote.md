---
entities:
- entity: quote
  shows:
  - Quote number
  - Line items
  - Discount
  - Withholding and adjustments
  - Terms
  - Custom field values
  - Total
  - Tax total
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
---

# Shared quote

A quote as its client sees it from the emailed link, with its PDF.
