---
entities:
- entity: tax-rate
  shows:
  - Name
  - Rate
  - Type
  - Category
  - Compound
references:
- kind: code
  role: implementation
  target: src/TaxBundle/Action/Index.php
- kind: code
  role: implementation
  target: src/TaxBundle/DataGrid/TaxGrid.php
---

# Tax rates

The company's tax rates, where rates are deleted.
