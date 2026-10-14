---
appliesTo:
- type: capability
  id: add-tax-rate
- type: capability
  id: edit-tax-rate
references:
- kind: code
  role: implementation
  target: src/TaxBundle/Entity/Tax.php
---

# Tax rate names are unique within a company

Adding or renaming a tax rate to a name another rate of the company has is refused.
