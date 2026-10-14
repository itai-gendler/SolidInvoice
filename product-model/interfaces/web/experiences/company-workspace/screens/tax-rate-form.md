---
entities:
- entity: tax-rate
  shows:
  - Name
  - Rate
  - Type
  - Category
  - Compound
  collects:
  - Name
  - Rate
  - Type
  - Category
  - Compound
references:
- kind: code
  role: implementation
  target: src/TaxBundle/Action/Add.php
- kind: code
  role: implementation
  target: src/TaxBundle/Action/Edit.php
- kind: code
  role: implementation
  target: src/TaxBundle/Form/Type/TaxType.php
---

# Tax rate form

Adding a tax rate or changing one.
