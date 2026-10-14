---
entities:
- entity: quote
  shows:
  - Line items
  - Discount
  - Withholding and adjustments
  - Terms
  - Notes
  - Custom field values
  collects:
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
  target: src/QuoteBundle/Twig/Components/CreateQuote.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Form/Type/QuoteType.php
---

# Quote editor

Preparing a new quote or changing one: its client and recipients, line items with their taxes, discount, withholding and adjustments, terms and notes.
