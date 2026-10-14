---
entities:
- entity: quote
  shows:
  - Quote number
  - Line items
  - Discount
  - Withholding and adjustments
  - Terms
  - Notes
  - Custom field values
  - Total
  - Tax total
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
  target: src/QuoteBundle/Action/View.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Resources/views/Default/view.html.twig
---

# Quote detail

One quote as the client will see it, with the abilities its status allows.
