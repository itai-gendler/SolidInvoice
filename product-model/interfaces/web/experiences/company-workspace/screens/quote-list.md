---
entities:
- entity: quote
  shows:
  - Quote number
  - Total
  - Tax total
  - Discount
- entity: client
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Action/Index.php
- kind: code
  role: implementation
  target: src/QuoteBundle/DataGrid/QuoteGrid.php
- kind: code
  role: implementation
  target: src/QuoteBundle/DataGrid/ArchivedQuoteGrid.php
---

# Quote list

The company's quotes, active and archived, where quotes are archived, brought back or deleted in bulk.
